# Pipeline Folder

Keep code to execute a combination of components' payloads

Example below

```
from {project}.logging import logger
from {project}.utils import bin_colors
from {project}.components.sample_component import SampleComponent
from {project}.config.configuration import ConfigurationManager

from pathlib import Path

config_manager = ConfigurationManager(Path("config/config.yaml"))

try:
  logger.info(f"{bin_colors.INFO}Starting sample pipeline.{bin_colors.ENDC}")
  sample_component = SampleComponent()
  sample_component.perform_payload()

except Exception as e:
  logger.error(f"{bin_colors.ERROR}Error starting sample pipeline.{bin_colors.ENDC}")
  raise e

.
.
.

try:

except Exception as e:

  raise e

```
