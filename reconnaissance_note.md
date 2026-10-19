# GROUP 7 RECONNAISSANCE NOTE: STEAM TOP SELLERS

**Institution:** Uganda Christian University, Mukono, Uganda
**Programme:** Bachelor of Science in Data Science and Analytics, Year 2
**Course Unit:** DSC2107 – Data Mining and Wrangling
**Website:** Steam Top Sellers
**Starting Page:** https://store.steampowered.com/search/?filter=topsellers
**Date Checked:** 13 October 2026

## 1. Purpose

The purpose of this reconnaissance was to understand how the Steam Top Sellers website is organised and determine how our group could collect the required data.

Group 7 planned to collect the first 500 ranked game listings daily for seven consecutive days. The information to be collected included the game rank, title, category, current price, original price, discount percentage, release date, review summary, supported platforms, and collection timestamp (`scraped_at`).

## 2. Website Inspection

We inspected the Steam Top Sellers page using a web browser and examined its HTML structure using Python's `requests` and `BeautifulSoup` libraries.

We observed that game listings appear in elements identified by the class `search_result_row`. These elements contain information such as game titles, prices, release dates, review summaries, and platform icons. The game URL can also be used to obtain its application ID (`app_id`).

We also checked Steam's `robots.txt` file to understand its rules for automated access. The scraper was intended to follow the website's access rules and use reasonable delays between requests.

Steam uses a `start` parameter in its search URL to move through the results. For example, different values such as `start=0`, `start=25`, and `start=50` can be used to request different sections of the listings. Our scraper would use pagination to collect the required 500 records.

## 3. Chosen Approach

We chose Python because it is suitable for collecting and processing data. We planned to use the following libraries:

* **Requests:** To send requests to the Steam website and retrieve page content.
* **BeautifulSoup:** To extract game information from the HTML.
* **pandas:** To organise the collected information into a table and save it as a CSV file.

This approach was selected because it is relatively simple and suitable for our level of study. It also avoids the need for browser automation tools such as Selenium, provided that the required information is available in the HTML returned by the website.

## 4. Data Fields

We planned to collect the following information for each game:

| Field              | Description                                                      |
| ------------------ | ---------------------------------------------------------------- |
| `app_id`           | The unique application ID of the game.                           |
| `rank`             | The game's position in the collected listing.                    |
| `category`         | The category from which the game was collected.                  |
| `title`            | The name of the game.                                            |
| `price`            | The current price of the game.                                   |
| `original_price`   | The original price before a discount, where available.           |
| `discount_percent` | The discount percentage, where it can be obtained or calculated. |
| `release_date`     | The game's recorded release date.                                |
| `review_summary`   | A summary of the available user reviews.                         |
| `platforms`        | The supported platforms, such as Windows, macOS, and Linux.      |
| `scraped_at`       | The date and time when the record was collected.                 |

These fields would help us study game prices, discounts, rankings, categories, and other characteristics of the collected listings.

## 5. Responsible Web Scraping

Our group aimed to collect data responsibly and avoid placing unnecessary pressure on the Steam website.

First, we planned to use a descriptive `User-Agent` identifying our project and course, together with valid contact information where appropriate.

Second, we planned to wait three seconds between page requests to reduce the number of requests sent within a short period.

Third, we would collect only publicly available game information and avoid collecting personal user information or attempting to access private accounts.

Finally, if Steam blocked our requests or presented a CAPTCHA, we would stop the automated collection, document the problem, and review our approach rather than attempting to bypass the restriction.

## 6. Limitations

Our project had several possible limitations.

**Changes to the website:** Steam may change its HTML structure or class names. If this happens, the scraper may need to be updated to continue extracting the correct information.

**Regional pricing:** Game prices may differ depending on the country and currency. Therefore, our collected prices represent the information available to our scraper during the collection period and may not match prices in other regions.

**Changing rankings:** Steam rankings can change over time. Our collected data represents the listings observed at the time of collection and should not be treated as a permanent ranking.

**Missing information:** Some games may not display an original price, discount percentage, release date, or review summary. These fields may therefore contain missing values that require careful handling during data cleaning.

**Collection interruptions:** Network problems or website restrictions may prevent the scraper from collecting the full target of 500 records on a particular day. The number of records collected should be checked after every run.

## Conclusion

The reconnaissance helped Group 7 understand the structure of the Steam Top Sellers website and identify a suitable method for collecting game information. Python, Requests, BeautifulSoup, and pandas were selected as the main tools for the project.

The group also identified important data fields, considered possible scraping challenges, and established practices for responsible data collection. This preparation provided a foundation for collecting, merging, cleaning, and analysing Steam game data as part of the DSC2107 Data Mining and Wrangling assignment.

**Prepared by:** Group 7
**Uganda Christian University**
