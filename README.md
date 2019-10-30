# Security Delivery Tracker
<p><span style="font-size: 24px;"><strong>Purpose</strong></span></p>
<p>This tool was developed for Security Leaders, Managers and/or Practitioners to address the ongoing challenge in tracking and reporting key security metrics within their organization. &nbsp;</p>
<hr>
<p><span style="font-size: 24px;"><strong>Requirements</strong></span></p>
<ul style="list-style-type: square;">
  <li>SDT.ZIP located on my Github 
    <a href="https://github.com/njfanelli/Security-Delivery-Tracker">https://github.com/njfanelli/Security-Delivery-Tracker</a>
  </li>
  <li>Microsoft Excel</li>
  <li>Microsoft PowerBi - 
    <a href="https://powerbi.microsoft.com/en-us/downloads/">https://powerbi.microsoft.com/en-us/downloads/</a>
  </li>
  <li>(<em>Optional</em>) Ability to create a scheduled task to run a VBScript. &nbsp;</li>
  <li>(<em>Optional</em>) Microsoft PowerQuery - 
    <a href="https://www.microsoft.com/en-us/download/details.aspx?id=39379">https://www.microsoft.com/en-us/download/details.aspx?id=39379</a>
  </li>
</ul>
<hr>
<p><strong><span style="font-size: 24px;">Getting Started</span></strong></p>
<ol>
  <li>Download the SDT.ZIP above, this compressed file contains the following files:
    <ul>
      <li><strong>Security Delivery Tracker.xlsx -&nbsp;</strong>This is main file for the solution and is used as a central repository to track changes (i.e. maturity, budget, issues, failures, etc.) to products under your portfolio.</li>
      <li><strong>Security Delivery Legend.xlsx -&nbsp;</strong>This file is only used as a reference and does not link to any of the other files within this package.</li>
      <li><strong>Security Delivery Archive Script.vbs -&nbsp;</strong>This script when executed will create a backup of the “Security Delivery Tracker.xlsx” in to .\Archive directory, the filename will reflect the date at which the script was executed, if you are not comfortable with the script this process could be done manually. &nbsp;NOTE: it is important you do not rename the filenames of the archives there is code with in the “Security Delivery Trend Data.xlsx” document that will take each filename and normalize it to an actual date.</li>
      <li><strong>“Archives” Folder -&nbsp;</strong>Depending on the frequency you define in running the script above will determine the checkpoint intervals of your reporting data. &nbsp;The files within this folder should following the naming format of “YYYY-MM-DD”, if leveraging the script above the file will be named appropriately if you are saving an archive manually, you’ll need to keep this in mind when saving your file (this is explain in more detail below). &nbsp;NOTE: there is one pre-existing entry within the Archives folder, this file is empty but it necessary to make sure the PowerQuery steps execute within the “Security Delivery Trend Data.xlsx” file.&nbsp;</li>
      <li><strong>Security Delivery Trend Data.xlsx -&nbsp;</strong>This file (initially blank) has a preconfigured PowerQuery that will browse to your Archives folder, it will then open each file that is stored within the repository then copy/paste them into this worksheet thus creating a single table with your rolling updates. &nbsp;To execute the PowerQuery steps you may go to either the Data Tab and select “Refresh All” within the ribbon bar OR go to the Query Tab and select “Refresh” within the ribbon bar. &nbsp;NOTE: &nbsp; COLUMN A is now created, the query takes the filename/s within the source path and normalizes them into an actual date that can be used for reporting purposes. &nbsp;Therefore, is it important to follow the filename format for archived files. &nbsp;If you are interested in the steps the query performs you may go to the Query Tab and click on “Edit” within the ribbon bar, a new window will appear then within the right window pane all steps will be listed under “Applied Steps”, you have the ability to select each step from top to bottom to watch the data transform.</li>
      <li><strong>Security Delivery Maturity Levels.xlsx -&nbsp;</strong>This workbook is very simple where it will convert the Maturity Level to an actual Maturity Number value. &nbsp;This file is only referenced the by the Security Delivery Dashboard.pbix file.</li>
      <li><strong>Security Delivery Dashboard.pbix -&nbsp;</strong>Contains a set of dashboards that are populated by reading data from the Security Delivery Trend Data.xlsx workbook. &nbsp;This file can be opened with Microsoft PowerBI (a free version is available) and the dashboards available are:
        <ul style="list-style-type: disc;">
          <li>Solution Summary - This dashboard provides a snapshot of all technologies identified within your environment and summarizes their current status. &nbsp;</li>
          <li>Solution Breakdown - This dashboard allows the user to select and individual technology to view additional details as well as trending patterns for the key metrics we’ve identified within our workbook.</li>
        </ul>
      </li>
      <li><strong>“EXAMPLE” Folder -&nbsp;</strong>This folder contains a pre-populated workbook and dashboard with fictitious data for you to reference. You may safely remove this folder if you wish.</li>
    </ul>
  </li>
  <li>Extract the compress file to the following path: “C:\SDT”. &nbsp;This is the default patch for the tool and can be changed if needed, refer to the FAQs section for more information on this.</li>
  <li>Launch Security Delivery Tracker.xlsx</li>
  <li>Under MASTER worksheet update Product names listed in COLUMN A to reflect your environment. &nbsp;NOTE: You’ll also need to update the respective worksheet tab to reflect the new product name (e.g. if cell A4 is Infinity Gauntlet so should the worksheet tab labeled Solution 1). &nbsp;After you’ve modified COLUMN A and the respected worksheet tab you’ll need to update several calculated cells for each solution. &nbsp;In the MASTER worksheet tab for any product you changed in COLUMN A you will need to update the calculated value identified in COLUMNS E, F, G, H, I, J &amp; L for each product (for instance: &nbsp;If cell A4 = Infinity Gauntlet and Solution 1 worksheet tab was renamed to Infinity Gauntlet you need to modify the calculated formula in E4, F4, G4, H4, I4, J4 &amp; L4), an easy way to accomplish this is:
    <ul>
      <li>On the MASTER worksheet tab highlight the entire row you’d like to change (e.g. row 4 but you’ll need to repeat this step for each solution)</li>
      <li>In the ribbon bar select Find &amp; Select</li>
      <li>In the window that appears click the Replace tab
        <ul style="list-style-type: disc;">
          <li>Find what: Solution 1</li>
          <li>Replace with: &lt;YOUR PRODUCT&gt; &nbsp;note this must match the worksheet tab name</li>
          <li>Within: Sheet</li>
          <li>Search: By Rows</li>
          <li>Look in: Formulas</li>
          <li>Click Find All button</li>
          <li>Verify the items found and if OK click the Replace All button</li>
          <li>Click Close</li>
        </ul>
      </li>
    </ul>
  </li>
  <li>Go to the Dropdown Data worksheet tab
    <ul style="list-style-type: circle;">
      <li>Update any cell as it relates to your environment for COLUMNS B-O. &nbsp;Common items to edit are Solution Focus, Team, Analyst &amp; VAR. &nbsp;These items control many of the drop-down lists that appear throughout the workbook.</li>
    </ul>
  </li>
  <li>The Solution worksheet tab/s (you’ll need to do this for each solution)
    <ul style="list-style-type: circle;">
      <li>Update the Header to reflect the worksheet tab name</li>
      <li>Review/Modify the Maturity Description labels specified for each solution and ensure they are applicable for that product, if not feel free to modify.</li>
    </ul>
  </li>
  <li><em>OPTIONAL</em> - Excel has the ability to Share Workbook, this is located under the Review Tab (note: in the newer version of Office this is now identified as a Legacy feature but is still accessible). &nbsp;When you click on the “Share Workbook” feature a popup will appear, under the Editing tab select the “Use the old shared workbooks feature instead of the new co-authoring experience.” and then click OK</li>
  <li><em>OPTIONAL</em> - Excel has the ability to Track Changes this is located under the Review Tab (note: in the newer version of Office this is now identified as a Legacy feature but is still accessible). &nbsp;Once you click on the “Track Changes” feature a popup will appear, make sure “Track changes while editing. This also shares your workbook.” is selected. &nbsp;As changes are made moving forward return to this popup and I found the specifying the following criteria under the “Highlight which changes” section helpful… &nbsp; When: = ALL, also check box to “List changes on a new sheet”. &nbsp;This will output a rolling list of changes onto a single worksheet for you AND if you go to any of your solution tabs within the Security Delivery Tracker you’ll also notice any field that was modified is now highlighted/outlined indicating a change to the field, if you hover over the field you’ll see details on the change.</li>
  <li>Save Workbook changes</li>
  <li>Start Entering Data!!</li>
