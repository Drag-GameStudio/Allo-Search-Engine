
### 🚀 Powered by ADG System
The original version of this document offers a superior layout and faster navigation. 
**Check it out here:** [Full Documentation Interface](https://draggame-adg-frontend.hf.space/docs/adg_doc_41991a4ab231ac1dab3d20862599e97b)
---

# Project Overview

## Project Title
**Dynamic Product Data Extraction and Display System**

---

## Project Goal
The primary objective of this project is to create a modular and scalable system for extracting, processing, and displaying product information dynamically. The software is designed to solve the challenge of aggregating product data, including characteristics and ratings, from HTML sources and presenting it in a user-friendly web interface. By leveraging a modular architecture and a handler-based workflow, the project ensures flexibility, maintainability, and ease of integration with other systems.

---

## Core Logic & Principles

### 1. **Modular Design with Handler-Based Workflow**
The backend of the project is built using a modular architecture where specific tasks are delegated to specialized handler modules. These handlers are responsible for:
- **Data Extraction:** Parsing HTML content to extract product details such as name, price, image, characteristics, and ratings.
- **Data Processing:** Transforming raw data into structured `Product` objects and organizing them based on user-defined criteria.
- **Data Sorting:** Sorting products based on ratings and other attributes, and generating structured dictionaries for characteristics and ratings.

The modular design ensures that each component is independent and reusable, allowing for easy debugging, testing, and future enhancements.

### 2. **MVC Pattern for Web Application**
The web application follows the Model-View-Controller (MVC) design pattern:
- **Model:** The backend processes product data, organizes it into structured formats, and serves it via a RESTful API.
- **View:** A dynamic HTML/JavaScript frontend displays product data in a table format, allowing users to query and interact with the data.
- **Controller:** The Flask server acts as the controller, managing API requests, rendering templates, and orchestrating the data flow between the backend and frontend.

### 3. **Key Technologies and Algorithms**
- **HTML Parsing:** The system uses BeautifulSoup to parse and extract structured data from HTML content. The `Finder` and `Parser` utility classes handle text normalization and element extraction.
- **Data Representation:** The `Product` class serves as the central data structure, encapsulating all product-related information, including characteristics and ratings.
- **Sorting and Organization:** The `HandlerOrder` class implements algorithms to sort products by ratings and organize characteristics and ratings into shared dictionaries for consistent display.
- **Web Framework:** Flask is used to create a lightweight backend that serves the HTML template and provides an API for fetching product data.
- **Frontend Interactions:** JavaScript dynamically updates the HTML table based on user input, ensuring a seamless user experience.

---

## Key Features

- **Automated Data Extraction:**
  - Extracts product details, characteristics, and ratings from HTML sources.
  - Handles both class-based and non-class-based HTML elements.

- **Dynamic Data Processing:**
  - Converts raw data into structured `Product` objects.
  - Normalizes text and converts price strings to numerical values.

- **Advanced Sorting and Organization:**
  - Sorts products by general ratings.
  - Organizes product characteristics and ratings into structured dictionaries for easy display.

- **Web-Based User Interface:**
  - Interactive frontend built with HTML and JavaScript.
  - Dynamically updates product data based on user input.
  - Displays product details in a tabular format with sortable columns.

- **Modular and Scalable Architecture:**
  - Handler-based workflow for easy maintenance and extensibility.
  - Clear separation of concerns between data extraction, processing, and display.

- **CI/CD Integration:**
  - Automated documentation generation using GitHub Actions and reusable workflows.

---

## Dependencies

### Backend
- **Python 3.x**
- **Flask:** Web framework for serving the application and handling API requests.
- **BeautifulSoup:** Library for parsing and extracting data from HTML.
- **YAML:** For configuration file parsing (e.g., `autodocconfig.yml`).

### Frontend
- **HTML/CSS/JavaScript:** For building the user interface.
- **AJAX:** For asynchronous communication with the backend API.

### CI/CD
- **GitHub Actions:** For automated documentation generation using the `autodoc.yml` workflow and external reusable workflows.

---

This project provides a robust and modular solution for extracting, processing, and displaying product data. Its handler-based architecture and MVC design ensure scalability and maintainability, making it an ideal choice for applications requiring dynamic data processing and visualization.
## Executive Navigation Tree

### 📄 AutoDoc System
- [Workflow](#autodoc-workflow)
- [Configuration](#autodoc-config)

### 📦 Product & Utility
- [Product Class](#product-class)
- [Utility Classes](#utility-classes)

### 📊 Data Handling
- [Data Handler](#data-handler)
- [Handler Order](#handler-order)
- [Handler Block](#handler-block)

### 🌐 Web Application
- [Request Handling](#request-handling)
- [Web Application](#web-application)
<a name="autodoc-workflow"></a>
## `.github/workflows/autodoc.yml` - Automated Documentation Workflow

### Functional Role
This file defines a GitHub Actions workflow named **AutoDoc**. Its primary purpose is to automate the generation of project documentation using an external reusable workflow.

### Workflow Logic
1. **Trigger Events**:
   - **Push to `main` branch**: Automatically triggers the workflow when changes are pushed to the `main` branch.
   - **Manual Dispatch**: Allows manual execution of the workflow via GitHub's UI.

2. **Job Configuration**:
   - **Permissions**: Grants write access to repository contents.
   - **Reusable Workflow**: Leverages `reuseble_agd.yml` from the external repository `Drag-GameStudio/ADG` for documentation generation.
   - **Secrets**: Uses the `ADG_API_TOKEN` secret for authentication.

### Data Flow
| Entity              | Type   | Role                          | Notes                                      |
|---------------------|--------|-------------------------------|--------------------------------------------|
| `ADG_API_TOKEN`     | Secret | Authentication Token          | Used to authenticate with the external workflow. |
| `reuseble_agd.yml`  | File   | Reusable Workflow Definition  | Contains the logic for automated documentation generation. |
| `main` branch       | Branch | Trigger for Workflow Execution | Pushes to this branch trigger the workflow. |

> **Note**: Ensure the `ADG_API_TOKEN` secret is correctly configured in the repository settings to avoid workflow failures.

---
<a name="autodoc-config"></a>
## `autodocconfig.yml` - AutoDoc Configuration File

### Functional Role
This configuration file defines the settings for the AutoDoc workflow, including file exclusions, build preferences, and documentation structure.

### Configuration Details
1. **Project Metadata**:
   - `project_name`: Specifies the name of the project as **"Project"**.
   - `language`: Sets the documentation language to **English (en)**.

2. **Ignored Files**:
   - Excludes specific file types and directories from the documentation process, such as Python bytecode files (`*.pyc`), cache directories (`__pycache__`), and environment folders (`venv`, `env`).

3. **Build Settings**:
   - `save_logs`: Disables saving of logs (`false`).
   - `log_level`: Sets the verbosity of logs to **2**.

4. **Structure Settings**:
   - `include_intro_links`: Enables the inclusion of introductory links in the documentation.
   - `include_intro_text`: Enables the inclusion of introductory text.
   - `include_order`: Ensures the documentation follows a specific order.

5. **Global File Usage**:
   - `use_global_file`: Indicates that a global configuration file is used (`true`).
   - `max_doc_part_size`: Limits the maximum size of each documentation part to **5000** characters.

### Data Flow
| Entity                   | Type   | Role                          | Notes                                      |
|--------------------------|--------|-------------------------------|--------------------------------------------|
| `project_name`           | String | Project Identifier            | Used as the title of the documentation.    |
| `ignore_files`           | List   | File Exclusion Rules          | Specifies files and directories to ignore. |
| `save_logs`              | Bool   | Log Saving Preference         | Determines if logs should be saved.        |
| `log_level`              | Int    | Log Verbosity Level           | Controls the level of detail in logs.      |
| `use_global_file`        | Bool   | Global Config File Usage      | Indicates if a global file is used.        |
| `max_doc_part_size`      | Int    | Documentation Part Size Limit | Limits the size of each documentation part.|

> **Warning**: Ensure that the `ignore_files` list is comprehensive to avoid including unnecessary files in the documentation.

---
<a name="product-class"></a>
## `Product` Class - Product Data Representation

### Functional Role
The `Product` class serves as the core data structure for storing and managing product-related information, including base data, characteristics, and ratings.

### Class Attributes and Methods
1. **Attributes**:
   - `name`: Name of the product.
   - `link`: URL to the product page.
   - `price`: Price of the product.
   - `image`: URL to the product image.
   - `characteristics`: Dictionary of product characteristics.
   - `rating`: Dictionary of product ratings.
   - `all_characteristics`: Dictionary of all characteristics across products.
   - `all_rate`: Dictionary of all ratings across products.

2. **Methods**:
   - `set_base_data(**kwargs)`: Sets the base attributes (`name`, `link`, `price`, `image`) of the product.
   - `set_characteristics(characteristics: dict)`: Updates the product's characteristics.
   - `set_rating(rating: dict[str, float])`: Updates the product's ratings.
   - `get_data()`: Prints the product's base data and general rating.
   - `set_all_characteristics_params(all_characteristics: dict)`: Maps all characteristics to the product.
   - `set_all_rate(all_rate: dict)`: Maps all ratings to the product.
   - `to_dict()`: Converts the product object into a dictionary for serialization.

### Data Flow
| Entity                  | Type   | Role                          | Notes                                      |
|-------------------------|--------|-------------------------------|--------------------------------------------|
| `name`                  | String | Product Name                  | Extracted from HTML.                       |
| `link`                  | String | Product URL                   | Extracted from HTML.                       |
| `price`                 | Float  | Product Price                 | Extracted and converted from HTML.         |
| `image`                 | String | Product Image URL             | Extracted from HTML.                       |
| `characteristics`       | Dict   | Product Characteristics       | Key-value pairs of product attributes.     |
| `rating`                | Dict   | Product Ratings               | Includes general and specific ratings.     |
| `all_characteristics`   | Dict   | All Characteristics           | Aggregated characteristics across products.|
| `all_rate`              | Dict   | All Ratings                   | Aggregated ratings across products.        |

---
<a name="utility-classes"></a>
## Utility Classes - `Parser` and `Finder`

### Functional Role
The `Parser` and `Finder` classes provide utility methods for text normalization and HTML element extraction, respectively.

---

### Key Methods

#### **`Parser` Class**
1. **`from_str_to_int(start: str, flag: tuple) -> float`**
   - **Responsibility:** Converts a string containing unwanted characters into a float.
   - **Logic:**
     - Iterates through the input string and removes characters specified in the `flag` tuple.
     - Converts the cleaned string into a float.

2. **`get_normal_text(text: str) -> str`**
   - **Responsibility:** Normalizes a string by removing leading/trailing characters and truncating at the first newline.
   - **Logic:**
     - Removes the first 17 characters from the input string.
     - Truncates the string at the first newline character.

#### **`Finder` Class**
1. **`find_classes(type_item, class_name) -> list`**
   - **Responsibility:** Finds all HTML elements with a specific class or tag.
   - **Logic:**
     - Uses BeautifulSoup's `find_all()` method to locate elements with the specified class or tag.

2. **`find_without_class() -> list`**
   - **Responsibility:** Finds all HTML elements, regardless of class or tag.
   - **Logic:**
     - Uses BeautifulSoup's `find_all()` method without filtering by class.

---

### Data Flow
| Entity             | Type   | Role                              | Notes                                       |
|---------------------|--------|-----------------------------------|---------------------------------------------|
| `start`            | String | Input String                      | Input string to be converted to a float.    |
| `flag`             | Tuple  | Unwanted Characters               | Characters to be removed from the string.   |
| `html_code`        | String | HTML Code                         | Input HTML code for parsing.                |

> **Warning**: Ensure the input HTML structure matches the expected format for accurate parsing and extraction.


markdown
<a name="data-handler"></a>
## `DataHandler` Class - Product Data Extraction and Processing

### Functional Role
The `DataHandler` class is responsible for extracting and processing product data from HTML elements. It initializes `Product` objects and populates their attributes with base data, characteristics, and ratings.

### Key Methods
1. **`get_base_data()`**:
   - Extracts base product data (name, link, price, image) from `classes_data`.
   - Initializes a `Product` object with the extracted data.

2. **`get_characteristics(product: Product)`**:
   - Extracts product characteristics from `others_data`.
   - Updates the `Product.characteristics` attribute with a dictionary of key-value pairs.

3. **`get_rate(product: Product)`**:
   - Extracts product ratings (general and specific) from `classes_data`.
   - Updates the `Product.rating` attribute with a dictionary of ratings.

### Data Flow
| Entity          | Type   | Role                          | Notes                                      |
|------------------|--------|-------------------------------|--------------------------------------------|
| `classes_data`   | Dict   | HTML Elements with Classes    | Input data for extracting structured elements. |
| `others_data`    | Dict   | HTML Elements without Classes | Input data for extracting unstructured elements. |
| `product`        | Object | Product Instance              | The `Product` object being populated.      |

> **Warning**: Ensure the structure of `classes_data` and `others_data` matches the expected HTML structure to avoid errors during data extraction.

### Technical Logic Flow
1. **Base Data Extraction**:
   - Extracts product name and link from `classes_data` using the key `"/[document]/product-card/product-card__content/product-card__title"`.
   - Extracts and converts product price using `Parser.from_str_to_int()`.
   - Extracts product image URL using the key `"/[document]/product-card/product-card__pictures/product-card__img/image-carousel/image-carousel__container/image-carousel__slides/is-active/gallery__img"`.
   - Initializes a `Product` object and sets its base data.

2. **Characteristics Extraction**:
   - Extracts characteristics from `others_data` using the key `"/[document]/p-view__specs/p-specs/p-specs__groups-list/p-specs__group/tbody/tr/p-specs__cell"`.
   - Normalizes characteristic names using `Parser.get_normal_text()`.

3. **Ratings Extraction**:
   - Extracts general rating from `classes_data` using the key `"/[document]/product-estimate/average-estimate/average-estimate__rating"`.
   - Extracts additional ratings (if available) using `HandlerBlock.Handler()` and its sub-methods.
   - Updates the `Product.rating` attribute with the extracted ratings.

> **Error Handling**: If ratings are not found, the method sets the `Product.rating` attribute to `None`.


markdown
<a name="handler-order"></a>
## `HandlerOrder` Class - Product Sorting and Organization

### Functional Role
The `HandlerOrder` class is responsible for sorting a list of `Product` objects by their general rating and organizing their characteristics and ratings into shared structures. It ensures that all products are aligned with a consistent set of characteristics and rating types for further processing or display.

---

### Key Methods

#### 1. **`sort_orders()`**
- **Responsibility:** Sorts the list of `Product` objects in descending order based on their general rating.
- **Logic:**
  - Implements a bubble sort algorithm to reorder products.
  - Compares the `general` rating of adjacent products and swaps them if necessary.
  - Uses a `try-except` block to handle cases where a product's `rating["general"]` is missing.

#### 2. **`get_colums()`**
- **Responsibility:** Creates a dictionary of all unique characteristics across the products.
- **Logic:**
  - Iterates over each product's `characteristics` dictionary.
  - Adds each characteristic key to the `colums` dictionary with a default value of `"-"`.

#### 3. **`get_all_characteristics()`**
- **Responsibility:** Updates each product's `all_characteristics` attribute to align with the shared `colums` dictionary.
- **Logic:**
  - Iterates over all products.
  - Calls the `set_all_characteristics_params()` method of each product, passing the `colums` dictionary.

#### 4. **`get_colums_rate()`**
- **Responsibility:** Creates a dictionary of all unique rating types across the products.
- **Logic:**
  - Iterates over each product's `rating` dictionary.
  - Adds each rating key to the `colums_rate` dictionary with a default value of `"-"`.

#### 5. **`get_all_rate()`**
- **Responsibility:** Updates each product's `all_rate` attribute to align with the shared `colums_rate` dictionary.
- **Logic:**
  - Iterates over all products.
  - Calls the `set_all_rate()` method of each product, passing the `colums_rate` dictionary.

---

### Data Flow
| Entity             | Type   | Role                              | Notes                                       |
|---------------------|--------|-----------------------------------|---------------------------------------------|
| `products`          | List   | List of `Product` objects         | The main input to the class.                |
| `colums`            | Dict   | Shared Characteristics Dictionary | Aggregates all unique product characteristics. |
| `colums_rate`       | Dict   | Shared Ratings Dictionary         | Aggregates all unique product rating types. |

---

### Technical Logic Flow

1. **Sorting Products by Rating (`sort_orders`)**:
   - Iterates through the `products` list using a nested loop.
   - Compares the `general` rating of adjacent products.
   - Swaps products if the current product's rating is lower than the next product's rating.
   - Handles missing `general` ratings gracefully using a `try-except` block.

2. **Extracting Shared Characteristics (`get_colums`)**:
   - Iterates through each product's `characteristics` dictionary.
   - Collects all unique keys into a shared `colums` dictionary.

3. **Aligning Characteristics (`get_all_characteristics`)**:
   - Calls `set_all_characteristics_params()` on each product, passing the shared `colums` dictionary.
   - Ensures all products have the same set of characteristics.

4. **Extracting Shared Ratings (`get_colums_rate`)**:
   - Iterates through each product's `rating` dictionary.
   - Collects all unique keys into a shared `colums_rate` dictionary.

5. **Aligning Ratings (`get_all_rate`)**:
   - Calls `set_all_rate()` on each product, passing the shared `colums_rate` dictionary.
   - Ensures all products have the same set of ratings.

---
<a name="handler-block"></a>
## `HandlerBlock` Class - HTML Parsing for Structured Data

### Functional Role
The `HandlerBlock` class is responsible for parsing HTML blocks and extracting structured data. It separates elements with and without classes into distinct dictionaries, which can be further processed by other components.

---

### Key Methods

#### 1. **`Handler()`**
- **Responsibility:** Extracts and returns both class-based and non-class-based HTML elements as dictionaries.
- **Logic:**
  - Calls `handler_classes()` to extract elements with classes.
  - Calls `handler_element_without_classes()` to extract elements without classes.
  - Returns a tuple containing the results of both methods.

#### 2. **`handler_classes()`**
- **Responsibility:** Extracts HTML elements with classes and organizes them into a dictionary.
- **Logic:**
  - Uses `Finder.find_classes()` to locate all elements with classes.
  - Constructs a dictionary where keys are element paths and values are lists of elements.

#### 3. **`handler_element_without_classes()`**
- **Responsibility:** Extracts HTML elements without classes and organizes them into a dictionary.
- **Logic:**
  - Uses `Finder.find_without_class()` to locate all elements without classes.
  - Constructs a dictionary where keys are element paths and values are lists of elements.

#### 4. **`get_item_path()`**
- **Responsibility:** Constructs a unique path for a given HTML element.
- **Logic:**
  - Traverses the element's parent hierarchy to build a path string.
  - Includes the element's class name or tag name in the path.

---

### Data Flow
| Entity             | Type   | Role                              | Notes                                       |
|---------------------|--------|-----------------------------------|---------------------------------------------|
| `block_code`        | String | HTML Code                        | Input HTML block to be parsed.              |
| `class_data`        | Dict   | Class-Based Elements             | Output dictionary of elements with classes. |
| `element_data`      | Dict   | Non-Class-Based Elements         | Output dictionary of elements without classes. |

---

### Technical Logic Flow

1. **Parsing HTML Block (`Handler`)**:
   - Calls `handler_classes()` to extract elements with classes.
   - Calls `handler_element_without_classes()` to extract elements without classes.
   - Returns a tuple containing both dictionaries.

2. **Extracting Class-Based Elements (`handler_classes`)**:
   - Uses `Finder.find_classes()` to locate elements with classes.
   - Builds a dictionary where keys are element paths (constructed by `get_item_path()`) and values are lists of elements.

3. **Extracting Non-Class-Based Elements (`handler_element_without_classes`)**:
   - Uses `Finder.find_without_class()` to locate elements without classes.
   - Builds a dictionary where keys are element paths (constructed by `get_item_path()`) and values are lists of elements.

4. **Constructing Element Paths (`get_item_path`)**:
   - Traverses the element's parent hierarchy.
   - Constructs a path string using class names or tag names.

---
<a name="request-handling"></a>
## Request Handling and Product Data Processing (`main.py`)

### Functional Role
The `main.py` file serves as the core logic for handling HTTP requests, fetching HTML content, parsing product data, and organizing it into structured objects. It acts as the intermediary between the web interface and the backend data processing pipeline.

---

### Key Classes and Methods

#### **`Req_part` Class**
Handles HTTP requests to fetch HTML content and extract specific elements from the response.

| Method                  | Parameters                                                                 | Return Type | Role                                                                 |
|-------------------------|----------------------------------------------------------------------------|-------------|----------------------------------------------------------------------|
| `__init__(url: str)`    | `url`: Base URL for the HTTP requests.                                     | None        | Initializes the `Req_part` instance with the base URL.              |
| `get_html_code(prompt: str) -> str` | `prompt`: Search query string.                                   | String      | Fetches the HTML code for a given search query from the URL.         |
| `get_element(element_type: str, element_class: str, html_code: str) -> list` | `element_type`: HTML tag type. <br> `element_class`: Class name of the element. <br> `html_code`: HTML content to parse. | List        | Extracts a list of HTML elements matching the specified type and class. |

#### **`HandlerCode` Class**
Coordinates the process of fetching, parsing, and organizing product data.

| Method                  | Parameters                                                                 | Return Type | Role                                                                 |
|-------------------------|----------------------------------------------------------------------------|-------------|----------------------------------------------------------------------|
| `__init__(url: str, find_items: str, prompt: str)` | `url`: Base URL for requests. <br> `find_items`: Class name to locate product blocks. <br> `prompt`: Search query string. | None        | Initializes the `HandlerCode` instance with the URL, search query, and target class. |
| `make_req(url: str, find_items: str, prompt: str) -> list` | `url`: URL for the request. <br> `find_items`: Class name to locate product blocks. <br> `prompt`: Search query string. | List        | Fetches HTML content and extracts product blocks matching the specified class. |
| `hendler_blocks(blocks: list) -> list` | `blocks`: List of HTML blocks containing product data.          | List        | Processes each block to extract product data, characteristics, and ratings. |
| `get_characteristics(html_code: str, RP_class: Req_part, product: Product) -> Product` | `html_code`: HTML content. <br> `RP_class`: Instance of `Req_part`. <br> `product`: Product object to update. | Product     | Extracts product characteristics and updates the `Product` object. |
| `get_all_order(max_page: int = 3) -> list` | `max_page`: Maximum number of pages to process.                 | List        | Iterates through pages to fetch and process product data.            |
| `add_filter(filter: str, value: any)` | `filter`: Filter type (e.g., price range). <br> `value`: Filter value. | None        | Adds a filter to the request parameters.                            |
| `apply_param()`          | None                                                                      | None        | Appends filters to the base URL for subsequent requests.             |

#### **`Get_orders(prompt: str)` Function**
Orchestrates the process of fetching, processing, and organizing product data based on a user-provided search query.

| Parameter               | Type   | Role                              | Notes                                       |
|-------------------------|--------|-----------------------------------|---------------------------------------------|
| `prompt`                | String | User search query.                | Used to fetch relevant product data.        |

**Logic:**
1. Initializes a `HandlerCode` instance with the base URL, search query, and target class for product blocks.
2. Applies filters (if any) to the request URL.
3. Fetches and processes product data from the specified number of pages using `get_all_order()`.
4. Passes the processed product list to `HendlerOrder` for sorting and organizing.
5. Returns the final list of `Product` objects.

---
<a name="web-application"></a>
## Web Application (`visual.py`)

### Functional Role
The `visual.py` file implements a Flask-based web application that serves an HTML interface and provides an API endpoint for fetching processed product data.

---

### Key Components

#### **Flask Application**
| Method                  | Parameters                                                                 | Return Type | Role                                                                 |
|-------------------------|----------------------------------------------------------------------------|-------------|----------------------------------------------------------------------|
| `start_app()`           | None                                                                      | None        | Starts the Flask server on the specified port.                       |
| `render_template()`     | None                                                                      | HTML        | Serves the `index.html` template to the client.                      |
| `get_orders()`          | None                                                                      | JSON        | Fetches product data using `main.Get_orders()` and returns it as JSON.|

---

### Functional Flow

1. **User Interaction:**
   - User accesses the root URL (`/`) of the web application.
   - The `render_template()` method serves the `index.html` file, which contains the user interface.

2. **Data Request:**
   - User enters a search query and submits it via the "Get orders" button.
   - The frontend sends a GET request to the `/get_orders` endpoint with the query as a parameter.

3. **Backend Processing:**
   - The `get_orders()` method retrieves the query parameter from the request.
   - Calls `main.Get_orders(prompt)` to fetch and process product data.
   - Converts the resulting `Product` objects into dictionaries using the `to_dict()` method.
   - Returns the product data as a JSON response.

4. **Frontend Update:**
   - The frontend parses the JSON response.
   - Dynamically updates the HTML table with product data, including characteristics and ratings.

---

### Data Flow
| Entity                  | Type   | Role                              | Notes                                       |
|-------------------------|--------|-----------------------------------|---------------------------------------------|
| `prompt`                | String | User search query.                | Passed from the frontend to the backend.    |
| `products`              | List   | List of `Product` objects.        | Processed product data returned by `Get_orders()`. |
| `products_list`         | List   | List of product dictionaries.     | Serialized product data for JSON response.  |

> **Note:** The Flask app listens on `0.0.0.0` and the default port is `800`. Ensure the port is available before starting the application.

    