# GCI CLI Documentation

The GCI Sales Automation Solution CLI is a command-line interface tool that allows you to perform various operations related to the sales automation solution. You can use these commands to create and manage groups, enrich data, export data, and more.

## Prerequisites

- Python 3.9 or higher
- Internet connection

## Installation Steps

### 1. Install ngrok

 ngrok is required for webhook functionality in our application.

 a. Visit the [ngrok download page](https://ngrok.com/download).
 b. Download and install the version appropriate for your operating system.
 c. After installation, sign up for a free ngrok account and authenticate your ngrok client by running:

ngrok authtoken YOUR_AUTHTOKEN

 Replace `YOUR_AUTHTOKEN` with the token provided in your ngrok dashboard.

### 2. Install pipx

 pipx is used to install and run Python applications in isolated environments. Visit [here](https://pipx.pypa.io/stable/installation/)

### 3. Install GCI Sales Automation Solution

 Use pipx to install our solution from the provided wheel file:

pipx install path/to/gci_sales_automation_solution-0.1.0-py3-none-any.whl

 Replace `path/to/gci_sales_automation_solution-0.1.0-py3-none-any.whl` with the actual path to the .whl file we provided.

### 4. Set up Proxycurl API Key

 After installation, you need to set up your Proxycurl API key:

gci set-api-keys YOUR_PROXYCURL_API_KEY

 Replace `YOUR_PROXYCURL_API_KEY` with your actual Proxycurl API key.

## Verification

 To verify that the installation was successful, run:

gci --help

 This should display the help information for our CLI tool.

## Updating the Application

 When we provide an updated version of the application, you can install it using:

pipx install --force path/to/new_gci_sales_automation_solution-X.X.X-py3-none-any.whl

 Replace `X.X.X` with the new version number and adjust the path as necessary.

## Troubleshooting

 If you encounter any issues during installation or usage, please contact our support team at <support@example.com>.

## Using the CLI

To use the CLI, open a terminal or command prompt and run the following command:

 gci [COMMAND] [OPTIONS]

Replace [COMMAND] with one of the available commands listed below, and [OPTIONS] with the necessary flags and arguments for that command.

The CLI supports various options and flags that you can use to customize the behavior of the commands. Options are typically prefixed with -- and allow you to pass in
additional information or settings. For example, the --group option allows you to specify the name of the group you want to work without

## CLI Commands

### set-api-keys

Description: Set and store the Proxycurl API key. This key is required for the enrichment process to work correctly.

Usage:

 gci set-api-keys --proxycurl-api-key <proxycurl-api-key>

Example:

 gci set-api-keys --proxycurl-api-key abc123

Options:

 • --proxycurl-api-key <proxycurl-api-key>: The Proxycurl API key to be stored.

### super

Description: This command combines the steps of creating a group from a CSV file, enriching the records, and exporting the data to a CSV file. It's a convenient way to
perform all these tasks in a single command.

Usage:

 gci super --group-name <group-name> --csv-file <csv-file> [--description <description>] [--output-file <output-file>] [--auto-confirm] [--skip-review]

Example:

 gci super --group-name "My Group" --csv-file data.csv --description "This is my group" --output-file output.csv

Options:

 • --group-name <group-name>: The name of the group to create and process.
 • --csv-file <csv-file>: The path to the CSV file containing the data to be processed.
 • --description <description>: The description of the group (optional).
 • --output-file <output-file>: The path to the output CSV file where the enriched data will be exported (optional).
 • --auto-confirm: Automatically confirm the enrichment process without manual review.
 • --skip-review: Skip the review process and export the data directly.

### create-group-from-csv

Description: Create a new group in the system by importing data from a CSV file.

Usage:

 gci create-group-from-csv --name <name> --csv-file <csv-file> [--description <description>]

Example:

 gci create-group-from-csv --name "My Group" --csv-file data.csv --description "This is my group"

Options:

 • --name <name>: The name of the group to create.
 • --csv-file <csv-file>: The path to the CSV file containing the data to be imported.
 • --description <description>: The description of the group (optional).

### enrich

Description: Enrich the records in a specified group by fetching additional data from external sources.

Usage:

 gci enrich --group <group>

Example:

 gci enrich --group "My Group"

Options:

 • --group <group>: The name of the group to enrich.

### review

Description: Review the records in a specified group that need reconciliation after the enrichment process.

Usage:

 gci review --group <group>

Example:

 gci review --group "My Group"

Options:

 • --group <group>: The name of the group to review.

### export

Description: Export the enriched data for a specified group to a CSV file.

Usage:

 gci export --group <group> --output-file <output-file>

Example:

 gci export --group "My Group" --output-file output.csv

Options:

 • --group <group>: The name of the group to export.
 • --output-file <output-file>: The path to the output CSV file where the data will be exported.

### list-groups

Description: List all the groups that have been created in the local CRM.

Usage:

 gci list-groups

Example:

 gci list-groups

### delete-group

Description: Delete a specified group from the local CRM.

Usage:

 gci delete-group --name <name>

Example:

 gci delete-group --name "My Group"

Options:

 • --name <name>: The name of the group to delete.

### status

Description: Display the current status of a specified group, including the total number of records, the number of enriched records, and the last updated and created
timestamps.

Usage:

 gci status --group <group>

Example:

 gci status --group "My Group"

Options:

 • --group <group>: The name of the group to check the status for.
