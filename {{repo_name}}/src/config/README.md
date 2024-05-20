# Config Folder

Code to read the config from the yaml file and prepare them for the component.

Example below

```
from {project}.entity import SampleConfig
from {project}.utils import read_yaml

class ConfigurationManager:
  def __init__(self, config_filepath):
    self.config = read_yaml(config_filepath)

  def get_sample_config(self) -> SampleConfig:
    return SampleConfig(**self.config.sample)
```