</ol>
<hr>
<p><span style="font-size: 24px;"><strong>Reporting</strong></span></p>
<p style="margin-left: 20px;">COMING SOON!!</p>
<hr>
<p><span style="color: rgb(44, 130, 201);"><span style="color: rgb(0, 0, 0); font-family: &quot;Times New Roman&quot;; font-size: 24px; font-style: normal; font-variant-ligatures: normal; font-variant-caps: normal; font-weight: 400; letter-spacing: normal; orphans: 2; text-align: left; text-indent: 0px; text-transform: none; white-space: normal; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px; text-decoration-style: initial; text-decoration-color: initial; float: none; display: inline !important;"><strong>Frequently Asked Questions</strong></span><span style="font-size: 24px;"><strong>&nbsp;</strong></span></span></p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(44, 130, 201);">QUESTION</span>:</strong>&nbsp; How do I change the default path of the tool from “C:\SDT” to something else?</p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(209, 72, 65);">ANSWER</span>:</strong>&nbsp; Once the files have been extracted and saved in the desired path, you’ll need to open each of the following documents and update the dependent links/connections (Note: this is where Power Query for Excel comes in):</p>
<ul>
  <li style="margin-left: 20px;">Browse and launch the “Security Delivery Trend Data.xlsx”
    <ol>
      <li style="margin-left: 40px;">Click Query Tab</li>
      <li style="margin-left: 40px;">Click Edit in the ribbon bar</li>
      <li style="margin-left: 40px;">Click OK to the security notice (if prompted)</li>
      <li style="margin-left: 40px;">In the right window pane labeled Query Setting under Applied Steps “Source” is listed as the first step, click the cog wheel to the right of it</li>
      <li style="margin-left: 40px;">Under folder path enter the new location for your “Archives” folder</li>
      <li style="margin-left: 40px;">Click OK</li>
      <li style="margin-left: 40px;">Click Close &amp; Load in the ribbon bar</li>
      <li style="margin-left: 40px;">Save and Close the file</li>
    </ol>
  </li>
  <li>Right click the “Security Delivery Archive Script.vbs” file and select Edit (if prompted with a security warning click Open)
    <ol>
      <li style="margin-left: 40px;">Row 8 update the strSource to the new location to your Security Delivery Tracker.xlsx file</li>
      <li style="margin-left: 40px;">Row 11 update the strDest to the new location of your Archives folder</li>
      <li style="margin-left: 40px;">Save and Close the file</li>
    </ol>
  </li>
  <li>Launch the “Security Delivery Tracker Dashboard.pbix” file
    <ol>
      <li style="margin-left: 40px;">Under the Home Tab click the “Edit Queries” option within the ribbon bar then select “Data Source Settings”</li>
      <li style="margin-left: 40px;">Highlight “c:\sdt\security delivery maturity levels.xlsx” and then select “Change Source…”</li>
      <li style="margin-left: 40px;">Under file path update the location to your respective file</li>
      <li style="margin-left: 40px;">Click OK</li>
      <li style="margin-left: 40px;">Highlight “c:\sdt\security delivery trend data.xlsx” and then select “Change Source…”</li>
      <li style="margin-left: 40px;">Under file path update the location to your respective file</li>
      <li style="margin-left: 40px;">Click OK</li>
      <li style="margin-left: 40px;">Click Close</li>
      <li style="margin-left: 40px;">Save and close file</li>
    </ol>
  </li>
