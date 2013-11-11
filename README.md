UrlTracker
==========


The Url Tracker is used to manage URLs within umbraco. It automatically tracks URL changes, for instance when a node is renamed, and makes sure the old URL will redirect to the new location. This is great for SEO and great for people visiting your website via this old URL. Search engines will update the indexed URL and people won't visit the old, broken URL.<br />
You can also create your own redirects, based on a simple URL or using a Regex pattern. You can redirect to an existing node or a manually entered URL. This is great for migrating existing indexed URLs to your new website!

## Features ##
*   Keeps track of **URL changes** (node gets renamed, moved or the umbracoUrlName property changes)
*   Keeps track of **not found (404)** requests, so you can easily create redirects for them
*   Keeps track of **removed content** and responds with **410 Gone** when one requests it
*   **Redirects requests** for old URLs to their new location
*   **Create** your own URL redirects, based on a simple URL or a **Regex** pattern. You can redirect to an **existing node** or a manually entered URL.
*   Create **permanent (301)** or **temporary (302)** redirects
*   Supports all extensions, including **.php** and **.html**
*   Supports all kinds of **query string** options, like matching a query string and pass through the request query string
*   Supports **multiple websites** in a single umbraco instance

## Changelog ##
*   2.2.8 [2013/11/11]
	* [Bugfix] Improved the 'rootnode is 0' bugfix from 2.2.7
	* [Bugfix] An issue was introduced in version 2.2.6 for 'older' umbraco versions
	* [Improvement] UI handles unpublished nodes better
*   2.2.7 [2013/11/08]
	* [Bugfix] Fixed a UI issue when the rootnode is 0
	* [Improvement] Better 404 handling; ignores referrer if it's value is the Url Tracker UI, ignores 404 entry if the URL is a BrowserLink URL (VS 2013)
*	2.2.6 [2013/10/21]
	* [Bugfix] There were some issues with umbraco 6.1.x and static file extensions (like .html)
*	2.2.5 [2013/10/16]
	* [Bugfix] There was an issue with multiple entries with the same old url, but different querystrings
	* [Bugfix] When multiple versions of log4net exist in the bin folder, the UrlTracker would crash
*	2.2.3 [2013/08/30]
	* [Bugfix] Sometimes the installer was stuck at "Installing database table" (VirtualPathProvider issue)
*	2.2.2 [2013/08/23]
	*	[Feature] Added regex capturing groups support (use '$n', where n is the capturing group number starting from 1)
	*	[Feature] Added response from HttpModule if it 'fails' in the installer (debugging purposes)
*	2.2.0 [2013/08/22]
	*	[Feature] Added filtering and searching
	*	[Feature] Improved error handling
*	2.1.6 [2013/08/16]
	*	[Bugfix] Fixed two small bugs (http module)
*   2.1.4  [2013/08/07]
	*	[Bugfix] Migrating data from v1 to v2 resulted in an error when there were absolute OldUrls in the DB table
*   2.1.3  [2013/08/05]
	*	[Bugfix] Redirects from URLs with non-aspx extensions were displayed with '.aspx' appended at the end
	*	[Bugfix] Redirects with querystring passthrough failed sometimes
*   2.1.1 [2013/07/03] 
	*   [Bugfix] Implemented an extra check for the installation of the dashboard
*   2.1.0 [2013/07/02] 
	*   [Feature] Implemented support for SQL CE
	*   [Feature] Added a setting to disable url tracking (urlTracker:trackingDisabled)
*   2.0.4-beta [2013/07/02] 
	*   [Feature] Added better exception handling for the installer
*   2.0.3-beta [2013/06/21] 
	*   [Bugfix] Enabling logging on umbraco versions including log4net threw ysod
*   2.0.2-beta [2013/06/20] 
	*   [Bugfix] Ports other than 80 didn't work with the Http Module check in the installer
	*   [Bugfix] String.Format in UrlTrackerDomain.UrlWithDomain was wrongly formatted
*   2.0.1-beta [2013/06/20] 
	*   [Bugfix] Multiple hostnames assigned to a node threw an exception
*   2.0-beta [2013/06/19] 
	*   Initial release, completely rebuilt the package
	*   Renamed 301 URL Tracker to Url Tracker
	*   The package is now a single assembly

## Roadmap ##
*   Datatype
*   Better validation (already existing etc.)
*   Support UrlRewriting if possible
*   Azure support (if it doesn't work yet, untested)

## Upgrading from v1 (301 URL Tracker) ##
1.   Back-up the existing infocaster301 database table (schema **and** data)
2.   Uninstall the old package
3.   When the database table is removed, restore it by using the script from step 1
4.   Install version 2; the Url Tracker
5.   The installation wizard will be able to migrate the existing data
6.   If the migration succeeded, you can delete the old infocaster301 database

## Upgrading from v2 ##
1.   Optional: Uninstall the old package (no data will be lost, just to keep the 'Installed packages' clean)
2.   Install the new package

## Uninstalling ##
You can uninstall the Url Tracker by removing the package. The database table will not get deleted! If you'd like to remove the database table too, you should do it manually.

## Tested with ##
*   IIS 7 and up
*   SQL Server 2008 R2
*   .NET 4 and up
*   Umbraco versions 4.6.1, 4.7.2, 4.9.1, 4.11.9, 6.0.0, 6.1.1 **(won't work with pre v4.6.0)**, so it should work with umbraco v4.6.0 and above

## Credits ##
*   **InfoCaster** | Being able to combine 'work' with package development and thanks to colleagues for inspiration.
*   **Richard Soeteman** | Richard came up with the idea for a package which keeps track of URLs of umbraco nodes.
*   **The uComponents project** | For inspiring me to create a single-assembly package solution.