# Final Project

The final project will be the culmination of all of the skills learned and practiced in this class. Students will build an application that has a custom backend (e.g., Flask with a PostGIS database) hosted on the cloud that can be publicly accessed and returns custom responses based on user inputs. Expectations are that API responses will be communicated in multiple ways: a static chart or map, interactive maps, formatted statistics among others.

## Proposal

A project proposal is due Thursday, Nov 19th. Please place your proposal in your project GitHub repo in a file called `proposal.md`. Write the proposal in markdown (how all class READMEs are written). If you need a markdown reference, check out [GitHub's](https://guides.github.com/features/mastering-markdown/). There are many more online.

The proposal consists of:

1. Abstract — a paragraph description of the problem/situation/etc. your application is addressing.
2. List of data sources you intend to use for this project. For each data source, please list:
   * Where you can get access to the dataset (e.g., a URL, government agency, third-party API, BigQuery public dataset, etc.)
   * Size of dataset (if applicable)
   * How you intend to host the dataset (if applicable) — PostgreSQL on AWS RDS, Google BigQuery, somewhere else
   * Do you have access to this data?

3. Wireframes of the webpages for your project. See [this page](https://careerfoundry.com/en/blog/ux-design/how-to-create-your-first-wireframe/) for guidance on creating wireframes. Hand-drawn or digital are both acceptable, but please scan or take pictures of the hand-drawn ones for inclusion in the repo. Link the images in the proposal markdown. Interactive wireframes are acceptable too. Many free and paid tools exist for creating wireframes (Adobe Wireframe XD, [MockFlow](https://mockflow.com/), [Figma](https://www.figma.com/wireframe-tool/), etc.)

## Project Requirements

* Data
  * Your application will use...
    * Data that is hosted on your own AWS RDS PostgreSQL/PostGIS database that you and your partner manage
    * Data from third-party API calls (e.g., Google Maps APIs, Census API, Twitter) that is performed ad hoc based on user interactions
  * For any data processing steps to alter original data sources (e.g., buffering a points table for faster querying), please document all of the steps.
* Application
  * Frontend — has an HTML frontend (see below for more)
    * User interface
      * HTML form that interacts with Flask backend
      * "Submit" button takes user to results page
      * On results page, give user the ability to do another query or go back to the start page again
      * Pages are linkable so user can share results with anyone without having to fill out the form again
    * Pages
      * Introduction page — this page will educate the user of the problem statement, give them an introduction to the data if needed, have some visuals and explanatory text
      * Requests Page (can be combined with Intro Page)
        * Bad requests lead to good errors letting user know that their input was not valid. Bad requests should redirect to Requests page.
      * Results Page
        * Option to download response
        * Interactive HTML map using mapping library of choice (Mapbox, Google Maps, etc.)
        * Summary statistics and/or descriptions, including charts, tables
      * 404 page — if someone requests a page that does not exist, a proper 404 page should be returned. Silly 404 pages that have bad puns are encouraged but not mandatory.
  * Backend — has a Python/Flask backend with a PostgreSQL database supporting many data operations (see below for more)
  * HTML responses
    * All responses have explicit response, status code, and content type (mimetype). See the [Flask Response class](https://flask.palletsprojects.com/en/1.1.x/api/#response-objects)
  * Runs in a Python environment
    * Include a `requirements.txt` file to detail core dependencies of project
  * Architecture diagram of your application. See [example here](https://reinvently.com/wp-content/uploads/2019/08/scheme.jpg).
* Backend — Python script (app) running Flask
  * Python application functions all have full docstrings
  * All dynamic queries should properly template parameters to avoid SQL injection situations
  * Credentials for any third-party APIs are stored in accompanying JSON files instead of being hard-coded into the Python script, making sure not to commit keys to GitHub repo
  * Contains (templated) queries to your DB
* Frontend — built with dynamically templated HTML pages
  * Must have full HTML tags (properly formatted document with `DOCTYPE`, `html`, `head`, and `body` tags), and `head` section is filled in with relevant information
  * Use static CSS for styling the page, where CSS sheets are included in application directory or via CDN
  * Include at least two partial HTML template to include in the full HTML response page (e.g., a form HTML snippet that is used in multiple locations, map HTML that's included elsewhere, etc.)
  * Give option on page to run another query (e.g., gives user the option to explore areas adjacent to region of interest)
  * Works with backend to ensure that inputs are valid
* Application Development
  * All code is to be committed to a GitHub repository that you share with your partner
  * No API credentials, DB credentials, or otherwise should be committed to the repo. Instead, commit files that are in the same structure but do not contain the API keys, passwords, hosts, etc. A good practice is to have files like `pg-credentials.json.sample` committed but in the `.gitignore` file `pg-credentials.json` is added to avoid accidentally committing.
  * Each person in the group must contribute roughly equal contributions of code to the repository