</ul>
<p style="margin-left: 20px;"><strong><span style="color: rgb(44, 130, 201);">QUESTION</span>:</strong>&nbsp; I would like the Security Delivery Tracker.xlsx file to be accessed modified by multiple users at one time, how do I do this?</p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(209, 72, 65);">ANSWER</span>:</strong>&nbsp; Excel has the ability to Share Workbook, this is located under the Review Tab (note: in the newer version of Office this is now identified as a Legacy feature but is still accessible). &nbsp;When you click on the “Share Workbook” feature a popup will appear, under the Editing tab select the “Use the old shared workbooks feature instead of the new co-authoring experience.” and then click OK</p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(44, 130, 201);">QUESTION</span>:</strong>&nbsp; Is there a way to track changes to the Security Delivery Tracker.xlsx workbook so I have a rolling record of what changed and by whom?</p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(209, 72, 65);">ANSWER</span>:</strong>&nbsp; Absolutely. &nbsp;Excel has the ability to Track Changes this is located under the Review Tab (note: in the newer version of Office this is now identified as a Legacy feature but is still accessible). &nbsp;Once you click on the “Track Changes” feature a popup will appear, make sure “Track changes while editing. This also shares your workbook.” is selected. &nbsp;As changes are made moving forward return to this popup and I found the specifying the following criteria under the “Highlight which changes” section helpful… &nbsp;When: = ALL, also check box to “List changes on a new sheet”. &nbsp;This will output a rolling list of changes onto a single worksheet for you AND if you go to any of your solution tabs within the Security Delivery Tracker you’ll also notice any field that was modified is now highlighted/outlined indicating a change to the field, if you hover over the field you’ll see details on the change.</p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(44, 130, 201);">QUESTION</span>:</strong>&nbsp; The dashboards within my Security Delivery Tracker Dashboard.pbix file are not displaying data?</p>
<p style="margin-left: 20px;"><strong><span style="color: rgb(209, 72, 65);">ANSWER</span>:</strong>&nbsp; Follow these steps to troubleshoot: &nbsp;1) Ensure there is data present within your Security Delivery Trend Data.xlsx workbook. &nbsp;2) If you changed the default path for the SDT tool please confirm the data sources you’re pointing to within the Security Delivery Tracker Dashboard.pbix file are accurate, you can do this by selecting the Home Tab then within the ribbon bar selecting “Edit Queries” followed by clicking “Data source setting”.</p>
