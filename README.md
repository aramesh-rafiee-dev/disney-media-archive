# Disney Corporate & Media Archive

A large, deeply-nested Python data structure (~1,700 lines) modeling The Walt Disney Company — its history, corporate structure, films, and subsidiaries — paired with scripts that traverse and analyze that data.

## Overview

This project models real-world corporate and media data as a single large nested Python dictionary, then demonstrates how to reliably extract information from deeply nested structures — a common task in data processing and ETL work.

## What the Data Covers

- Company founders, founding date, and historical name changes
- Corporate structure: management, stock symbol, financials (revenue, net profit, assets), employee count
- A large catalog of Disney films with director(s), producer(s), writer(s), cast, country, language, and production cost — including cases with a single value and cases with multiple values (lists) for the same field
- Subsidiaries and affiliated companies (Marvel, ESPN, National Geographic, A&E Networks, etc.) with their own nested details

## Tech Stack

- **Python 3** (standard library only — `datetime` for date calculations)

## How It Works

The data is intentionally irregular — some films have a single `director`, others have a list of `directors`; some fields are spelled slightly differently across entries. The analysis scripts are written to handle this real-world messiness rather than assuming a perfectly uniform schema:

1. **Actor lookup**: iterates through every movie entry and prints the cast list per title.
2. **Nested key lookup**: drills down through several layers of nested dictionaries (`Products → music → DisneySongs → ...`) to reach a specific songwriter credit — demonstrating safe traversal of deeply nested data with `.get()` fallbacks instead of direct key access (which would crash on missing keys).
3. **Computed field**: calculates how many years ago each film was released, using `datetime.now().year` and handling the fact that the publication-date key is spelled differently in different entries (`PublicationDate` vs `Publicationdate`).

## Setup

bash
python disney_archive.py

No external dependencies — runs with the Python standard library.

## What I'd Build Next

- Normalize the inconsistent key names (`Publicationdate` vs `PublicationDate`, singular vs plural fields) into a consistent schema.
- Move the data out of a hardcoded dictionary into a JSON file, loaded at runtime.
- Add a simple query interface (e.g. "list all films from the 1940s" or "find all films with a given actor") instead of fixed, single-purpose loops.

---

**Author:** Aramesh Rafiee
[github.com/aramesh-rafiee-dev](https://github.com/aramesh-rafiee-dev) · [linkedin.com/in/aramesh-rafiee-dev](https://www.linkedin.com/in/aramesh-rafiee-dev/)
