# Utils Folder

Keep generic code that is useful through out the project here e.g. read_yaml etc.

Example below

```
from typing import List, Dict, Any
import yaml
from pathlib import Path
import os
from supabase import create_client, Client
import dotenv
from box.exceptions import BoxValueError
from box import ConfigBox

from QuickPunch.logging import logger

def read_yaml(path_to_yaml: Path) -> ConfigBox:
  """
  Read a yaml file and return a ConfigBox object.
  """
  try:
    with open(path_to_yaml, "r") as yaml_file:
      yaml_dict = yaml.safe_load(yaml_file)
      logger.info(f"yaml file: {yaml_file.name} read successfully.")
      return ConfigBox(yaml_dict)
  except BoxValueError:
    raise ValueError(f"Error reading yaml file at {path_to_yaml}.")
    logger.error(f"Error reading yaml file at {path_to_yaml}.")
  except Exception as e:
    raise e
    logger.error(f"Error reading yaml file at {path_to_yaml}.")


class bin_colors:
  HEADER = '\033[95m'
  INFO = '\033[94m'
  OKCYAN = '\033[96m'
  SUCCESS = '\033[92m'
  WARNING = '\033[93m'
  ERROR = '\033[91m'
  ENDC = '\033[0m'
  BOLD = '\033[1m'
  UNDERLINE = '\033[4m'

def create_directory(path: Path) -> None:
  """
  Create a directory if it does not exist.
  """
  try:
    if not os.path.exists(path):
      os.makedirs(path)
      logger.info(f"{bin_colors.INFO}Directory created at {path}.{bin_colors.ENDC}")
  except Exception as e:
    logger.error(f"{bin_colors.ERROR}Error creating directory at {path}.{bin_colors.ENDC}")
    raise e
  

def connect_to_supabase():
  """
  Get the database connection.
  """
  dotenv.load_dotenv()
  SUPABASE_URL = os.getenv("SUPABASE_URL")
  SUPABASE_KEY = os.getenv("SUPABASE_KEY")
  logger.info(f"{bin_colors.INFO}Connecting to database at {SUPABASE_URL}.{bin_colors.ENDC}")
  supabase = create_client(SUPABASE_URL, SUPABASE_KEY)
  if supabase is None:
    logger.error(f"{bin_colors.ERROR}Error connecting to database at {SUPABASE_URL}.{bin_colors.ENDC}")
    raise Exception("Error connecting to database.")
  logger.info(f"{bin_colors.SUCCESS}Connected to database at {SUPABASE_URL}.{bin_colors.ENDC}")
  return supabase


```