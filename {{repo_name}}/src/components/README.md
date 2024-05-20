# Components Folder

Contains code that defines the payload for any major app component

Example below

```
from {project}.utils import sample_db_connection
from {project}.logging import logger, bin_colors
from {project}.entity import SampleConfig
from {project}.config.configuration import ConfigurationManager

class SampleComponent:
  def __init__(self, config: SampleConfig):
    self.config = config
    self.db = sample_db_connection()

  def payload(self, inputs: str) -> output_type:
    logger.info(f"{bin_colors.INFO}Performing payload{bin_colors.ENDC}")
    return output
```