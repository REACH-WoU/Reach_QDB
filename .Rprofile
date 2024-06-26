# This file configures the virtualenv and Python paths differently depending on
# the environment the app is running in (local vs remote server).

# Edit this name if desired when starting a new app
VIRTUALENV_NAME_local = 'example_env_name2'
VIRTUALENV_NAME_shiny= 'shiny_virtual_environment'

# ------------------------- Settings (Edit local settings to match your system) -------------------------- #

if (Sys.info()[['user']] == 'shiny'){
  
  # Running on shinyapps.io
  Sys.setenv(PYTHON_PATH = '/usr/bin/python3')
  Sys.setenv(VIRTUALENV_NAME = VIRTUALENV_NAME_shiny) # Installs into default shiny virtualenvs dir
  Sys.setenv(RETICULATE_PYTHON = paste0('/home/shiny/.virtualenvs/', VIRTUALENV_NAME_shiny, '/bin/python'))
  
} else if (Sys.info()[['user']] == 'rstudio-connect'){
  
  # Running on remote server
  Sys.setenv(PYTHON_PATH = '/opt/python/3.7.7/bin/python3')
  Sys.setenv(VIRTUALENV_NAME = paste0(VIRTUALENV_NAME_local, '/')) # include '/' => installs into rstudio-connect/apps/
  Sys.setenv(RETICULATE_PYTHON = paste0(VIRTUALENV_NAME_local, '/bin/python'))
  
} else {
  # Running locally
  options(shiny.port = 7450)
  Sys.setenv(PYTHON_PATH = reticulate::virtualenv_starter('3.9.9'))
  Sys.setenv(VIRTUALENV_NAME = VIRTUALENV_NAME_local) # exclude '/' => installs into ~/.virtualenvs/
  # RETICULATE_PYTHON is not required locally, RStudio infers it based on the ~/.virtualenvs path
}
