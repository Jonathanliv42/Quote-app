
Here’s a detailed set of instructions on how to build and run the Go application locally:

Step 1: Install Go

	1.	Download Go:
Go to the official Go website and download the installer for your operating system.
	2.	Install Go:
Follow the instructions in the installer to complete the installation. On macOS, you can also install Go using Homebrew:

brew install go


	3.	Verify the installation:
Open a terminal and type:

go version

You should see the installed version of Go.

Step 2: Clone the Project

	1.	Open the terminal and navigate to the directory where you want to store the project.
For example:

cd ~/Projects


	2.	Clone the repository containing the project code:

git clone <repository-url>

Replace <repository-url> with the actual URL of your GitHub repository.

	3.	Navigate into the project directory:

cd <project-directory>



Step 3: Initialize the Go Module

	1.	Ensure you’re in the project directory. Then initialize a Go module:

go mod init <module-name>

Replace <module-name> with a relevant name (e.g., quotes-app). This will create a go.mod file.

	2.	Download the required dependencies:

go get github.com/PuerkitoBio/goquery



Step 4: Build the Application

	1.	Build the Go application:

go build -o quotes-app main.go

This will create an executable file named quotes-app in your project directory.

Step 5: Run the Application

	1.	Run the application directly:

./quotes-app


	2.	The server will start, and you’ll see an output like:

Scraping page 1: https://quotes.toscrape.com/page/1/
Scraping page 2: https://quotes.toscrape.com/page/2/
Listening on :8080


	3.	Open your browser or use a tool like curl or Postman to test the endpoint:

http://localhost:8080/quotes



Step 6: Verify Output

The application will return a JSON array containing 100 quotes. Each quote will include the text, author, and tags.

Example output:

[
  {
    "text": "The world as we have created it is a process of our thinking. It cannot be changed without changing our thinking.",
    "author": "Albert Einstein",
    "tags": ["change", "deep-thoughts", "thinking", "world"]
  },
  {
    "text": "It is our choices, Harry, that show what we truly are, far more than our abilities.",
    "author": "J.K. Rowling",
    "tags": ["abilities", "choices"]
  }
]

Troubleshooting

	•	Missing dependencies? Run:

go mod tidy

This ensures all required dependencies are downloaded.

	•	Error with ports? Ensure port 8080 is not in use. You can change the port in the code:

log.Fatal(http.ListenAndServe(":8080", nil))

Replace 8080 with a different port (e.g., 9090).

	•	Permission error on macOS? Ensure the binary is executable:

chmod +x quotes-app



This process will help you set up, build, and run the Go application successfully on your local machine.
