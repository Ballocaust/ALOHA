📊 HOUSEpitality Family Financial Dashboard (JSON Fetch)This is a single-file, client-side web application designed to display near-real-time financial reports from multiple restaurant locations. It is specifically built to be a read-only dashboard that consumes processed data from an external JSON endpoint, making it ideal for integration with automation tools like Restaurant 365 (R365) via a middleware service.The app is built using React and Tailwind CSS embedded directly within a single HTML file for easy deployment via an <iframe>.✨ FeaturesRead-Only Dashboard: Provides a clear, executive summary of key financial metrics (Sales, COGS Food %, BOH Labor %) for each location.External Data Source: Data is fetched directly from a public JSON endpoint, requiring no database setup or client-side authentication.Simple Deployment: Built as a single HTML file (embed.html) ready to be deployed to any web server and embedded via an <iframe>.Visual Variance Tracking: Color-coded metrics (Green/Red) and an "Attention" flag highlight when Actuals significantly exceed Budget targets.🛠️ Setup and ConfigurationThis project consists of only one file, embed.html, which contains all the HTML, CSS (via Tailwind CDN), and React/JSX code.Step 1: Configure the Data Source URLYou must update the DATA_SOURCE_URL variable inside the <script type="text/babel"> block in embed.html.Open embed.html.Locate the following line near the top of the React code:const DATA_SOURCE_URL = "YOUR_PUBLIC_JSON_URL_HERE"; 

Replace the placeholder string with the actual public URL where your R365 automation script deposits the processed report data (e.g., a link to a file on S3 or Google Cloud Storage).Step 2: Automation PrerequisiteThis dashboard requires a working backend process to function correctly:Your R365 integration must be configured to run daily (or hourly).The script must fetch, calculate, and format the required sales, COGS, and labor data for each location.The script must save the final array of report objects as a JSON file to the URL specified in Step 1.Step 3: DeploymentUpload the configured embed.html file to your public web server or hosting platform.Note the public URL of the uploaded file (e.g., https://myreports.com/dashboard/embed.html).🖥️ Usage: Embedding on a WebsiteTo display the dashboard on any webpage (e.g., a SharePoint site, internal company wiki, or main company website), use the following <iframe> tag.Replace [YOUR_PUBLIC_URL_TO_embed.html] with the URL noted in Step 3 of the deployment section.<iframe
  src="[YOUR_PUBLIC_URL_TO_embed.html]" 
  title="Financial Report Dashboard"
  width="100%"
  height="1000px" 
  style="border: none; min-height: 100vh;"
></iframe>

📝 Expected Data StructureThe external JSON file must contain an array of objects, with each object representing a single location report.KeyTypeDescriptionlocationIdstringUnique identifier (e.g., "boathouse_sp")locationNamestringDisplay name (e.g., "The Boathouse at Short Pump")periodstringReporting period (e.g., "09/08/2025-09/28/2025")totalSalesActualnumberActual total sales amount (Currency)totalSalesBudgetnumberBudget total sales amount (Currency)cogsFoodActualnumberActual COGS Food percentage (e.g., 0.277 for 27.7%)cogsFoodBudgetnumberBudget COGS Food percentage (e.g., 0.252 for 25.2%)laborBOHActualnumberActual BOH Labor percentage (e.g., 0.110 for 11.0%)laborBOHBudgetnumberBudget BOH Labor percentage (e.g., 0.119 for 11.9%)Example JSON Payload:[
    {
        "locationId": "boathouse_sp",
        "locationName": "The Boathouse at Short Pump",
        "period": "10/01/2025-10/21/2025",
        "totalSalesActual": 140906,
        "totalSalesBudget": 179790,
        "cogsFoodActual": 0.354,
        "cogsFoodBudget": 0.316,
        "laborBOHActual": 0.162,
        "laborBOHBudget": 0.120
    }
]

📜 LicenseThis project is licensed under the GNU General Public License v3.0. See the official license text for full details.
