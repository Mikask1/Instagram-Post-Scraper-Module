# Instagram-Scraper
Uses selenium to scrape profiles that are accessible to the account

## Setup
  ### Install Dependencies
  ```sh
  pip install pickle
  pip install requests
  pip install json
  pip install selenium
  ```

  ### Download a chromedriver
  - Go to https://chromedriver.chromium.org/downloads
  - Download the chromedriver that is compatible with your Chrome browser

## Documentation
  ### Introduction
  - Call the `login` function if you don't have the `cookies.pkl` file
  - Call the `setup` function to setup your chrome driver

  ### Quick Example
  ```py
  import instagram

  CHROMEDRIVER = "chromedriver.exe"
  instagram.login(username="username", password="pass", chromedriver=CHROMEDRIVER)
  driver = instagram.setup(CHROMEDRIVER)

  profile = instagram.Profile(query="tom holland", driver=driver)
  
  post = profile.get_post(35)
  print(post.media)
  
  post = profile.get_random_post()
  print(post.media)
  
  profile.download(start=23, end=30)
  ```

  ### Profile Class
  - Takes a query and a driver parameter
  - Searches up the account you're looking for

    #### Attributes
    ```
    username    : str
    link        : url
    driver      : Selenium Driver
    ```
    #### Methods
    ```
    get_random_post : Get a random post from the profile
    get_post : Get an indexed post from the profile
    download : Downloads posts in a range
    ```

  ### Post Class
    #### Attributes
    ```
    media       : url
    caption     : str
    upload_date : str
    is_video    : bool
    ```

  ### Login Function
  Logs into account saves the cookies to `cookies.pkl`

  ### Setup Function
  Sets up the chrome webdriver

