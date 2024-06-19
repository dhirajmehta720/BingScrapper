# Bing Scraper

A web scraper written in Go to extract search results from Bing.com across various international domains.

## Table of Contents
- [Technologies Used](#technologies-used)
- [Key Features](#key-features)
- [Challenges Addressed](#challenges-addressed)
- [Additional Features](#additional-features)
- [Usage](#usage)
- [Example](#example)
- [Result](#result)
- [License](#license)

## Technologies Used
- **Programming Language**: Go (Golang)
- **Libraries**:
  - `net/http` for HTTP requests and handling
  - `strings` for string manipulation
  - `time` for timing and delays
  - `math/rand` for randomizing user agents
  - `net/url` for URL parsing
  - `github.com/PuerkitoBio/goquery` for HTML parsing

## Key Features
- **Multi-domain Support**: Configured to support Bing search across multiple country-specific domains.
- **Random User-Agent Selection**: Implemented to mimic different browsers and reduce the chance of being blocked.
- **Pagination Handling**: Able to fetch multiple pages of search results by calculating the appropriate `first` parameter for Bing's pagination.
- **Proxy Support**: Designed to handle requests through a proxy if required, enhancing the ability to scrape anonymously.
- **Error Handling**: Checks for non-200 status codes to identify possible bans and other errors.
- **Result Parsing**: Extracts and structures search result details such as rank, URL, title, and description using `goquery`.

## Challenges Addressed
- **IP Blocking Mitigation**: Implemented randomized user agents and optional proxy support to avoid IP bans.
- **Search Result Accuracy**: Ensured accurate extraction of search result details by effectively parsing HTML with `goquery`.

## Additional Features
- **Backoff Strategy**: Introduced a delay mechanism between requests to avoid being flagged by Bing as a bot.
- **Country Code Configuration**: Maintained a map of supported Bing domains with their respective country codes for easy configuration.

## Usage
1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/bing-scraper.git
    ```
2. Navigate to the project directory:
    ```sh
    cd bing-scraper
    ```
3. Build the project:
    ```sh
    go build
    ```
4. Run the scraper:
    ```sh
    ./bing-scraper
    ```

## Example
Here's an example of how to use the Bing Scraper in your Go code:

```go
package main

import (
    "fmt"
    "time"
)

func main() {
    res, err := BingScrape("akhil sharma", "com", nil, 1, 15, 30)
    if err == nil {
        for _, res := range res {
            fmt.Println(res)
        }
    } else {
        fmt.Println(err)
    }
}
