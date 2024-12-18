

# Quotes Scraper API  

This project is a Go web application that scrapes quotes from the website [Quotes to Scrape](https://quotes.toscrape.com) and serves them as a JSON API.  

## Features  
- Scrapes up to **100 quotes** from the website.  
- Each quote includes its **text**, **author**, and **tags**.  
- Returns the data in **JSON** format via an HTTP endpoint.  

## Prerequisites  
Before getting started, ensure you have the following:  
- **Go** (version 1.16 or higher). You can verify if Go is installed by running the following command:  
  ```bash  
  go version  

Installing Go

Step 1: Download and Install Go

	1.	Visit the Go download page.
	2.	Download the appropriate version for your operating system.
	3.	Follow the installation instructions:
	•	Windows: Run the .msi installer and follow the steps.
	•	macOS: Use the .pkg file or install via Homebrew with brew install go.
	•	Linux: Extract the tarball and add the Go binary to your PATH.

Step 2: Verify Go Installation

After installation, verify that Go is properly installed by running:

go version  

You should see the installed version of Go.

How to Run the Application

Step 1: Clone the Repository

Clone this project to your local machine:

git clone <repository-url>  
cd <repository-folder>  

Step 2: Install Dependencies

The application uses the goquery library for web scraping. Install it with:

go get -u github.com/PuerkitoBio/goquery  

Step 3: Run the Application

Execute the application with the following command:

go run main.go  

Step 4: Access the API

Open a browser or use tools like curl or Postman to access the API:

http://localhost:8080/quotes  

How the Code Works

Overview

	1.	The application starts a web server that listens on port 8080.
	2.	When the /quotes endpoint is accessed:
	•	The scrapeQuotes function scrapes up to 100 quotes from the website, starting from the first page.
	•	Each quote includes its text, author, and tags, which are extracted from the HTML using the goquery library.
	3.	The scraped quotes are returned in JSON format as a response.

Key Components

Quote Structure

The Quote struct defines the data for each quote:

type Quote struct {  
    Text   string   `json:"text"`  
    Author string   `json:"author"`  
    Tags   []string `json:"tags"`  
}  

scrapeQuotes Function

This function handles the scraping logic:

	•	It iterates through the website’s pages, starting from the first page.
	•	For each page, it retrieves the quote text, author, and tags using goquery.
	•	It stops scraping when 100 quotes are collected or there are no more pages.

Main Function

The main function starts the HTTP server and defines the /quotes endpoint:

http.HandleFunc("/quotes", func(w http.ResponseWriter, r *http.Request) {  
    quotes := scrapeQuotes(100)  
    w.Header().Set("Content-Type", "application/json")  
    json.NewEncoder(w).Encode(quotes)  
})  
log.Fatal(http.ListenAndServe(":8080", nil))  

Example API Response

Here’s an example response from the /quotes endpoint:

[  
  {  
    "text": "The greatest glory in living lies not in never falling, but in rising every time we fall.",  
    "author": "Nelson Mandela",  
    "tags": ["inspirational", "perseverance"]  
  },  
  {  
    "text": "The way to get started is to quit talking and begin doing.",  
    "author": "Walt Disney",  
    "tags": ["motivation", "action"]  
  }  
]  

Notes

	•	The application scrapes only up to 100 quotes, even if more are available.
	•	Quotes are returned in the same order as they appear on the website.

Contributing

Feel free to fork this repository and submit a pull request with your improvements.


