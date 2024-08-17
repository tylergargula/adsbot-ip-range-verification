# ADsBot Verification Notebook

## Overview

This Jupyter Notebook is designed to verify the crawling of AdsBot using Google IP ranges. It performs the following high-level tasks:

1. **Load Data**: Reads the crawl log data from a CSV file into a Pandas DataFrame.
2. **Fetch Google IP Ranges**: Retrieves the list of Google IP ranges from an external JSON file hosted by Google.
3. **Extract and Process IP Ranges**: Extracts IPv4 and IPv6 ranges from the JSON data and computes the start and end IP addresses for each range.
4. **Verify IP Addresses**: Checks if the IP addresses in the crawl log data fall within the Google IP ranges.
5. **Export Results**: Exports the verification results to a CSV file.

## Detailed Steps

1. **Load the Data**:
   - Reads the crawl log data from `/data/`.
   - Creates a copy of the DataFrame for processing.

2. **Fetch Google IP Ranges**:
   - Sends a GET request to `https://developers.google.com/static/search/apis/ipranges/special-crawlers.json`.
   - Parses the JSON response to extract IP ranges.

3. **Extract and Process IP Ranges**:
   - Separates the IP ranges into IPv4 and IPv6.
   - Computes the start and end IP addresses for each range using the `ipaddress` library.
   - Creates DataFrames for IPv4 and IPv6 ranges.

4. **Verify IP Addresses**:
   - Defines a function to check if an IP address falls within a given range.
   - Iterates through the crawl log data and checks each IP address against the Google IP ranges.
   - Adds a new column `is_google` to the DataFrame to indicate whether each IP address is from Google.

5. **Export Results**:
   - Exports the DataFrame with the verification results to `export/{datetime}_AdsBot_Verification.csv`.
   - Prints a success message upon completion.

## Benefits for an Application

- **Security and Compliance**: Ensures that the AdsBot crawls are legitimate and originate from Google's IP ranges, enhancing security and compliance.
- **Data Integrity**: Helps maintain the integrity of crawl log data by verifying the source of the crawls.
- **Performance Monitoring**: Assists in monitoring the performance and reach of AdsBot crawls, providing insights into how often and from where the crawls are occurring.
- **Automated Verification**: Automates the process of verifying IP addresses, saving time and reducing the potential for human error.

## Packages Used
- pandas
- requests