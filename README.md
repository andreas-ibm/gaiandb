# GaianDB
A light-weight data-federation technology built on Apache Derby. Gaian accesses and transforms data securely "at the edge" and can discover other instances of itself to form a scalable data network.

<HTML>

<BODY>

<h1 class="title">Readme.html taken from build/GAIANDB_V2.1.8_20160523.zip</h1>
<h4 class="nocount">Images are not available here - To view them please download and unzip the most recent zip file 
from gaiandb/build/</h4>

<br/>

<hr><h2 class="nocount">Contents</h2>
<ol class="nest">
<li class="nest"><a href="#contents8">What is the Gaian Database ?</a></li><br/>
<li class="nest"><a href="#contents10">Key benefits - what does Gaian give you ?</a></li><br/>
<li class="nest"><a href="#contents12">What's new in version 2</a></li><br/>
<li class="nest"><a href="#contents160">Installation and First Steps</a>
	<ol class="nest">
	<li class="nest"><a href="#contents162">Upgrading Gaian</a></li>
	<li class="nest"><a href="#contents165">Installation Prerequisites</a></li>
	<li class="nest"><a href="#contents337">Supported Operating Systems</a></li>
	<li class="nest"><a href="#contents168">First Steps</a></li>
	<li class="nest"><a href="#contents169">Verify the installation</a></li>
	<li class="nest"><a href="#contents52">Quick table federation examples (matching a Logical Table to a Physical One)</a>
		<ol class="nest">
		<li class="nest"><a href="#contents53">Federate an RDBMS table</a></li>
		<li class="nest"><a href="#contents60">Federate an existing CSV File</a></li>
		<li class="nest"><a href="#contents201">Federate an existing Excel spreadsheet</a></li>
		</ol>
	</li>
	<li class="nest"><a href="WorkedExamples.html">Further worked examples</a></li>
	</ol>
</li><br/>
<li class="nest"><a href="#contents110">GaianDB Usage</a>
	<ol class="nest">
	<li class="nest"><a href="#contents115">GaianDB node usage</a></li>
	<li class="nest"><a href="#contents120">Launching multiple GaianDB nodes</a></li>
	<li class="nest"><a href="#contents127">Launching a GaianDB node from a separate directory</a></li>
	<li class="nest"><a href="#contents130">How to specify a location for configuration and log files and the physical database folder</a></li>
	<li class="nest"><a href="#contents137">How to manage multiple GaianDB node executions with multiple working directories</a></li>
	<li class="nest"><a href="#contents138">How to initialise a GaianDB node with User defined Derby objects like Tables, views, procedures,functions</a></li>
	<li class="nest"><a href="#contents139">How to integrate GaianDB into a wrapping class or framework: startup, start detection, kill</a></li>
	</ol>
</li><br/>
<li class="nest"><a href="#contents339">Client Usage</a>
	<ol class="nest">
	<li class="nest"><a href="#contents140">Command line processor options with 'queryDerby'</a></li>
	<li class="nest"><a href="#contents145">Issuing Distributed SQL Queries</a></li>
	<li class="nest"><a href="#contents341">Distributed Sub-queries or Pushing query processing to each node</a></li>
	<li class="nest"><a href="#contents217">Listing server warnings</a></li>
	<li class="nest"><a href="#contents344">Dashboard Graphical User Interface</a></li>
	</ol>
</li><br/>
<li class="nest"><a href="#contents175">Configuration</a>
	<ol class="nest">
	<li class="nest"><a href="#contents343">Using the Configuration File</a>
		<ol class="nest">
		<li class="nest"><a href="#contents180">Configuration file: Properties for Logical Tables, their Data Sources and associated Connections</a></li>
		<li class="nest"><a href="#contents209">Configuration file: Global System properties and identifiers</a></li>
		</ol>
	</li>
	<li class="nest"><a href="#contents177">Using the management API to apply configuration updates</a></li>
	<li class="nest"><a href="#contents67">Pluralized data sources</a></li>
	<li class="nest"><a href="#contents66">In-Memory tables and indexes on their columns</a></li>
	<li class="nest"><a href="#contents92">Constant Column definitions</a></li>
	<li class="nest"><a href="#contents64">Using the LISTQUERIES and CANCELQUERY procedures as well as the GDB_TIMEOUT and GDB_WID features</a></li>
	<li class="nest"><a href="#contents65">Connection maintenance configuration in intermittent/high latency/low bandwidth networks</a></li>
	<li class="nest"><a href="#contents215">Hard-wiring connections between GaianDB nodes (incl setting up gateways)</a></li>
	<li class="nest"><a href="#contents99">Text file federation configuration options (e.g: how to specify different record and field separators)</a></li>
	</ol>
</li><br/>
<li class="nest"><a href="#contents306">Security</a>
	<ol class="nest">
	<li class="nest"><a href="#contents307">Communication encryption using SSL (Secure Sockets Layer)</a>
		<ol class="nest">
		<li class="nest"><a href="#contents3071">Server Configuration for SSL</a></li>
		<li class="nest"><a href="#contents3072">Client Setup for SSL</a></li>
		</ol>
	</li>
	<li class="nest"><a href="#contents308">User authentication</a></li>
	<li class="nest"><a href="#contents309">User access restriction to chosen databases</a></li>
	<li class="nest"><a href="#contents310">Password scrambling</a></li>
	</ol>
</li><br/>
<li class="nest"><a href="#contents315">Advanced Features</a>
	<ol class="nest">
	<li class="nest"><a href="#contents321">Special SQL Query Options (with_provenance, explain, maxDepth, ...)</a></li>
	<li class="nest"><a href="#contents234">Provenance Columns: Special columns identifying origin of data rows</a></li>
	<li class="nest"><a href="#contents270">Explain Queries: Getting and showing the route of a query</a></li>
	<li class="nest"><a href="#contents273">Specifying advanced table and column mappings</a></li>
	<li class="nest"><a href="#contents274">SQL Query as a Logical Table Data Source</a></li>
	<li class="nest"><a href="#contents275">Message Storer: Message Broker Integration (e.g. use with sensors)</a></li>
	<li class="nest"><a href="#contents401">Custom VTIs</a>
		<ol class="nest">
		<li class="nest"><a href="#contents402">IBM Content Analytics Restful Interface (ICAREST)</a></li>
		<li class="nest"><a href="#contents403">Spatial Query</a></li>
		</ol>
	</li>
	</ol>
</li><br/>
<li class="nest"><a href="#contents325">Supported RDBMS Data sources</a></li><br/>
<li class="nest"><a href="#contents330">Supported SQL Types for Logical Tables Definitions</a></li><br/>
<li class="nest"><a href="#contents335">Supported Number of Logical Tables</a></li><br/>
<li class="nest"><a href="#contents346">Error Messages</a></li><br/>
<li class="nest"><a href="#contents359">FAQ & Troubleshooting</a></li><br/>
<li class="nest"><a href="#contents121">Features</a></li><br/>
<li class="nest"><a href="#contents400">Authors/Contacts</a></li>

</ol>


<hr><h2><a name="contents8">What is the Gaian Database ?</a></h2>

<p>The Gaian Database - or GaianDB for short - is a lightweight (&lt;4MB) dynamically distributed federated database (DDFD) engine based on Apache Derby 10.x. It provides a single centralized view over multiple, heterogeneous back-end data sources (e.g. RDBMS dbs, files, text indexes, spreadsheets, etc.) using an extensible logical table abstraction layer. However, its principal feature is its ability to automatically discover and federate other GaianDB instances (federating nodes) such that a whole network of these can be automatically formed.</p>
<br/>
<center>
<TABLE class='image'>
   <TR class='image'>
     <TD class='image'><a Href="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/gaiandb3.gif">
          <img src="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/gaiandb3.gif" width=500>
	  </a></TD>
     <TD class='image'><a Href="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/gaiandb1.gif">
          <img src="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/gaiandb1.gif"></a></TD>
	  </TR>
   <TR class='image'>
     <TD  class='image' align='center'>Fig. 1 - GaianDB high level architecture</TD>
     <TD  class='image' align='center'>Fig. 2 - GaianDB connectivity model</TD>
    </TR>
</TABLE>
</center>

<p>GaianDB advocates a flexible 'store locally, query anywhere' (SLQA) paradigm, which means the data remains where it is, but you have a centralized view over which you can query. Each data source should have its data managed autonomously and applications can choose which sections of it to make available to the GaianDB network. For this reason distributed insert/update/delete operations are not currently supported.</p>
<p>Queries can be injected at any node and are routed effectively around the network using a 'biologically inspired' connectivity model that strives to minimise query time and maximise efficiency (by minimising network diameter and maximising connections to the fittest nodes).</p>
<p>Architecturally, GaianDB sits <b>underneath</b> Derby, and is invoked by Derby to process any GaianDB-specific SQL. To query GaianDB you typically identify the 'GaianTable' class (which references a logical table, similar to a view definition), or the 'GaianQuery' class (which references an embedded subquery), either of which will retrieve federated data from every GaianDB node in a connected network. Other GaianDB SQL usage may be invocations of one of the stored procedures or functions that make up GaianDB's system management API. These can be used to define Logical Tables and their federated Data Sources, relational database connections, user-defined Gaian Connections (for nodes that couldn't be discovered), or any of GaianDB's general system properties individually.</p>
<br />
<p>The distributed, federated and store-local nature of GaianDB makes it extremely scalable and suitable for a wide variety of deployments and scenarios. Also, GaianDB is 100% Java and so it can run in a multitude of places; anywhere from small devices, like mobile phones, to large enterprise systems; easily integrating between all of these.</p>
<p>GaianDB has already been used in the context of complex text analytics applications, performing distributed semantic join queries, and drawn the attention of significant customers in the military space.</p>
<p>As a DDFD technology, its positioning is shown below:</p>

<br/>
<center>
<TABLE class='image'>
   <TR class='image'>
     <TD class='image'><a Href="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/gaiandb5.gif"><img src="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/gaiandb5.gif" ></a></TD>
     </TR>
   <TR class='image'>
     <TD class='image' align='center'>Fig. 3 - GaianDB positioning</TD>
     </TR>
</TABLE>
</center>

<br/>
<p>GaianDB also offers a wide range of other features such as: Dynamic re-configuration; an 'Explain' network-route query option; In-Memory tables and indexing; Message Broker integration; contextual meta-data.</p>
<p>For more information on GaianDB, take a look at this recently (2008) published paper:
<a href="http://www.usukita.org/files/Page238.pdf">A Dynamic Distributed Federated Database</a></p>

<br/>

<hr><h2><a name="contents10">Key benefits - what does Gaian give you ?</a></h2>
<br/>
Gaian federation technology provides a "data virtualisation" layer - with many beneficial aspects:
<p/>

<ol>
<li>Reduced Maintenance</li>
<ul>
	<li>Using simplified abstract data model as opposed to full physical data model for each back-end</li>
	<li>Views do not need to be created in back-end databases</li>
	<li>Data sets from separate providers can be joined with SQL + configuration only (no need for code)</li>
	<li>Many types of data-sources are supported out-of-the-box (including RDBMS tables, structured text files or XL spreadsheets)</li>
	<li>Other data-sources can be exposed via a Gaian Java plugin interface wrapper.</li>
	<li>Simplified model for Migrating/swapping underlying data-sources - only requires configuration updates.</li>
</ul>
<li>In-line SQL transformation of data records</li>
<ul>
	<li>Ad-hoc simple data cleansing</li>
	<li>Data matching</li>
</ul>
<li>Real-time data</li>
<ul>
	<li>Gaian provides access to current endpoint data - as opposed to "old" data exported by data owner.</li>
</ul>
<li>Data Ownership</li>
<ul>
	<li>Gaian nodes can be attributed to each data owner.</li>
	<li>Data owners provide/deny access to their data as they wish - Graphical/intuitive tools for this are in development.</li>
	<li>Intermediary data stores for published data are no longer required.</li>
</ul>
<li>Distributed Access + Scalability</li>
<ul>
	<li>A plurality of interconnected Gaian nodes provides the ability to connect and query through any node.</li>
	<li>Nodes can be configured differently to allow access to more or less data structures.</li>
	<li>Gaian networks can provide scalability by attributing distinct data set partitions to different Gaian instances.</li>
</ul>
<li>Distributed Processing</li>
<ul>
	<li>Distributed queries can result in parallel processing, e.g. invoking procedure calls (can also be used to implement map/reduce).</li>
	<li>Processing functions can be deployed dynamically (in a JAR file). Gaian does not need restarting.</li>
</ul>
<li>Provenance</li>
<ul>
	<li>Gaian provides provenance information for every data record.</li>
	<li>This facilitates development of Governance aspects which can also be applied at the Gaian layer.</li>
</ul>
<li>Policy</li>
<ul>
	<li>Access rules can be implemented to cover access to all data providers (incl. files etc) in one place.</li>
	<li>Policy functions can be deployed dynamically (in a JAR file). Gaian does not need to be restarted.</li>
</ul>
<li>Caching</li>
<ul>
	<li>Gaian can act as a cache location for pre-processed results, faster access, etc</li>
	<li>Gaian can also host surrogate key tables for linking different datasets together (e.g. same locations expressed in different languages)</li>
</ul>
</ol>

<br/>

<hr><h2><a name="contents12">What's new in version 2</a></h2>
<UL>
	<li>New features</li>
	<ul>
    <li>Updated Derby pre-req to version 10.8.3.1.1505077</li>
    <li>Query timeout and cancellation capabilities</li>
    <li>Support for batched record filtering for access to high-latency authentication systems.</li>
    <li>Extended ICAREST + SpatialQuery VTIs such that they call out to the policy plugin to enforce required filtering.</li>
    <li>New TRANSIENT option ** Deprecated in favour of PLURALIZED ** allows in-memory data sources definitions, thus speeding up their registration and avoiding having to remove them on start-up.</li>
    <li>Improved capability to integrate Gaian in a wrapping JVM process (e.g. OSGi framework) - with start detection, termination handling and workspace configuration.</li>
    <li>Allowed sub-queries to include stored procedure calls and CRUD operations.</li>
    <li>New capability to target sub-queries at specific nodes.</li>
    <li>Added expiry capability to INMEMORY caching option.</li>
    <li>Improved core capability to distinguish ordinary from delimited identifiers; and eliminated need for column naming in sub-queries.</li>
    <li>Added capability to connect and authenticate using a separate user database or schema whilst retaining access to all GaianDB logical tables and procedures/functions.</li>
    <li>New query path visualisation in dashboard - ability to discover loaded logical tables and paths to them.</li>
    <li>Pluralized data sources for accessing multiple data source end-points through a single Gaian data source wrapper - e.g. a set of files in a folder.</li>
    <li>Policy framework improvements: Now passes cluster ID and session user ID to allow more control over user and query access.</li>
    <li>New API batch update capability with procedure: setconfigproperties().</li>
    <li>Capability to restrict user access to designated derby databases, see shipped derby.properties.</li>
    <li>Auto-resoltuion of schemas and column-mappings for custom VTIs</li>
    <li>Generic pooling of all data source wrappers - now includes custom VTIs</li>
	</ul>
	<li>Bug fixes</li>
	<ul>
    <li>Fixed and improved reliability of Excel data source wrapper</li>
    <li>Improved persisted caching behaviour when handling expensive join queries</li>
    <li>Simplified logical table reload when nodes connect or disconnect</li>
    <li>Improved policy plugin framework to allow GaianDB to call out to the plugin at any stage in the query life cycle in future.</li>
    <li>Reduced GaianNode startup time and improved reliability of refresh of logical table views and stored procedures.</li>
    <li>Fixed propagation of query meta-data information (such as user credentials) so it is only sent with GaianDB queries and can now reach endpoint data sources via sub-queries.</li>
    <li>Improved robustness of discovery capability and fixed local discovery for MAC OS X.</li>
    <li>Made policy framework generically extensible without impacting on backwards compatibility in future.</li>
    <li>Fixed/improved resilience to concurrent configuration updates, reducing risk of corruption to the configuration file.</li>
    <li>Improved reliability and cross-platform capability of start-up and kill scripts.</li>
    <li>Fixed intermittent hang and deadlock issues.</li>
    <li>Increased size of all VARCHAR input parameters of APIs to maximum size 32672 chars.</li>
    <li>Improved resolution of file paths on Windows for structured text file data sources.</li>
    <li>Fixed OutOfMemoryError related to long running queries - by ignoring hanging suspects which are not inter-node connections (as these cannot be polled anyway), clearing executing data sources after a query. Also added logging for memory reporting.</li>
    <li>Fixed intermittent GaianDB inter-node connection hiccups during discovery</li>
    <li>Fixed run status when the main GaianNode thread completes such that it can subsequently be re-started</li>
    <li>Fixed inconsistent state after a REMOVELT() causing issues with subsequent SETDSXXX().</li>
    <li>Fixed GaianNode shutdown() to complete despite issues, removing use of Thread.isAlive(), and only when Derby has shut down - thus allowing a clean restart.</li>
    <li>Removed use of System.gc() calls when releasing cached rows for JOINs.</li>
    <li>Fixed logical table table creation issues with full synchronization of SETXXX() API calls.</li>
    <li>Performance improvement with logical table API updates by avoiding checks on unaffected tables.</li>
    <li>Resolved issues with IS [NOT] NULL construct against Gaian VTIs and Table Functions.</li>
    <li>Fixed issue whereby a data source pointing to an RDBMS table expression would not load after being changed (throwing a StringIndexOutOfBoundsException).</li>
    <li>Improved resilience to issues with logical table view reloads such that subsequent view reloads are not impacted.</li>
    <li>Fixed condition whereby GaianDB at rest having Oracle data source consumes its cursors until failure.</li>
    <li>Cleaner error reporting when GAIANDB.jar cannot be found on startup.</li>
    <li>Changed condition for DROP statements which raised silent derby.log ERRORs, e.g. at startup.</li>
    <li>Fixed issue with CACHE tables used for JOIN processing when an logical table definition contains a LONGVARCHAR, by normalising types to Derby syntax.</li>
    <li>Avoid Gaian hang when connection to a peer node is abruptly lost, e.g. termination of a peer node's VM</li>
    <li>Allow special characters in column names</li>    
	</ul>
	<li>Prototyped - coming soon:</li>
	<ul>
    <li>UDP Driver for inter-node connectivity over UDP</li>
    <li>'Lite' Driver to run independantly from Derby (with limited SQL capability)</li>
    <li>Client node discovery capability to allow load balancing, e.g. from WAS</li>
    <li>New deployment capability to IBM Bluemix cloud</li>
    <li>Generic access to web services</li>
    <li>MongoDB VTI</li>
    <li>Accumulo VTI</li>
	</ul>
</UL>
<br/>

<hr><h3><a name="contents20">Version 2.1.4</a></h3>
<UL>
	<li>New features</li>
	<ul>
    <li>Dynamic class-loading of newly deployed JAR libraries containing JDBC drivers, policy code, and data source connectors (VTIs).</li>
    <li>Policy framework improvements: Now receives full-sub-query for pass-through queries, and ResultSetMetaData is supplemented with table names of queried columns.</li>
    <li>New capability to enable Derby's SSL encryption for client-server and inter-node connections.</li>
    <li>New procedure RUNSQL() to run SQL directly against any specified connection ID or JDBC properties specified directly.</li>
    <li>New capability to specify &lt;GAIAN_WORKSPACE&gt; tag in _ARGS property of a Text file DS.</li>
    <li>New procedures LISTTHREADS() to list Gaian's JVM threads; and LISTENV() to list Gaian's system environment properties.</li>
	</ul>
	<li>Bug fixes</li>
	<ul>
	<li>Fixed condition leading to a Derby NullPointerException occurring with 4-way (or higher complexity) self-joins.</li>
    <li>Fixed queryDerby behaviour (e.g. with delimiters, comments) to be consistent across all modes: file, query-list, interactive</li>
    <li>Fixed lookup of control files for structured text file data sources (e.g. CSV)</li>
    <li>RDBMS types normalisation for Oracle data types - particularly INTERVAL type and TIMESTAMP types involving a TIME ZONE.</li>
    <li>Resolved OutOfMemoryError occurring from accumulated stale objects after repeated runs of a query.</li>	
	</ul>
	<li>Prototyping in progress - coming soon:</li>
	<ul>
	<li>Windows Service for Gaian - with documentation for registry changes required</li>
    <li>GaianServlet for deploying Gaian as a webapp</li>
    <li>Gaian in Bluemix</li>
    <li>GenericWS connector hardening for access to a web service as a data source</li>
	</ul>
</UL>
<br/>



<hr><h2><a name="contents160">Installation and First Steps</a></h2>

<hr><h3><a name="contents162">Upgrade Gaian</a></h3>
<p>If you are already using GaianDB, and want to upgrade please refer to the <a href="UpgradeGaian.html">upgrade instructions</a>.</p>

<hr><h3><a name="contents165">Installation Prerequisites</a></h3>
<ul>
	<li>Java JRE version: IBM JRE 1.7.0 or above. (Oracle JRE 1.7.0 should work; GNU versions of Java have caused problems). Make sure that the 'java' executable is in your PATH.</li>
	<br />
	<li>Any RDBMS JDBC drivers required to connect to and federate your Relational Database tables. These will often
	be included in the installation package for the RDBMS.
	<br>To make a new JDBC driver available to GaianDB, add the JAR file that contains the driver class to the Java CLASSPATH
	variable before starting GaianDB (for convenience, the Java CLASSPATH is defined in 'launchGaianServer' batch and script files).<br>
	<p>GaianDB only supports the official JDBC drivers provided by the Relational Database providers listed below:</p>

	<table class='data'>
			<thead>
			<tr>
				<th width="101" height="30"><b>Name</b></th>
				<th height="30" width="169"><b>Jar file(s)</b></th>
				<th height="30" width="314"><b>JDBC driver class</b></th>
				<th height="30" width="429"><b>URL connection template</b></th>
			</tr>
			</thead>
		<tbody>
			<tr>
				<th height="43" width="101">DB2</th>				
				<td height="43" width="169">db2jcc.jar, db2jcc_licence_cu.jar</td>
				<td height="43" width="314">com.ibm.db2.jcc.DB2Driver</td>
				<td height="43" width="429">jdbc:db2://&lt;server&gt;:&lt;port50000&gt;/&lt;database&gt;</td>
			</tr>
			<tr class='odd'>
				<th width="101" height="43">SQLServer</th>
				<td width="169" height="43">sqljdbc4.jar</td>
				<td width="314" height="43">com.microsoft.sqlserver.jdbc.SQLServerDriver</td>
				<td width="429" height="43">jdbc:sqlserver://&lt;server&gt;:&lt;port1433&gt;;DatabaseName=&lt;database&gt;</td>
			</tr>
			<tr>
				<th width="101" height="43">MySQL</th>
				<td width="240" height="43">mysql-connector-java-5.1.7-bin.jar</td>
				<td width="314" height="43">com.mysql.jdbc.Driver</td>
				<td width="429" height="43">jdbc:mysql://&lt;server&gt;:&lt;port3306&gt;/&lt;database&gt;</td>
			</tr>
			<tr class='odd'>
				<th width="101" height="43">Oracle</th>
				<td width="169" height="43">ojdbc14.jar or ojdbc6.jar</td>
				<td width="314" height="43">oracle.jdbc.OracleDriver</td>
				<td width="429" height="43">jdbc:oracle:thin:@&lt;server&gt;:&lt;port3306&gt;/&lt;database&gt;</td>
			</tr>
		</tbody>
	</table>
	</li>
	<li><p>Knowledge of SQL. All SQL conventions that apply to Apache Derby apply to the IBM Gaian Database. See <a href="http://db.apache.org/derby/docs/10.5/ref/">Apache Derby's Reference Manual</a> for more information.</li>
</ul>
<br/>

<hr><h3><a name="contents337">Supported Operating Systems</a></h3>
<p>GaianDB has primarily been tested on RHEL, Ubuntu, Windows and MAC OS X. The documentation uses the term 'Unix' to refer to Linux and MAC OS X. 
   GaianDB should work on other Unix systems (AIX, HP-UX, Solaris, etc ..) and was demonstrated running on many virtualization engines (VMWare,KVM,Xen) and Cloud software (IBM SmartCloud Provisioning (SCP), Amazon EC2, OpenStack), but no testing has been done.</p>
<p>Windows and Unix scripts are provided in the installation for starting a GaianDB server ('launchGaianServer.bat' &amp; 'launchGaianServer.sh') and running the Command Line Processor ('queryDerby.bat' &amp; 'queryDerby.sh').</p>

<p><b>Note:</b> All paths, whether on Windows or Unix, should use forward slashes (/) and not backslashes (\).</p>
<p>When launching a GaianDB node, the system must be able to resolve its own hostname to an IP address. You can check this by:</p>
<ul>
	<li>You can find out what the server's hostname is by running the
	'hostname' command in a command prompt.</li>
	<li>Test whether the system can resolve its own IP address using
	the 'ping &lt;hostname&gt;' command (valid for Unix and Windows).</li>
</ul>
<p>If it cannot:</p>
<ul>
<li>Check whether your firewall is blocking the requests. For more information on configuring firewalls for use with GaianDB, please refer to the <a href="#contents359">FAQ & Troubleshooting</a> section. </li>
<li>Check your network settings:
<ul>
	<li>For Windows systems:
		<ul>
			<li>Check your
	network connection's IP configuration properties (Control Panel->Network Connections->Select a connection->
	right click, Properties->Internet protocol). </li>
		</ul>
	</li>
    <li>For Unix systems:
		<ul>
			<li>Check that the file /etc/hosts has a line (otherwise add one)
			in the format: &lt;ipaddress&gt; &lt; hostname&gt;
			&lt;hostname.domain&gt;</li>
		</ul>
	</li>
	  <li>For virtualization software and systems:
		<ul>
			<li>Check that the network layer exposes the proper IP addresses and allows the IP and UDP traffic through as described above. 
			    You may be required to use NAT instead of BRIDGE for instance. </li>
		</ul>
	</li>
</ul>
</li>
</ul>

<hr><h3><a name="contents168">First Steps</a></h3>
<p><b>Install Gaian</b></p>
<p>To 'install' GaianDB, simply unzip the zip install file to a directory of your choice. (For instance 'C:\GaianDB' on Windows or '/home/myuser/GaianDB' on Unix)</p>
<p><b>Launch a GaianDB Node</b></p>
<p>You are now ready to launch a GaianDB node. To do so,  run 'launchGaianServer.bat' on Windows or './launchGaianServer.sh' on Unix.</p>
<p>By default, the GaianDB node will start a Derby server listening on port 6414 and use the properties file 'gaiandb_config.properties' in the local directory.</p>
<p><b>Examine the default configuration</b></p>
<ul>
<li>
To see the default startup settings for a GaianDB node, take a look at the USAGE statement. You can see this by running the launch scripts and passing in any unrecognised argument, e.g: '-?' , '-help' or '-usage'. For example, from a command prompt, by running 'launchGaianServer.bat -help' on Windows or './launchGaianServer.sh -help' on Unix.  
</li>
<li>
Have a look at the configuration file 'gaiandb_config.properties'. This defines logical tables (LT0, LT1, ..), and their federated physical data sources (LT0_DS0, LT0_DS1, ..). You can find out more about these configuration settings <a href="#contents175">here</a>.
</li>
</ul>

<hr><h3><a name="contents169">Verify the installation</a></h3>
<p>To quickly test that GaianDB is up and running:</p>
<ul><li>Run 'testGaianDB.bat' on Windows or './testGaianDB.sh' on Unix. This launches a sample query against the sample LT0 logical table, which should retrieve &amp; display the records from the CSV flat file found at: '&lt;GaianDB Install Directory&gt;/csvtestfiles/datafile.dat'.</li></ul>

<p>You can also run other queries against GaianDB using the <a href="#contents140">Command Line Processor</a> or <a href="#contents344">Dashboard Graphical User Interface</a> client utilities.
For example, you can use to the Command Line Processor to run 'select' commands or run some of the stored procedures the GaianDB provides to verify the installation is correct, as follows:</p>
<ol>
	<li>
		Run 'queryDerby.bat' on Windows or './queryDerby.sh' on Unix.
		<br>Once the the Command Line Processor is ready to receive commands you will see: <pre>sql></pre>
	</li><br>
	<li>
		To query a GaianDB logical table, use the syntax: 'select <i>xxx</i> from LT0 where ...' where LT0 is the name of a logical table defined in the 'gaiandb_config.properties'.
		<br>For example you can type:<pre>select * from LT0</pre>
	</li><br>
	<li>To execute the stored procedure API calls use the following:
		<ul>
		<li><pre>call listspfs()</pre>- lists all defined stored procedures and functions.</li>
		<li><pre>call listlts()</pre>- lists all defined Logical Tables.</li>
		<li><pre>call listds() </pre>- lists all Data Sources federated by all logical tables.</li>
		<li><pre>call listrdbc()</pre>- lists all active (i.e. that have an attached data source) relational database connections</li>
		</ul>
	</li>
</ol>
<br/>

<hr><h3><a name="contents52">Quick table federation examples (matching a Logical Table to a Physical One)</a></h3>

<ul style="margin-top:1em;">
	<li><a href="#contents53">Federate an RDBMS table</a></li>
	<li><a href="#contents60">Federate an existing CSV File</a></li>
	<li><a href="#contents201">Federate an existing Excel spreadsheet</a></li>
</ul>

<p>For each example, first start a GaianDB node (see <a href="#contents168">First Steps</a>).</p>
<p>Then, when the server has started, run 'queryDerby.bat' on Windows or './queryDerby.sh' on Unix to start a Command Line Processor connected to the GaianDB server.</p>
<p><b>Note:</b> You can also use the <a href="#contents344">Dashboard Graphical User Interface</a> client utility to perform these examples.</p>
<hr><h4><a name="contents53">Federate an RDBMS table</a></h4>
<p>
In this quick example we will show you how to federate an existing RDBMS table using GaianDB. For this we will use the DB2 sample table 'employee'; please refer to the <a href="http://publib.boulder.ibm.com/infocenter/db2luw/v9/index.jsp?topic=%2Fcom.ibm.db2.udb.admin.doc%2Fdoc%2Fr0001934.htm">DB2 documentation for how to install the sample tables</a>.
</p>
<ol>
<li><a name="contents54">List all the active Relational Database Connections to see the current state of the GaianDB node:</a></li>
<pre>
sql>
sql> call listrdbc()
call listrdbc()
============================================================================================================================================
GDB_NODE        |CID             |CDRIVER                                       |CURL                                 |CUSR                |
============================================================================================================================================
L3R3844         |LOCALDERBY      |org.apache.derby.jdbc.EmbeddedDriver          |jdbc:derby:gaiandb;create=true       |gaiandb             |
L3R3844         |mysql5          |com.mysql.jdbc.Driver                         |jdbc:mysql://localhost:3306/test     |root                |
============================================================================================================================================
Fetched 2 rows. Total Time: 47ms (Execution Time: 47ms)

sql>
</pre>
<br/><li><a name="contents55">Create a new Relational Database Connection.</a><br />
To do this we use the GaianDB stored procedure <code>setrdbc(...)</code> with a connection id of 'db2conn' and the driver & url as shown below (unless your DB2 instance is running on a different machine or port). Enter your own user name and password for DB2 in place of the last 2 arguments.</li>
<pre>
sql>
sql> call setrdbc('db2conn', 'com.ibm.db2.jcc.DB2Driver', 'jdbc:db2://localhost:50000/sample', 'DavidVyvyan', '???????')
call setrdbc('db2conn', 'com.ibm.db2.jcc.DB2Driver', 'jdbc:db2://localhost:50000/sample', 'DavidVyvyan', '???????')

sql>
</pre>

<br /><li><a name="contents56">Setup a Logical Table that includes all columns of the 'employee' table and federates it.</a><br />
To do this we use the GaianDB stored procedure <code>setltforrdbtable(&lt;New Logical Table Name&gt;, &lt;Database Connection&gt;, &lt;Selection Predicate&gt;)</code>. For example:</li>
<pre>
sql> call setltforrdbtable('db2employee', 'db2conn', 'employee')
call setltforrdbtable('db2employee', 'db2conn', 'employee')

sql>
</pre>
Where:
<ul>
<li>'db2employee' is the new logical table name.</li>
<li>'db2conn' designates the RDBMS connection we just created.</li>
<li>'employee' matches the entire 'employee' table.</li>
</ul>
<p>NOTE: The DB2 driver classes must be on the CLASSPATH in launchGaianServer.bat.</p>

<br /><li><a name="contents57">Query the new Logical Table.</a><br />
To do this you can simply issue a standard SQL SELECT query on the table 'db2employee'. For example:</li>
<pre>
sql> select * from db2employee
select * from db2employee
========================================================================================================================================================
EMPNO |FIRSTNME    |MIDINIT|LASTNAME       |WORKDEPT|PHONENO|HIREDATE  |JOB     |EDLEVEL|SEX|BIRTHDATE |SALARY     |BONUS      |COMM       |NODEINDEX  |
========================================================================================================================================================
000010|CHRISTINE   |I      |HAAS           |A00     |3978   |1995-01-01|PRES    |     18|F  |1963-08-24|  152750.00|    1000.00|    4220.00|          1|
000020|MICHAEL     |L      |THOMPSON       |B01     |3476   |2003-10-10|MANAGER |     18|M  |1978-02-02|   94250.00|     800.00|    3300.00|          1|
000030|SALLY       |A      |KWAN           |C01     |4738   |2005-04-05|MANAGER |     20|F  |1971-05-11|   98250.00|     800.00|    3060.00|          1|
000050|JOHN        |B      |GEYER          |E01     |6789   |1979-08-17|MANAGER |     16|M  |1955-09-15|   80175.00|     800.00|    3214.00|          1|
000060|IRVING      |F      |STERN          |D11     |6423   |2003-09-14|MANAGER |     16|M  |1975-07-07|   72250.00|     500.00|    2580.00|          1|
000070|EVA         |D      |PULASKI        |D21     |7831   |2005-09-30|MANAGER |     16|F  |2003-05-26|   96170.00|     700.00|    2893.00|          1|
000090|EILEEN      |W      |HENDERSON      |E11     |5498   |2000-08-15|MANAGER |     16|F  |1971-05-15|   89750.00|     600.00|    2380.00|          1|
000100|THEODORE    |Q      |SPENSER        |E21     |0972   |2000-06-19|MANAGER |     14|M  |1980-12-18|   86150.00|     500.00|    2092.00|          1|
000110|VINCENZO    |G      |LUCCHESSI      |A00     |3490   |1988-05-16|SALESREP|     19|M  |1959-11-05|   66500.00|     900.00|    3720.00|          1|
000120|SEAN        |       |O'CONNELL      |A00     |2167   |1993-12-05|CLERK   |     14|M  |1972-10-18|   49250.00|     600.00|    2340.00|          1|
000130|DELORES     |M      |QUINTANA       |C01     |4578   |2001-07-28|ANALYST |     16|F  |1955-09-15|   73800.00|     500.00|    1904.00|          1|
000140|HEATHER     |A      |NICHOLLS       |C01     |1793   |2006-12-15|ANALYST |     18|F  |1976-01-19|   68420.00|     600.00|    2274.00|          1|
000150|BRUCE       |       |ADAMSON        |D11     |4510   |2002-02-12|DESIGNER|     16|M  |1977-05-17|   55280.00|     500.00|    2022.00|          1|
000160|ELIZABETH   |R      |PIANKA         |D11     |3782   |2006-10-11|DESIGNER|     17|F  |1980-04-12|   62250.00|     400.00|    1780.00|          1|
000170|MASATOSHI   |J      |YOSHIMURA      |D11     |2890   |1999-09-15|DESIGNER|     16|M  |1981-01-05|   44680.00|     500.00|    1974.00|          1|
000180|MARILYN     |S      |SCOUTTEN       |D11     |1682   |2003-07-07|DESIGNER|     17|F  |1979-02-21|   51340.00|     500.00|    1707.00|          1|
000190|JAMES       |H      |WALKER         |D11     |2986   |2004-07-26|DESIGNER|     16|M  |1982-06-25|   50450.00|     400.00|    1636.00|          1|
000200|DAVID       |       |BROWN          |D11     |4501   |2002-03-03|DESIGNER|     16|M  |1971-05-29|   57740.00|     600.00|    2217.00|          1|
000210|WILLIAM     |T      |JONES          |D11     |0942   |1998-04-11|DESIGNER|     17|M  |2003-02-23|   68270.00|     400.00|    1462.00|          1|
000220|JENNIFER    |K      |LUTZ           |D11     |0672   |1998-08-29|DESIGNER|     18|F  |1978-03-19|   49840.00|     600.00|    2387.00|          1|
000230|JAMES       |J      |JEFFERSON      |D21     |2094   |1996-11-21|CLERK   |     14|M  |1980-05-30|   42180.00|     400.00|    1774.00|          1|
000240|SALVATORE   |M      |MARINO         |D21     |3780   |2004-12-05|CLERK   |     17|M  |2002-03-31|   48760.00|     600.00|    2301.00|          1|
000250|DANIEL      |S      |SMITH          |D21     |0961   |1999-10-30|CLERK   |     15|M  |1969-11-12|   49180.00|     400.00|    1534.00|          1|
000260|SYBIL       |P      |JOHNSON        |D21     |8953   |2005-09-11|CLERK   |     16|F  |1976-10-05|   47250.00|     300.00|    1380.00|          1|
000270|MARIA       |L      |PEREZ          |D21     |9001   |2006-09-30|CLERK   |     15|F  |2003-05-26|   37380.00|     500.00|    2190.00|          1|
000280|ETHEL       |R      |SCHNEIDER      |E11     |8997   |1997-03-24|OPERATOR|     17|F  |1976-03-28|   36250.00|     500.00|    2100.00|          1|
000290|JOHN        |R      |PARKER         |E11     |4502   |2006-05-30|OPERATOR|     12|M  |1985-07-09|   35340.00|     300.00|    1227.00|          1|
000300|PHILIP      |X      |SMITH          |E11     |2095   |2002-06-19|OPERATOR|     14|M  |1976-10-27|   37750.00|     400.00|    1420.00|          1|
000310|MAUDE       |F      |SETRIGHT       |E11     |3332   |1994-09-12|OPERATOR|     12|F  |1961-04-21|   35900.00|     300.00|    1272.00|          1|
000320|RAMLAL      |V      |MEHTA          |E21     |9990   |1995-07-07|FIELDREP|     16|M  |1962-08-11|   39950.00|     400.00|    1596.00|          1|
000330|WING        |       |LEE            |E21     |2103   |2006-02-23|FIELDREP|     14|M  |1971-07-18|   45370.00|     500.00|    2030.00|          1|
000340|JASON       |R      |GOUNOT         |E21     |5698   |1977-05-05|FIELDREP|     16|M  |1956-05-17|   43840.00|     500.00|    1907.00|          1|
200010|DIAN        |J      |HEMMINGER      |A00     |3978   |1995-01-01|SALESREP|     18|F  |1973-08-14|   46500.00|    1000.00|    4220.00|          1|
200120|GREG        |       |ORLANDO        |A00     |2167   |2002-05-05|CLERK   |     14|M  |1972-10-18|   39250.00|     600.00|    2340.00|          1|
200140|KIM         |N      |NATZ           |C01     |1793   |2006-12-15|ANALYST |     18|F  |1976-01-19|   68420.00|     600.00|    2274.00|          1|
200170|KIYOSHI     |       |YAMAMOTO       |D11     |2890   |2005-09-15|DESIGNER|     16|M  |1981-01-05|   64680.00|     500.00|    1974.00|          1|
200220|REBA        |K      |JOHN           |D11     |0672   |2005-08-29|DESIGNER|     18|F  |1978-03-19|   69840.00|     600.00|    2387.00|          1|
200240|ROBERT      |M      |MONTEVERDE     |D21     |3780   |2004-12-05|CLERK   |     17|M  |1984-03-31|   37760.00|     600.00|    2301.00|          1|
200280|EILEEN      |R      |SCHWARTZ       |E11     |8997   |1997-03-24|OPERATOR|     17|F  |1966-03-28|   46250.00|     500.00|    2100.00|          1|
200310|MICHELLE    |F      |SPRINGER       |E11     |3332   |1994-09-12|OPERATOR|     12|F  |1961-04-21|   35900.00|     300.00|    1272.00|          1|
200330|HELENA      |       |WONG           |E21     |2103   |2006-02-23|FIELDREP|     14|F  |1971-07-18|   35370.00|     500.00|    2030.00|          1|
200340|ROY         |R      |ALONZO         |E21     |5698   |1997-07-05|FIELDREP|     16|M  |1956-05-17|   31840.00|     500.00|    1907.00|          1|
========================================================================================================================================================
Fetched 42 rows. Total Time: 219ms (Execution Time: 172ms)

sql>
</pre>
<p>This contains all columns from the physical table 'employee' and also an example constant column 'NODEINDEX' to identify which GaianDB node the information is from. For more info on constant columns, refer to <a href="#contents92">this section</a>.</p>

<br /><li>
<a name="contents58">List the active RDBMS connections and data sources to verify updates.</a><br />
To do this we use two GaianDB stored procedures: <br /><br />
<ul>
    <li><code>listrdbc()</code> - this shows the active RDBMS connections of every connected GaianDB node (the only node in the example below is L3R3844).

<pre>
sql>
sql> call listrdbc()
call listrdbc()
============================================================================================================================================
GDB_NODE        |CID             |CDRIVER                                       |CURL                                 |CUSR                |
============================================================================================================================================
L3R3844         |LOCALDERBY      |org.apache.derby.jdbc.EmbeddedDriver          |jdbc:derby:gaiandb;create=true       |gaiandb             |
L3R3844         |mysql5          |com.mysql.jdbc.Driver                         |jdbc:mysql://localhost:3306/test     |root                |
L3R3844         |DB2CONN         |com.ibm.db2.jcc.DB2Driver                     |jdbc:db2://localhost:50000/sample    |DavidVyvyan         |
============================================================================================================================================
Fetched 3 rows. Total Time: 47ms (Execution Time: 16ms)

sql>
</pre></li>

    <li><code>listds()</code> -  this shows all the active data sources of every connected GaianDB node.
<pre>
sql>
sql> call listds()
call listds()
=====================================================================================================================================================================================
GDB_NODE        |DSID                |DSTYPE|DSWRAPPER           |DSHANDLE                                                                               |DSOPTIONS                 |
=====================================================================================================================================================================================
L3R3844         |DB2SALES_DS0        |R     |tk:1                |jdbc:db2://localhost:50000/sample::sales                                               |-                         |
L3R3844         |LT1_DS0             |R     |EmbedStatement:1    |jdbc:derby:gaiandb;create=true::TABLE1                                                 |-                         |
L3R3844         |LT0_DS0             |V     |InMemoryRows:1      |./csvtestfiles/datafile.dat                                                            |INMEMORY                  |
L3R3844         |DB2EMPLOYEE_DS0     |R     |InMemoryRows:1      |jdbc:db2://localhost:50000/sample::employee where firstnme > 'T'                       |INMEMORY INDEX ON FIRSTNME|
L3R3844         |DF2_DSDATAFILE2     |V     |FileImport:1        |./csvtestfiles/datafile2.dat                                                           |-                         |
L3R3844         |MYSQLLT_DSCARS      |R     |InMemoryRows:1      |jdbc:mysql://localhost:3306/test::cars                                                 |INMEMORY                  |
L3R3844         |DERBY_TABLES_DSLOC  |R     |EmbedStatement:1    |jdbc:derby:gaiandb;create=true::sys.systables,sys.syscolumns where tableid=referenceid |-                         |
=====================================================================================================================================================================================
Fetched 7 rows. Total Time: 62ms (Execution Time: 46ms)

sql>
</pre>

<p>
The data source id (DSID) is a composite name which has as prefix of the logical table name to which it is attached.
Other columns denote:<br /><br />

<table class="data">
<thead>
<tr><th>Column Name</th><th>Description</th></tr>
</thead>
<tbody>
<tr><td>DSTYPE</td><td>Data source type (e.g. R for RDBMS, V for Virtual Table)</td></tr>
<tr><td>DSWRAPPER</td><td>
Wrapping class and the number of pool instances in memory.</td></tr>
<tr><td>DSHANDLE</td><td>
Physical source handle descriptor (e.g data source filename or db url+table name)</td></tr>
<tr><td>DSOPTIONS</td><td>
Data source options list. This currently only describes whether the data source is held in memory and, if so, any index that might be defined on one of its columns.</td></tr>
</tbody>
</table>
</p>
</li>
</ul>

<br/><li><a name="contents59">Federate only a portion of the 'employee' table by using a selection predicate on it.</a><br />
Here we will pass a more complex selection predicate to the <code>setltforrdbtable(...)</code> stored procedure so that only matching records from the 'employee' table are federated.</li>
<pre>
sql>
sql> call setltforrdbtable('db2employee', 'db2conn', 'employee where firstnme > ''T''')
call setltforrdbtable('db2employee', 'db2conn', 'employee where firstnme > ''T''')

sql>
sql> select * from db2employee
select * from db2employee
========================================================================================================================================================
EMPNO |FIRSTNME    |MIDINIT|LASTNAME       |WORKDEPT|PHONENO|HIREDATE  |JOB     |EDLEVEL|SEX|BIRTHDATE |SALARY     |BONUS      |COMM       |NODEINDEX  |
========================================================================================================================================================
000100|THEODORE    |Q      |SPENSER        |E21     |0972   |2000-06-19|MANAGER |     14|M  |1980-12-18|   86150.00|     500.00|    2092.00|          1|
000110|VINCENZO    |G      |LUCCHESSI      |A00     |3490   |1988-05-16|SALESREP|     19|M  |1959-11-05|   66500.00|     900.00|    3720.00|          1|
000210|WILLIAM     |T      |JONES          |D11     |0942   |1998-04-11|DESIGNER|     17|M  |2003-02-23|   68270.00|     400.00|    1462.00|          1|
000330|WING        |       |LEE            |E21     |2103   |2006-02-23|FIELDREP|     14|M  |1971-07-18|   45370.00|     500.00|    2030.00|          1|
========================================================================================================================================================
Fetched 4 rows. Total Time: 31ms (Execution Time: 15ms)

sql>
sql>
</pre>
<p>These selection predicates can be very complex. For example, you could use one to federate the result of a join between two tables.</p>
</ol>


<hr><h4><a name="contents60">Federate an existing CSV File</a></h4>
<p>
In this quick example we will show you how to federate an existing CSV flat file using GaianDB. For this we will use the file found at '&lt;GaianDB Install Directory&gt;/csvtestfiles/datafile3.dat'.
</p>
<p>
Note that GaianDB's FileImport VTI can read many different file formats, not just CSV.
The record and field separators and other 'control parameters' such as these may be altered using a 'control file'. Refer to
<a href="#contents99">Text file federation configuration options (e.g: how to specify different record and field separators)</a> for details.
</p>
<p><b>Note:</b> All paths, whether on Windows or Unix, should use forward slashes (/) and not backslashes (\).</p>
<ol>
<li><a name="contents61">Federate the CSV flat file 'datafile3.dat' as an RDBMS table called 'zzz'.</a><br />
To do this, we call the stored GaianDB procedure <code>setltforfile(&lt;logical table name&gt;, &lt;file location&gt;)</code>.</li>
<pre>
sql>
sql> call setltforfile('zzz', './csvtestfiles/datafile3.dat')
call setltforfile('zzz', './csvtestfiles/datafile3.dat')

sql>
</pre>
<br/><li><a name="contents62">List data sources to verify that the update was applied.</a><br />
To do this, we call the stored GaianDB procedure <code>listds()</code>. 
Refer to the
<a href="#contents58">previous explanation on the columns returned by listrdbc() and listds()</a> for details on the columns used here.</li>
<pre>
sql>
sql> call listds()
call listds()
=========================================================================================================================================================================================
GDB_NODE            |DSID                |DSTYPE|DSWRAPPER           |DSHANDLE                                                                               |DSOPTIONS                 |
=========================================================================================================================================================================================
L3R3844             |DB2SALES_DS0        |R     |tk:1                |jdbc:db2://localhost:50000/sample::sales                                               |-                         |
L3R3844             |LT1_DS0             |R     |EmbedStatement:1    |jdbc:derby:gaiandb;create=true::TABLE1                                                 |-                         |
L3R3844             |LT0_DS0             |V     |InMemoryRows:1      |./csvtestfiles/datafile.dat                                                            |INMEMORY                  |
L3R3844             |DB2EMPLOYEE_DS0     |R     |InMemoryRows:1      |jdbc:db2://localhost:50000/sample::employee where firstnme > 'T'                       |INMEMORY INDEX ON FIRSTNME|
L3R3844             |ZZZ_DS0             |V     |FileImport:1        |./csvtestfiles/datafile3.dat                                                           |-                         |
L3R3844             |MYSQLLT_DSCARS      |R     |InMemoryRows:1      |jdbc:mysql://localhost:3306/test::cars                                                 |INMEMORY                  |
L3R3844             |DERBY_TABLES_DSLOC  |R     |EmbedStatement:1    |jdbc:derby:gaiandb;create=true::sys.systables,sys.syscolumns where tableid=referenceid |-                         |
=========================================================================================================================================================================================
Fetched 7 rows. Total Time: 31ms (Execution Time: 0ms)

sql>
</pre>
<p>If it was successful, you should see an entry with a DSID of 'ZZZ_DS0' and a DSHANDLE of './csvtestfiles/datafile3.dat'.</p>

<br/><li><a name="contents63">Query the new Logical Table.</a><br />
To do this you can simply issue a standard SQL SELECT query on the table 'zzz'. For example:</li>
<pre>
sql>
sql> select * from zzz
select * from zzz
====================================================================================================================================================================================
COLUMN1           |COLUMN2               |COLUMN3             |COLUMN4             |COLUMN5             |COLUMN6             |COLUMN7             |COLUMN8             |NODEINDEX  |
====================================================================================================================================================================================
2                 |YYYYYYYYYYY2222222222 |62                  |35                  |17                  |10                  |122                 |65.6                |          1|
91                |BLAHBLAH              |3                   |2                   |44                  |35                  |0                   |2.1                 |          1|
9                 |SHG*&^22datafile3     |62                  |35                  |17                  |10                  |122                 |65.6                |          1|
9                 |FFFFFFFFFFFK2222222222|62                  |35                  |17                  |10                  |122                 |65.6                |          1|
====================================================================================================================================================================================
Fetched 4 rows. Total Time: 16ms (Execution Time: 16ms)

sql>
sql>
</pre>
<p>This contains all columns from the CSV file and also an example constant column 'NODEINDEX' to identify which GaianDB node the information is from. For more info on constant columns, refer to <a href="#contents92">this section</a>.</p>
</ol>

<hr><h4><a name="contents201">Federate an existing Excel spreadsheet</a></h4>

<p>In this quick example we will show you how to federate an existing Excel spreadsheet using GaianDB. For this we will use the spreadsheet found at '&lt;GaianDB Install Directory&gt;/exceltestfiles/address.xls'.</p>
<p><b>Note:</b> All paths, whether on Windows or Unix, should use forward slashes (/) and not backslashes (\).</p>
<ol>
	<li>
		<a name="contents202"> Prerequisites</a>
		<p>
		If you wish to perform this example, you will require the POI libraries (version 3.6 or above) for manipulating Microsoft Documents from the <a href="http://poi.apache.org/download.html">Apache POI website</a>. If you are happy to accept the license terms, you can choose to download the binary distributions. The necessary jar files are:
		<ul>
			<li> poi-XX.jar </li>
			<li> poi-ooxml-XX.jar </li>
			<li> poi-ooxml-schemas-XX.jar </li>
			<li> dom4j-XX.jar </li>
			<li> geronimo-stax-api_XX.jar (or stax-api-xx.jar in some versions of POI)</li>
			<li> xmlbeans-XX.jar </li>
		</ul>
		</p>

		<p>
		Where XX is the version number.</p>
		<p>These jars would need to be placed into the GaianDB lib directory and then added to the GaianDB classpath as follows:</p>
		<ul>
			<li> On Windows, edit the 'launchGaianServer.bat' file (right click -> edit). </li>
			<li> Add the following lines :
				<pre>
rem Apache - POI jars for spreadsheet federation
SET CLASSPATH=%CLASSPATH%;%GDBL%\geronimo-stax-api_XX.jar;%GDBL%\poi-ooxml-schemas-XX.jar;%GDBL%\dom4j-XX.jar;%GDBL%\poi-XX.jar;%GDBL%\poi-ooxml-XX.jar;%GDBL%\xmlbeans-XX.jar
				</pre>
			</li>
			<li> On Unix, edit the 'launchGaianServer.sh' file. </li>
			<li> Add the following lines :
			        <pre>
# Apache - POI jars for spreadsheet federation
export CLASSPATH="$CLASSPATH:$GDBL/geronimo-stax-api_XX.jar:$GDBL/poi-ooxml-schemas-XX.jar:$GDBL/dom4j-XX.jar:$GDBL/poi-XX.jar:$GDBL/poi-ooxml-XX.jar:$GDBL/xmlbeans-XX.jar"
                                </pre>
                        </li>
		</ul>
		<p>If you had already started the GaianDB by using the launchGaianServer script, you will need to stop the node and restart it for the new changes to be taken into account.
		To stop GaianDB, you can either close the command window on Windows, or use Ctrl-C on Unix or use the killGaianServer script.
		When starting multiple nodes, you will need to use the killGaianServers script to stop them all.</p>
	</li>

	<br/>
	<li>
		<a name="contents203">
		Federate the Excel spreadsheet 'Sheet1' from the file 'address.xls' as an RDBMS table.</a><br />To do this, we use the GaianDB stored procedure <code>setltforexcel(...)</code>:
	</li>

	<pre>
sql>
sql> call setltforexcel('lsheet1', 'exceltestfiles/address.xls,Sheet1')
call setltforexcel('lsheet1', 'exceltestfiles/address.xls,Sheet1')

sql>
	</pre>

	You can also federate a part of the spreadsheet by defining a range :

	<pre>
sql>
sql> call setltforexcel('lsheet2', 'exceltestfiles/address.xls,Sheet1,A1,D7')
call setltforexcel('lsheet2', 'exceltestfiles/address.xls,Sheet1,A1,D7')

sql>
	</pre>

	By default, the values of the first row are used as the column names for the federated table. However, if the first row does not contain the column names, you can add 'false' to the parameters to have the column names automatically generated; in the form <i>COLUMN1</i>, <i>COLUMN2</i>, <i>COLUMN&lt;n&gt;</i>:

	<pre>
sql>
sql> call setltforexcel('lsheet3', 'exceltestfiles/address.xls,Sheet1,A5,D7,false')
call setltforexcel('lsheet3', 'exceltestfiles/address.xls,Sheet1,A5,D7,false')

sql>
	</pre>

	<br/>
	<li>
		<a name="contents204">
		List data sources to verify that the update was applied.</a><br /> To do this, we call the stored GaianDB procedure <code>listds()</code>. Refer to the <a href="#contents58"> previous explanation on the columns returned by listrdbc() and listds()</a> for details on the columns used here.
	</li>
	<pre>
sql>
sql> call listds()
call listds()
===============================================================================================================================================================================
GDB_NODE    |DSID                |DSTYPE|DSWRAPPER         |DSHANDLE                                                                               |DSOPTIONS                 |
===============================================================================================================================================================================
L3R3844     |DB2SALES_DS0        |R     |tk:1              |jdbc:db2://localhost:50000/sample::sales                                               |-                         |
L3R3844	    |LSHEET1_DS0         |V     |-                 |address.xls,Sheet1                                                                     |-                         |
L3R3844     |LSHEET2_DS0         |V     |-                 |address.xls,Sheet1,A:1,D:7                                                             |-                         |
L3R3844     |LT1_DS0             |R     |EmbedStatement:1  |jdbc:derby:gaiandb;create=true::TABLE1                                                 |-                         |
L3R3844     |LT0_DS0             |V     |InMemoryRows:1    |./csvtestfiles/datafile.dat                                                            |INMEMORY                  |
L3R3844     |DB2EMPLOYEE_DS0     |R     |InMemoryRows:1    |jdbc:db2://localhost:50000/sample::employee where firstnme > 'T'                       |INMEMORY INDEX ON FIRSTNME|
L3R3844     |ZZZ_DS0             |V     |FileImport:1      |./csvtestfiles/datafile3.dat                                                           |-                         |
L3R3844     |MYSQLLT_DSCARS      |R     |InMemoryRows:1    |jdbc:mysql://localhost:3306/test::cars                                                 |INMEMORY                  |
L3R3844     |DERBY_TABLES_DSLOC  |R     |EmbedStatement:1  |jdbc:derby:gaiandb;create=true::sys.systables,sys.syscolumns where tableid=referenceid |-                         |
===============================================================================================================================================================================
Fetched 7 rows. Total Time: 31ms (Execution Time: 0ms)
	</pre>

	<br/>
	<li>
		<a name="contents205">Query the new Logical Tables.</a><br />To do this you can simply issue a standard SQL SELECT query against the 'LSheet1', 'LSheet2' and 'LSheet3' tables. For example:
	</li>

	<pre>
sql> select * from LSheet1
select * from LSheet1
================================================================================================
LAST        |FIRST          |ADDRESS                    |CITY            |STATE    |ZIP        |
================================================================================================
Buffet      |Jimmy          |Somewhere on the Beach     |KeyWest         |FL       |      33040|
Bush        |George         |1600 Pennsylvania Ave      |Washington      |DC       |      20500|
Cartman     |Eric           |84 Bigboned Way            |South Park      |CO       |      84214|
Crockett    |Davey          |The Alamo                  |San Antonio     |TX       |      78210|
Doe         |Jane           |821 Zimbabwe Ave           |Washington      |DC       |      20021|
Gates       |Bill           |1 Microsoft Way            |Redmond         |WA       |      98052|
Jefferson   |George         |194 Deelux Apartments      |In the Sky      |NY       |      10041|
Kong        |King           |Empire State Building      |New York        |NY       |      10118|
Munster     |Herman         |1313 Mockingbird Lane      |Fargo           |ND       |      58102|
Rockne      |Knute          |146 Keenan Hall            |Notre Dame      |IN       |      46556|
Simpson     |Homer          |742 Evergreen Terrace      |Springfield     |US       |      12345|
Smith       |Bob            |12 Main Street             |Anytown         |IN       |      46001|
================================================================================================
Fetched 12 rows. Total Time: 62ms (Execution Time: 31ms)
</pre>
<pre>
sql> select * from LSheet2
select * from LSheet2
==========================================================================
LAST        |FIRST          |ADDRESS                    |CITY            |
==========================================================================
Buffet      |Jimmy          |Somewhere on the Beach     |KeyWest         |
Bush        |George         |1600 Pennsylvania Ave      |Washington      |
Cartman     |Eric           |84 Bigboned Way            |South Park      |
Crockett    |Davey          |The Alamo                  |San Antonio     |
Doe         |Jane           |821 Zimbabwe Ave           |Washington      |
Gates       |Bill           |1 Microsoft Way            |Redmond         |
==========================================================================
Fetched 6 rows. Total Time: 46ms (Execution Time: 15ms)
</pre>
<pre>
sql> select * from LSheet3
select * from LSheet3
==========================================================================
COLUMN1     |COLUMN2        |COLUMN3                    |COLUMN4         |
==========================================================================
Crockett    |Davey          |The Alamo                  |San Antonio     |
Doe         |Jane           |821 Zimbabwe Ave           |Washington      |
Gates       |Bill           |1 Microsoft Way            |Redmond         |
==========================================================================
Fetched 3 rows. Total Time: 63ms (Execution Time: 47ms)
</pre>
You can use predicates to filter the view even further. <b>Note</b>: in the example below we have to use "" around the word LAST as it is an SQL keyword.
Putting the "" specifies that this should be taken as a string and hence a column name and now as the SQL keyword.
Here we select entries where the last name starts with the letters from C to Z in alphabetical order.
<pre>
sql> select * from lsheet1 where "LAST" > 'C'
select * from lsheet1 where "LAST" > 'C'
==========================================================================================================
LAST        |FIRST          |ADDRESS                    |CITY             |STATE    |ZIP        |COLUMN7 |
==========================================================================================================
Cartman     |Eric           |84 Bigboned Way            |South Park       |CO       |      84214|-       |
Crockett    |Davey          |The Alamo                  |San Antonio      |TX       |      78210|-       |
Doe         |Jane           |821 Zimbabwe Ave           |Washington       |DC       |      20021|-       |
Gates       |Bill           |1 Microsoft Way            |Redmond          |WA       |      98052|-       |
Jefferson   |George         |194 Deelux Apartments      |In the Sky       |NY       |      10041|-       |
Kong        |King           |Empire State Building      |New York         |NY       |      10118|-       |
Munster     |Herman         |1313 Mockingbird Lane      |Fargo            |ND       |      58102|-       |
Rockne      |Knute          |146 Keenan Hall            |Notre Dame       |IN       |      46556|-       |
Simpson     |Homer          |742 Evergreen Terrace      |Springfield      |US       |      12345|-       |
Smith       |Bob            |12 Main Street             |Anytown          |IN       |      46001|-       |
==========================================================================================================
Fetched 10 rows. Total Time: 59ms (Execution Time: 55ms)
</pre>

<p>If you wish, you can also add another Excel file as a Data Source to one of the logical tables created above. Here we select row 2 and 3 to be added to LSheet3.
So LSheet3 will now have a view of rows: 2,3 and 5,6,7. 
<pre>
sql> call setdsexcel('lsheet3', '1', 'exceltestfiles/address.xls,Sheet1,A2,D3,false','MAP_COLUMNS_BY_POSITION', '')
call setdsexcel('lsheet3', '1', 'exceltestfiles/address.xls,Sheet1,A2,D3,false','MAP_COLUMNS_BY_POSITION', '')</pre>
Below we can see how the new data source has been linked to the logical table:
<pre>
sql> call listds()
call listds()
=================================================================================================================================================================================
GDB_NODE    |DSID                |DSTYPE|DSWRAPPER           |DSHANDLE                                                                               |DSOPTIONS                 |
=================================================================================================================================================================================
L3R3844     |DB2SALES_DS0        |R     |tk:1                |jdbc:db2://localhost:50000/sample::sales                                               |-                         |
L3R3844	    |LSHEET1_DS0         |V     |-                   |address.xls,Sheet1                                                                     |-                         |
L3R3844     |LSHEET2_DS0         |V     |-                   |address.xls,Sheet1,A:1,D:7                                                             |-                         |
L3R3844     |LSHEET3_DS0         |V     |-                   |address.xls,Sheet1,A5,D7,false                                                         |-                         |
L3R3844     |LSHEET3_DS1         |V     |-                   |address.xls,Sheet1,A2,D3,false                                                         |MAP_COLUMNS_BY_POSITION   |
L3R3844     |LT1_DS0             |R     |EmbedStatement:1    |jdbc:derby:gaiandb;create=true::TABLE1                                                 |-                         |
L3R3844     |LT0_DS0             |V     |InMemoryRows:1      |./csvtestfiles/datafile.dat                                                            |INMEMORY                  |
L3R3844     |DB2EMPLOYEE_DS0     |R     |InMemoryRows:1      |jdbc:db2://localhost:50000/sample::employee where firstnme > 'T'                       |INMEMORY INDEX ON FIRSTNME|
L3R3844     |ZZZ_DS0             |V     |FileImport:1        |./csvtestfiles/datafile3.dat                                                           |-                         |
L3R3844     |MYSQLLT_DSCARS      |R     |InMemoryRows:1      |jdbc:mysql://localhost:3306/test::cars                                                 |INMEMORY                  |
L3R3844     |DERBY_TABLES_DSLOC  |R     |EmbedStatement:1    |jdbc:derby:gaiandb;create=true::sys.systables,sys.syscolumns where tableid=referenceid |-                         |
=================================================================================================================================================================================
Fetched 9 rows. Total Time: 31ms (Execution Time: 0ms)
</pre>
There are now more entries in lsheet3.
<pre>
sql> select * from lsheet3 order by column1
select * from lsheet3 order by column1
==========================================================================
COLUMN1     |COLUMN2        |COLUMN3                    |COLUMN4         |
==========================================================================
Buffet      |Jimmy          |Somewhere on the Beach     |KeyWest         |
Bush        |George         |1600 Pennsylvania Ave      |Washington      |
Crockett    |Davey          |The Alamo                  |San Antonio     |
Doe         |Jane           |821 Zimbabwe Ave           |Washington      |
Gates       |Bill           |1 Microsoft Way            |Redmond         |
==========================================================================
Fetched 5 rows. Total Time: 296ms (Execution Time: 294ms)
</pre>
</ol>

<hr><h3><a name="contents338">Further Examples</a></h3>

<p>For more examples see the <a href="WorkedExamples.html">Worked Examples page</a>.</p><br />

<hr><h2><a name="contents110">GaianDB Usage</a></h2>

<hr><h3><a name="contents115">GaianDB node usage</a></h3>
<p>To launch a GaianDB node, simply run 'launchGaianServer.bat' on Windows or './launchGaianServer.sh' on Unix; which can be found in the GaianDB install directory.</p>
<p>This will start a GaianDB node using the default options.</p>

<p>To specify different options at startup, from the command line, simply run the appropriate startup script for your operating system as follows:</p>
On Windows:
<pre>launchGaianServer.bat [-n &lt;nodeID&gt;] [-p &lt;gaian node port&gt;] [-c &lt;configuration file name&gt;] [-mt &lt;message storer topic&gt;] [-log &lt;log level&gt;] [-console] [-g &lt;gateways&gt;] [-initscript &lt;sql init file&gt;]</pre>
On Unix:
<pre>./launchGaianServer.sh [-n &lt;nodeID&gt;] [-p &lt;gaian node port&gt;] [-c &lt;configuration file name&gt;] [-mt &lt;message storer topic&gt;] [-log &lt;log level&gt;] [-console] [-g &lt;gateways&gt;] [-initscript &lt;sql init file&gt;]</pre>

<p>The parameters are defined as follows:</p>
<table class="data">
	<thead>
	<tr>
		<th style="width:13em;">Parameter</th>
		<th>Default</th>
		<th>Description</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>-n &lt;nodeID&gt;</td>
		<td>&lt;hostname value&gt;</td>
		<td>The node ID you wish to use. A suffix of ':&lt;port number&gt;' will be appended for all nodes not running on the default port (6414)</td>
	</tr>
	<tr>
		<td>-p &lt;gaian node port&gt;</td>
		<td>6414</td>
		<td>The TCP port for the GaianDB node to use.</td>
	</tr>
	<tr>
		<td>-c &lt;configuration file name&gt;
		<td>gaiandb_config.properties
		<td>The name of the configuration file for the GaianDB node to use (located in the current working directory).<br />
			The file must have the '.properties' extension and will not be created automatically if it does not exist.<br />
			For more information, please refer to the <a href="#contents175">Configuration section</a>.</td>
	</tr>
	<tr>
		<td>-mt &lt;message storer topic&gt;
		<td>None
		<td>The topic for the Message Storer to use.<br />For more information please refer to the <a href="#contents275">Message Storer: Message Broker Integration (e.g. use with sensors)</a> section.</td>
	</tr>
	<tr>
		<td>-log &lt;log level&gt;
		<td>None
		<td>The level of logging to use. This can only be one of: [NONE, LESS, MORE, ALL].<br />
		If NONE, then no logging is performed.<br />
		Otherwise logging is performed to a file in the current working directory. This file will be named 'gaiandb&lt;port&gt;.log' if a port was specified (using -p) or simply 'gaiandb.log' if no port was specified.<br />
		<br />
		The logging level can otherwise be dynamically updated using the configuration file.</td>
	</tr>
	<tr>
		<td>-console
		<td>N/A
		<td>If specified, then the GaianDB node will log to <i>System.out</i>.<br />
		If used in combination with the -log parameter, then logging will be performed to both <i>System.out</i> and a file.</td>
	</tr>
		<tr>
		<td>-g &lt;gateways&gt;
		<td>None
		<td>List of Discovery Gateways. A discovery gateway is a node outside of your subnet that acts as a relay allowing you to join nodes in its network.</td>
	</tr>
		<tr>
		<td>-initscript &lt;sql init file&gt;
		<td>None
		<td>File location of optional custom SQL initialisation script. For example this may setup logical or physical tables; or stored procedures/functions.</td>
	</tr>
	
	</tbody>
</table>

<p>Note: these are all optional and when not provided the default values will be used. Also, ordering is not important.</p>

<p>To stop GaianDB, you can either close the command window it was started from, or run the killGaianServers script</p>

<br /><hr><h3><a name="contents120">Launching multiple GaianDB nodes</a></h3>
<p>To launch multiple GaianDB nodes on the same machine, simply run 'launchMultipleNodes.bat' on Windows or './launchMultipleNodes.sh' on Unix; which can be found in the GaianDB install directory.</p>
<p>By default this will kick off 3 GaianDB nodes that respectively use the pre-canned configuration files: 'gaiandb_config.properties', 'gaiandb_config2.properties' and 'gaiandb_config3.properties' in the current working directory.</p>
<p>You can optionally pass in the number of nodes to launch and you may also use the '-sameconfig' flag to request that each node use the default configuration file: 'gaiandb_config.properties', as follows:</p>
On Windows:
<pre>launchMultipleNodes.bat [&lt;numnodes&gt; [-sameconfig]]</pre>
On Unix:
<pre>./launchMultipleNodes.sh [&lt;numnodes&gt; [-sameconfig]]</pre>
<p>If the '-sameconfig' flag is not specified, each new launched node will expect to find a new 'gaiandb_configN.properties' file where N is the index of the launched node.</p>

<p>To stop GaianDB, you  will need to run the killGaianServers script.</p>


<br /><hr><h3><a name="contents127">Launching a GaianDB node from a separate directory</a></h3>
<p>A GaianDB node will use the working directory to lookup its system files, i.e. gaiandb_config.properties, derby.properties, gaiandb.log, derby.log and the local physical derby database 'gaiandb'.</p>
<p>However this directory does not neccessarily have to be the GaianDB install folder... This means that you can store separate databases/configurations/logs etc for GaianDB in separate folders, 
e.g. one may have tables accessing a DB2 and another may just be a test instance. These would effectively be 'workspace' folders where you can run GaianDB from.
This can be very useful in networked file system scenarios where you may have multiple machines all having their own workspace folder, and loading the GaianDB code from a remote 
location (which you may also not have write-access to).</p>
<p>To run GaianDB from a separate workspace directory, you just need to set the environment variable GDBH to the GaianDB install folder before launching the 'launchGaianServer' script.
For example:</p>
On Windows:
<pre>
  set GDBH=&lt;install path&gt;
  %GDBH%\launchGaianServer.bat
</pre>
On Unix:
<pre>
  export GDBH=&lt;install path&gt;
  $GDBH/launchGaianServer.sh
</pre>

<p>To stop GaianDB, you  will need to run the killGaianServers script.</p>


<br /><hr><h3><a name="contents130">How to specify a location for configuration and log files and the physical database folder</a></h3>
<p>Continuing on the topic above, in some scenarios you may wish to explicitly set the default location of GaianDB's workspace files: 
i.e. gaiandb_config.properties, derby.properties, gaiandb.log, derby.log and the local physical derby database 'gaiandb'</p>
<p>This can be useful in particular if you have wrapped GaianDB in an OSGi framework or some other 'owning process' which has no concept of a working directory for GaianDB.
To set the location of these GaianDB workspace files, set the Java system property: 'derby.system.home' to point to it before starting the Gaian Database. Note that the gaiandb
config file location can also be overriden beyond this using the -c option passed to launchGaianServer (or GaianNode class directly).</p>
<p>Here's an example where you want to run GaianDB from an independant "User directory", referencing a separate "GaianDB workspace folder" and "GaianDB install path":</p>

<pre>
  # Inside &lt;User directory&gt;/launchGaianServer.sh...:
  export GDBH=&lt;GaianDB install path&gt;
  java -Xmx128m -Dderby.system.home="&lt;GaianDB workspace folder&gt;" -cp "$CLASSPATH" com.ibm.gaiandb.GaianNode $args
</pre>

<br /><hr><h3><a name="contents137">How to manage multiple GaianDB node executions with multiple working directories</a></h3>
<p>While not a typical use case, it may sometimes be desirable to run multiple GaianDB nodes on the same computer. For instance, if you are performing testing or for the purposes of resiliency or load balancing.</p>
<p>If you run multiple GaianDB nodes from the same working directory, they will by default share the same configuration file. This may be desirable if every node shares the same logical table definitions and configuration settings. Otherwise, you would need to specify a different configuration file for each node (using the -c parameter, as explained in <a href="#contents115">GaianDB Server usage</a>).</p>
<p>A cleaner approach is to have each GaianDB node use it's own working directory; and consequently it's own configuration file. The <a href="#contents127">Launching GaianDB from a separate directory</a> section details how to do this.</p>
<p>One issue to consider when running multiple GaianDB nodes on the same machine is whether there will be any physical resource contention. As an example, a single Derby database will only allow one process to access it directly at any one time and so multiple nodes trying to access it simultaneously will suffer from resource contention and may behave unexpectedly. However, you are unlikely to encounter this kind of issue in typical usage scenarios.</p>

<br /><hr><h3><a name="contents138">How to initialise a GaianDB node with User defined Derby objects like Tables, views, procedures,functions</a></h3>
<p>It may be sometimes desirable to initialise the derby database of a GaianDB node with tables, views, index, records, procedures and functions before the Logical tables and datasources are created by GaianDB.
<p>An easy implementation is to prime the Derby database before launching the GaianDB as usual. 
   The priming can be linked to the presence of the GaianDB directory.If the directory is not present, that means the GaianDB has not been launched previously and therefore the derby database need to be created and primed.
   For this,  one can create a copy of the Queryderby.bat  to run a SQL script in standalone derby mode with eventually creation of the Database, with the following lines: 
<P>The new batch file launchGaianServerWithInit.bat can be modified like the following (on Windows):
<pre>@echo off
TITLE Initiliasing the Derby database

if not defined GDBH set GDBH=.
set GDBL=%GDBH%\lib

SET CLASSPATH="%GDBL%\;%GDBL%\GAIANDB.jar;%GDBL%\db2jcutdown.jar;%GDBL%\derby.jar;%GDBL%\derbyclient.jar"

SET ARGS=%*

REM Run a SQL script only if gaianDB directory doesn't exist.
IF  EXIST GAIANDBX GOTO DB_ALREADY_INITIALIZED
      echo  Creating the necessary SQL objects for my application....
      java -cp "%CLASSPATH%" com.ibm.gaiandb.tools.SQLDerbyRunner -td@ -standalone -createdb gaiandb_init2.sql      
:DB_ALREADY_INITIALIZED
 
Call launchGaianServer.bat 
</pre> 

<P>The file gaiandb_init2.sql looks like this below:
<PRE>
  -- a set of SQL statements delimited by @ (signs for multiline support)
  -- and prefixed with ! (for ignoring exceptions:see CLP paragraph in GaianDB documentation)
  !drop table Mytable@
  !create table Mytable (a varchar(20), 
                             bb varchar(10),
                             c int)@
  !create index i1 on  Mytable(a)@                            
  !insert into Mytable values ( 'yoya', 'drvy', 23 )@
  --....more DDL and SQL statements here.... 
</PRE>
<p> The output of launchGaianServerWithInit.bat will look something like this the first time:
<PRE>
 Creating the necessary SQL objects for my application....
Processing args: [-td@, -standalone, -createdb, gaiandb_init2.sql]

Connecting to derby database: jdbc:derby:gaiandb;create=true, usr: gaiandb...

drop table Mytable
Suppressed Exception: 'DROP TABLE' cannot be performed on 'MYTABLE' because it does not exist.
create table Mytable (a varchar(20), bb varchar(10), c int)
Update count: 0 (Execution Time: 23ms)

insert into Mytable values ( 'yoya', 'drvy', 23 )
Update count: 1 (Execution Time: 16ms)

Launching Server...
PROCESS ID:             101832
NODE ID:                MYGDBNODE
WORKING DIRECTORY:      C:\GAIANDB_Demo
LOG FILE:               gaiandb.log
PHYSICAL DATABASE:      gaiandb
CONFIG FILE:            gaiandb_config.properties
VERSION INFO:           V2.x - JAR sizes: [640461, 372333], timestamps: [2012/03/14-17:02:12, 2012/03/14-
17:02:14]

GaianNode started for Derby network server on port: 6414 at Wed Mar 14 17:03:48 GMT 2012

Wed Mar 14 17:03:48 GMT 2012: Connections: Maintained to [MYGDBNODE] (seeking 1), Accepted from []
</PRE>



<br /><hr><h3><a name="contents139">How to integrate GaianDB into a wrapping class or framework: startup, start detection, kill</a></h3>
<p>To integrate GaianDB as an OSGi bundle or as a child 'task' of an owning parent class, you will need to have a means of starting a node, detecting when it has started and stopping it.</p>
<p>This can be done using public methods 'start(<startupOption>)', 'isStarted()' and 'killNode()' on the GaianNode class in GAIANDB.jar. Here's some sample startup code:</p>
<pre>
String gdbHome = System.getProperty("derby.system.home");

if ( null == gdbHome )
	System.setProperty( "derby.system.home", gdbHome = com.ibm.gaiandb.Util.getInstallPath() );
			
final String[] gaianTaskStartupOptions = new String[] { "-c", gdbHome + "/gaiandb_config.properties" }; // e.g new String[] { "-p", "6414", "-n", "MyNodeID" }

final GaianNode gdbNode = new GaianNode();

Thread gdbParentThread = new Thread( new Runnable() {
	public void run() {
		try {
			gdbNode.start( gaianTaskStartupOptions );
			System.out.println("GaianNode parent thread exited cleanly (no Exception)");
		}
		catch (Exception e) {
			System.out.println("GaianNode parent thread Exception: " + e);
		}
	}
});

gdbParentThread.start();

boolean gdbStartupGood = true;

while ( gdbNode.isStarted() == false ) {
	if ( ! gdbParentThread.isAlive() ) {
		System.out.println("GaianNode parent thread has died");
		gdbStartupGood = false;
		break;
	}
	Thread.sleep( 100 );
}
</pre>


 
<br /><hr><h2><a name="contents339">Client Usage</a></h2>

<hr><h3><a name="contents140">Command line processor (CLP) options with 'queryDerby'</a></h3>
<p>A command line processor (CLP) client utility is provided with the GaianDB installation. This can be used to run queries on GaianDB and also to issue the GaianDB stored procedures. You can find the CLP in the installation directory and it can be launched by running 'queryDerby.bat' on Windows and 'queryDerby.sh' on Unix.</p>
<p>By default the CLP tries to connect to a local Derby Network server, running on the default GaianDB port: 6414, which is started automatically when a GaianDB node is started.</p>
<p>You can specify different options at startup by launching 'queryDerby' from the command line as follows:</p>
On Windows:
<pre>
queryDerby.bat [-h &lt;host&gt;] [-p &lt;port&gt;] [-usr &lt;usr&gt;] [-pwd &lt;pwd&gt;] [-standalone] [-d &lt;database&gt;] [-createdb] [-nocreatedb] [-repeat &lt;count&gt;] [-tab] [-csv] [-raw] [-csvraw] [-quiet] [-batchprefix &lt;prefix sql&gt;] &lt;sql queries | queries files&gt;*
</pre>
On Unix:
<pre>
./queryDerby.sh [-h &lt;host&gt;] [-p &lt;port&gt;] [-usr &lt;usr&gt;] [-pwd &lt;pwd&gt;] [-standalone] [-d &lt;database&gt;] [-createdb] [-nocreatedb] [-repeat &lt;count&gt;] [-tab] [-csv] [-raw] [-csvraw] [-quiet] [-batchprefix &lt;prefix sql&gt;] &lt;sql queries | queries files&gt;*
</pre>
<p>The parameters are defined as follows:</p>
<table class="data">
<thead>
<tr>
<th>Parameter</th>
<th>Default</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
-h &lt;host&gt;
</td><td>
localhost
</td><td>
The host of the GaianDB node to connect to.
</td>
</tr>
<tr>
<td>
-p &lt;port&gt;
</td><td>
6414
</td><td>
The port of the GaianDB node to connect to.
</td>
</tr>
<tr>
<td>
-usr &lt;usr&gt;
</td><td>
gaiandb
</td><td>
The username to use to connect.
</td>
</tr>
<tr>
<td>
-pwd &lt;pwd&gt;
</td><td>
passw0rd
</td><td>
The password to use to connect.
</td>
</tr>
<tr>
<td>
-standalone
</td><td>
<i>N/A</i>
</td><td>
Connect to Derby directly using the Embedded driver.<br />
This option is incompatible with any host or port setting.<br />
Subsequently setting the -h or -p parameter will invalidate the setting of this parameter.
</td>
</tr>
<tr>
<td>
-d &lt;database&gt;
</td><td>
gaiandb
(or gaian&lt;port&gt;db, if -p is specified)
</td><td>
The database to connect to.
</td>
</tr>
<tr>
<td>
-createdb
</td><td>
<i>N/A</i>
</td><td>
On connect, create the database if it doesn't already exist (see -d for which database this will be).<br />
<br />
Note: If a database is created, the default schema will not have been created yet and the shorthand GaianDB views &amp; stored procedures will not be defined. 
</td>
</tr>
<tr>
<td>
-nocreatedb
</td><td>
<i>N/A</i>
</td><td>
On connect, do NOT create the database if it doesn't already exist (see -d for which database this will be).
</td>
</tr>
<tr>
<td>
-repeat &lt;count&gt;
</td><td>
<i>N/A</i>
</td><td>
Specifies the number of times any query will be immediately re-issued. i.e. if you set '-repeat 3', then any query you issue will be run 3 times in a row.
</td>
</tr>
<tr>
<td>
-tab
</td><td>
<i>N/A</i>
</td><td>
Output query results in the default table format which is with table headings and vertical line separators.<br />
<b>This is the default.</b>
</td>
</tr>
<tr>
<td>
-csv
</td><td>
<i>N/A</i>
</td><td>
Output query results in a CSV (comma-separated-values) format.
</td>
</tr>
<tr>
<td>
-raw
</td><td>
<i>N/A</i>
</td><td>
Output query results as raw data (space-separated) format, with no information or headers.
</td>
</tr>
<tr>
<td>
-csvraw
</td><td>
<i>N/A</i>
</td><td>
Output query results as raw data in CSV (comma-separated-values) format, with no information or headers.
</td>
</tr>
<tr>
<td>
-quiet
</td><td>
<i>N/A</i>
</td><td>
No output to stdout.
</td>
</tr>
<tr>
<td>
-batchprefix &lt;prefix sql&gt; 
</td><td>
<i>N/A</i>
</td><td>
Specifies an SQL fragment to insert as the prefix to every SQL query batch file passed in on the command line.<br />
See <a href="#contents340">here</a> for more details.
</td>
</tr>
<tr>
<td>
&lt;sql queries | queries files&gt;*
</td><td>
<i>N/A</i>
</td><td>
A space-separated list of SQL queries, or files containing SQL queries, to run immediately on connection.<br />
See <a href="#contents340">here</a> for more details.
</td>
</tr>
</tbody>
</table>

<p>In addition to specifying these parameters when launching 'queryDerby', all flag switches (-h, -p, -usr, etc.) may be entered in the CLP at any time and will take effect immediately.<p>

<p>As an example, this makes it possible to manage multiple GaianDB nodes from a single window (simply by switching between them using -h and -p). As a special case, note that specifying the -p flag will automatically change the database name to 'gaiandb<port>' (as this is the default database name for a GaianDB node running on a different port). To override this, you can use the '-d' flag to explicitly specify which database name to use.<p>

<p>Whenever query execution fails (for example, because the Derby connection was lost after we changed the 'port' connection value with the '-p' option), the CLP attempts to reconnect automatically: <p>

<pre>
sql>
sql> -p 6415
sql>
sql> select * from LT0_P

Attempting to re-connect...

Connecting to GAIAN server using url: jdbc:derby://localhost:6415/gaiandb6415;create=false, usr: gaiandb...

Connection attempt succeeded, Re-run query [n/other] ?
</pre>

<p>This is also the case when any Exception occurs during query execution. Although in this case, after recycling the connection, the CLP also automatically runs the stored procedure: <code>call listwarnings()</code> to retrieve and display any recently raised server warnings.</p>

<br />

<a name="contents340">&nbsp;</a>
<p>When launching 'queryDerby', you can pass in a list of SQL queries and/or files containing multiple SQL statements to execute immediately. For example:</p>

On Windows:
<pre>
queryDerby.bat "select * from LT0;select * from LT0" FileWithSQLQueriesToTest.sql
</pre>
On Unix:
<pre>
./queryDerby.sh "select * from LT0;select * from LT0" FileWithSQLQueriesToTest.sql
</pre>
<p>Where the file 'FileWithSQLQueriesToTest.sql' contains:</p>
<pre>
select * from LT0;
select * from LT0;
</pre>
<p><b>Note:</b> When creating a batch file of SQL statements, each new statement should be on it's own line and suffixed with ';'.</p>
<p>This example executes the query 'select * from LT0' four times.</p>

<p>As well as this, a 'batchprefix' SQL fragment value can be passed in using the '-batchprefix' flag. This fragment of SQL is prefixed to all SQL statements to be executed from batch files passed in when invoking 'queryDerby'. <b>Note:</b> this <b>only</b> applies to the queries passed in in batch files.</p>

<br/><hr><h3><a name="contents145">Issuing Distributed SQL Queries</a></h3>
<p>A GaianDB distributed query is a query against a logical table (or a <a href="#contents341">distributed sub-query</a>) defined on multiple nodes in the network.</p>

<p>Each of the GaianDB nodes may have a different underlying data source for the logical table (e.g. an RDBMS, an excel file, etc.), however they all share the same logical table definition and so they can be queried consistently.</p>

<p>When the query is executed, it is 'distributed' to each GaianDB node in the network by forwarding the predicates against the queried columns. Each node then maps these locally to the underlying physical types of the data sources attached to the logical table, and performs the query.</p>

<p>For a GaianDB node to be included in the distributed query, it's local logical table definition must have matching data types for all the columns involved in the distributed query (based on the logical table definition of the original querying node). However, there is some flexibility, as columns don't have to be present (in which case a null value will be returned) and extra columns will be ignored.</p>

<p>Results from each of these distributed queries are then union'ed together as they are fed back to the querying node in the network.</p>
<br />
<p>Here is the syntax for referring to a logical table that can be used in place of any table identifier in SQL:</p>
<pre>new com.ibm.db2j.GaianTable('&lt;Logical Table Name&gt;'[, '&lt;Logical Table Arguments&gt;']) &lt;Alias Identifier&gt;</pre>

<p>For example:</p>
<pre>select * from new com.ibm.db2j.GaianTable('LT0') LT0</pre>

<p>Or, to query against a logical table 'ACCOUNTS', requesting <a href="#contents234">provenance columns</a>:</p>
<pre>select * from new com.ibm.db2j.GaianTable('ACCOUNTS', 'with_provenance') T</pre>
<p><b>Note:</b> The Alias Identifier should be included so that the nested query can be uniquely referenced. This is standard SQL best practice and is useful in cases where you wish to join multiple tables/queries and need to refer to each of the tables'/sub-queries' columns uniquely. For example, if two queries, aliased as Q1 & Q2 respectively, both returned the column FIRSTNAME, you could reference each queries' column uniquely by using Q1.FIRSTNAME and Q2.FIRSTNAME.</p>
<p>A full list of <a href="#contents321">Logical Table Arguments</a>is described later in the document.</p>
<br />

<p>For convenience, GaianDB automatically maintains some system managed views to query a GaianDB logical table. For a logical table LT0, the list of all managed views is:</p>

<table class="data">
<thead>
<tr>
<th>View</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>LT0</td>
<td>Propagated logical table - represents the logical table over all GaianDB nodes</td>
</tr><tr>
<td>LT0_0</td>
<td>Just local (not propagated) - represents the logical table on the local GaianDB node only</td>
</tr><tr>
<td>LT0_P</td>
<td>Propagated, with <a href="#contents234">provenance columns</a></td>
</tr><tr>
<td>LT0_X</td>
<td>Explain query - see <a href="#contents270">Explain Queries: Getting and showing the route of a query</a> for more information.</td>
</tr><tr>
<td>LT0_XF</td>
<td>Explain query to file graph.dot - see <a href="#contents270">Explain Queries: Getting and showing the route of a query</a> for more information.</td>
</tr>
</tbody>
</table>

<p>For example, to retrieve all rows from logical table LT0 for data sources federated by the local GaianDB node only, use the SQL:</p>

<pre>select * from LT0_0</pre>
  
<p>Note that these views are updated automatically when a change to the GaianDB configuration for the logical table is made.</p>

<hr><h3><a name="contents341"><b>Distributed Sub-queries or Pushing query processing to each node</b></a></h3>

<p>Another, much more powerful, approach to distributed querying with GaianDB is to use distributed sub-queries. In this case, you specify a sub-query (nested query) that is 'distributed' to each GaianDB node, run locally and the results are then union'ed together as they are fed back to the original querying node in the network. The results are then queried by the querying node to get the final result set.</p>
<p>As an example, the following statement defines a query to select everything from ('select * from') the results of the 
distributed sub-query 'select * from example':</p>
<pre>select * from new com.ibm.db2j.GaianQuery('select * from example') Q</pre>
<p>In this case, the sub-query will be distributed to each GaianDB node in the network and will be executed 
against the local derby RDBMS that each GaianDB node rests on; querying a physical table named 'example', 
under the schema 'gaiandb' of Derby database 'gaiandb' (as this is the default behaviour).</p>
<p><b>Note:</b> The 'example' table is not defined in a default GaianDB installation. If you wish to create it, 
please refer to the <a href="WorkedExamples.html#contents2">Worked Examples</a>.</p>
<br />

<p>Here is the syntax for referring to a distributed sub-query that can be used in place of any table identifier in SQL:</p>
<pre>new com.ibm.db2j.GaianQuery('&lt;Nested SQL Query&gt;'[, '&lt;Logical Table Arguments&gt;'[, '&lt;Nested Query Arguments&gt;']]) &lt;Alias Identifier&gt;</pre>
<p><b>Note:</b> The Alias Identifier should be included so that the nested query can be uniquely referenced. This is standard SQL best practice and is useful in cases where you wish to join multiple tables/queries and need to refer to each of the tables'/sub-queries' columns uniquely. For example, if two queries, aliased as Q1 & Q2 respectively, both returned the column FIRSTNAME, you could reference each queries' column uniquely by using Q1.FIRSTNAME and Q2.FIRSTNAME.</p>
<p><b>Note:</b> any single quotes (') appearing inside Nested SQL Queries must be escaped with another single quote ('').</p>
<p>A full list of <a href="#contents321">Logical Table Arguments and Nested Query Arguments</a> is described later in the document.</p>
<br />

<p>By default, the nested query will be executed against the local Derby database that an GaianDB node runs on (as in the example above). 
However, the nested query can also target a particular <a href="#contents342">SOURCELIST</a>; which is a way of targeting an abstracted list of 
exposed data sources individually on every node. In this case, the query is 'passed on' to each exposed data source for it to execute. 
See the distributed query options section for more information. As an example, the following query targets a <a href="#contents342">SOURCELIST</a> 
called TOYS:</p>
<pre>select * from new com.ibm.db2j.GaianQuery('select * from toysales', 'with_provenance', 'SOURCELIST=TOYS') Q</pre>
<p><b>Note:</b> the resources referenced in this example are not setup in a default GaianDB configuration and so the example will not work
out of the box.</p>

<p>The nested query can also reference a logical table, as follows:</p>
<pre>select * from new com.ibm.db2j.GaianQuery('select * from new com.ibm.db2j.GaianTable(''LT0'', ''maxDepth=2'') T') Q</pre>
<p>In this case, the query will be distributed out from the local Derby GaianDB node to every node in the network and each of them will query the logical table 'LT0' out to a depth of 2. </p>

<p><b>Note:</b> it would make no sense to specify a <a href="#contents342">SOURCELIST</a> in this case as the sub-query contains a GaianDB construct (GaianTable()) which will not be meaningful to exposed data sources other than the GaianDB nodes themselves.</p>

<br />
<p>Here are some useful tips on propagating queries using GaianQuery():</p>

<ul>
<li>To push query processing to each node, i.e. to make all nodes query their local federated data sources and return their own timestamps and provenance information, you can reference the managed view with suffix '_0'. For example: 
<pre>select * from new com.ibm.db2j.GaianQuery('select CURRENT_TIMESTAMP TS, LOCATION, MISC from LT0_0', 'with_provenance') Q</pre>

This makes every node query its own local federated sources for LT0 columns LOCATION and MISC and compute its own local timestamp.
The provenance columns are added to the results on every node.
</li>
<br/>
<li>One way of propagating a function without needing a logical table is using a dummy system physical table.
A dummy table tends to have a single record and is used for selecting when you're not actually interested in the data, but instead want the results of some system function in a select statement.
The default dummy table on Derby is 'sysibm.sysdummy1' and, as an example, it can be used to return the timestamp from each node in the network as follows:
<pre>select * from new com.ibm.db2j.GaianQuery('select current_timestamp ts from sysibm.sysdummy1', 'with_provenance') Q</pre>
</li>
<br/>
<li>If a nested query contains a distributed table or query, it may only reference the provenance, explain or constant columns if these are renamed within the nested query.
This is because otherwise they would be seen as potential duplicates with the columns defined by the outer GaianQuery().

e.g. this is invalid:
<pre>select * from new com.ibm.db2j.GaianQuery('select CURRENT_TIMESTAMP TS, GDB_NODE from LT0_P') Q</pre>

but this is OK:
<pre>select * from new com.ibm.db2j.GaianQuery('select CURRENT_TIMESTAMP TS, GDB_NODE NESTED_PROVENANCE from LT0_P') Q</pre>
<b>Note:</b> here we use the managed view 'LT0_P' which uses suffix '_P' to designate logical table 'LT0' with <a href="#contents234">provenance columns</a>.
</li>
</ul>

</ul>
<br />

Using distributed sub-queries is a powerful mechanism that provides the opportunity to perform many complex operations.
As a final example of this, note here how it allows non-aggregate functions on partitioned data to be pushed down to all nodes in the network.
The GaianQuery below targets local data sources of logical table LT at each node, using LT's view having the &quot;_0&quot; suffix (i.e. restricted to depth 0).
This trick allows us to independently compare at each node the msg_received time values in LT at that node with it's own individual local system time
and only retrieve data that was generated in the last 10 minutes.
<pre>select * from new com.ibm.db2j.GaianQuery('select * from LT_0 where msg_received &gt; {fn TIMESTAMPADD(SQL_TSI_MINUTE, -10, current_timestamp)}') GQ</pre>


<p>For more examples on issuing distributed queries, please refer to <a href="WorkedExamples.html">WorkedExamples.html</a>.</p>
<br/>

<hr><h3><a name="contents217">Listing server warnings</a></h3>

<p>To list all recently raised warnings on all GaianDB nodes in the network, run the GaianDB stored procedure <code>call listwarnings()</code>:<p>
<pre>
sql&gt; call listwarnings()
call listwarnings()
=========================================================================================================================================================================
GDB_NODE            |TSTAMP                    |WARNING        |
=========================================================================================================================================================================
Patrick_linux       |2011-10-25 10:56:37.827   |Failed JDBC Connection attempt in 189391 ms for: jdbc:derby://x.x.x.x:6420/gaiandb6420;create=true, cause:Thread.run:736 -&gt; r.run:31 -&gt; r.a:25 -&gt; DriverManager.getConnection:358 -&gt; DriverManager.getConnection:322 -&gt; ClientDriver.connect:-1 -&gt; SqlException.getSQLException:-1 -&gt; SQLExceptionFactory40.getSQLException:-1:: java.sql.SQLNonTransientConnectionException: java.net.ConnectException : Error connecting to server x.x.x.x on port 6420 with message Connection timed out.|
=========================================================================================================================================================================
Fetched 1 rows. Total Time: 2225ms (Execution Time: 2007ms)
sql&gt;
</pre>

<p>This procedure is automatically called when using the command line processor 'queryDerby.bat' if an exception occurs.</p>
<p><b>Note:</b> warnings are cleared from memory on all nodes once retrieved. However they will still appear in the log files (if logging is enabled).</p>
<p>This is a convenience procedure, which is better suited to managed GaianDB clusters.</p>

<br/>

<hr><h3><a name="contents344">Dashboard Graphical User Interface</a></h3>
<p>A graphical user interface client utility (also known as the dashboard) is also provided with the GaianDB installation.
You can find the dashboard in the installation directory and it can be launched by running 'dashboard.bat' on Windows and 'dashboard.sh' on Unix.</p>
<p>As with the CLP, the dashboard can be used to run queries on GaianDB and also to issue GaianDB stored procedures; 
however it allows you to do this and view the results in a more consumable manner. It also has a number of additional features that allow you to
view the current network topology and current &amp; historical metrics for nodes in the network.</p>

<p>After starting the dashboard, this is what you should see:<br/><br/>
<center>
<TABLE class='image'>
   <TR class='image'>
   <TD class='image'><img src="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/s_dashboard-connect.png"></TD></TR>
   <TR class='image'>
     <TD class='image' align='center'>Fig. 5 - Dashboard connection page</TD></TR>
</TABLE>
</center>

<p>If you want to connect to GaianDB nodes on other machines, change the following:
<ul>
<li>Hostname field for the hostname of the machine you know the node is on.</li>
<li>Port field if needed.</li>
<li>If you have changed the port field you need to change the Dabatase field as well. For example, a Gaian node running on port 7000 uses the Database name: gaiandb7000.</li>
</ul>

<p>You can view the Gaian nodes topology in the Network Topology tab, this what you should see:<br/><br/>
<center>
<TABLE class='image'>
   <TR class='image'> <TD class='image'><img src="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/s_dashboard-topo.png"></TD></TR>
   <TR class='image'> <TD class='image' align='center'>Fig. 6 - Dashboard Network Topology page</TD></TR>
</TABLE>
</center>

<p>And finally you can go to the SQL Queries page and issue commands, call procedures and call functions just as you would from the QueryDerby command line.
<center>
<TABLE class='image'>
   <TR class='image'>
     <TD class='image'><img src="https://github.com/gaiandb/gaiandb/blob/master/doc/UserDocs/images/s_dashboard-query.png"></TD></TR>
   <TR class='image'>
   <TD class='image' align='center'>Fig. 7 - Dashboard Network Topology page</TD></TR>
</TABLE>
</center>

<br />

<hr><h2><a name="contents175">Configuration</a></h2>

<p>A GaianDB node's configuration can be modified either by using the management API stored procedures or by editing the config
file ('gaiandb_config.properties') directly. Configuration updates are effective dynamically when applied and there is no need to restart the GaianDB server at any point. Neither is it necessary to pause issuing queries when applying a configuration update.</p>

<hr><h3><a name="contents343">Configuration file</a></h3>
<p>
You can edit a GaianDB node's configuration by editing it's configuration file directly. By default, a GaianDB node looks for a file named 'gaiandb_config.properties' in the current working directory. However you can specify an alternative configuration file by specifying the '-c' parameter. For more information, please refer to <a href="#contents115">GaianDB node usage</a></p>

<hr><h4><a name="contents180">Configuration file: Properties for Logical Tables, their Data Sources and associated Connections</a></h4>

<p>The following example shows how to define a logical table LT0, which has two columns named 'ENTITY' &amp; 'ID' and is a federation of 2 physical data sources:
<ol>
<li>A CSV flat file named 'wc_stat.dat' - with it's column 'COLUMN2' mapped to 'ENTITY' and it's column 'COLUMN1' mapped to 'ID'.</li>
<li>A DB2 table named 'EMPLOYEE' - with it's column 'FIRSTNME' mapped to 'ENTITY' and it's column 'ID' mapped to I'D'.</li>
</ol>
</p>

<pre>
#--------- Logical table definition
LT0_DEF=ENTITY VARCHAR(30), ID INTEGER
#----------- Data Source 0: file definition ------------
LT0_DS0_VTI=com.ibm.db2j.FileImport
LT0_DS0_ARGS=C:/MyFiles/wc_stat.dat
LT0_DS0_C0=COLUMN2
LT0_DS0_C1=COLUMN1
#----------- Data Source 1: DB2 table definition--------
LT0_DS1_CONNECTION=DB2 EMPLOYEE
LT0_DS1_C0=FIRSTNME
LT0_DS1_C0=ID
#----------- DB2 table connection definition--------
DB2_DRIVER=com.ibm.db2.jcc.DB2Driver
DB2_URL=jdbc:db2://localhost:50000/sample
DB2_USR=myuser
DB2_PWD=mypasswd
</pre>

<p>
The first part defines the logical table:
</p>

<pre>
#--------- Logical table definition
LT0_DEF=ENTITY VARCHAR(30), ID INTEGER
</pre>

<p>Specifying the name of the logical table (LT0), suffixed with "_DEF", and it's columns and their associated data types.</p>
<p><b>Note:</b> When <a href="#contents145">issuing distributed SQL queries</a>, the logical table definitions must match between Gaian Nodes for them to be treated as the same one. More specifically, a query against a logical table LT0 originating from a GaianDB node N0 will query all nodes that have a definition for LT0 which 'matches' the one on N0. In the context of GaianDB, a logical table definition is said to match another definition if they share the same name and every column name they have in common has an identical type definition. Querying columns that do not exist in a table definition on a Gaian Node will result in null values being returned for that column and node and extra columns will be ignored.
</p>

<p>
You may also define specific attributes of a logical table - examples of currently supported ones are below:
</p>

<pre>
#--------- LT0 Logical table definition
LT0_DEF=ENTITY VARCHAR(30), ID INTEGER

#--------- LT0 Constant columns - these are described in a later section. Essentially, the constant is a 3rd argument after the column name and type.
LT0_CONSTANTS=OFFICE VARCHAR(50) MY_OFFICE_NAME

</pre>

<p>We then define the data sources that the logical table federates. The data sources of a logical table are identified using the "_DS" suffix label, which itself is followed by the data source ID (e.g. "0") and then a further suffix to identify a particular property of the data source (e.g. "_VTI").</p>

<p>There are currently 2 supported data source types:</p>

<ol>
<li>Virtual Table Interface (VTI) data sources (such as the FileImport data source) - In this case, the data source suffix "_VTI" is used and the resulting property identifies a Virtual Table Interface Java class which acts as a wrapper for the data source. This is an extensible model, so any data source type could potentially be federated. In this example, we use a FileImport VTI to wrapper a flat CSV file.
<pre>#----------- Data Source 0: file definition ------------
LT0_DS0_VTI=com.ibm.db2j.FileImport
LT0_DS0_ARGS=C:/MyFiles/wc_stat.dat
LT0_DS0_C0=COLUMN2
LT0_DS0_C1=COLUMN1</pre>

<p>
The table schema of a VTI extending AbstractVTI (such as FileImport) is based on the following rules:
<ol>
<li> If the VTI implements a getMetaData() method, the GaianResultSetMetaData object resulting from this takes precedence.
Note this can be based on properties passed to the VTI constructor, which will hold the string specified against property &lt;LTNAME&gt;_DS&lt;DSNAME&gt;_ARGS
in the gaiandb_config.properties file.</li>
<li> Next, AbstractVTI will choose a schema resolved from a static property for the VTI having the "schema" suffix, i.e. "&lt;VTI_class_name&gt;.schema".</li>
<li> Next, and if the VTI is invoked as a data source of a logical table (rather than directly by Derby), AbstractVTI will resolve the schema based
on property &lt;LTNAME&gt;_DS&lt;DSNAME&gt;_SCHEMA.</li>
<li> Next, and if the VTI is invoked as a data source of a logical table (rather than directly by Derby), AbstractVTI will resolve the schema based
on the logical table definition.</li>
Note that in all cases where the VTI is invoked as a logical table data source, columns will be mapped by name to the logical table ones 
unless you specify the option to map columns by posisiton, e.g: LT0_DS0_OPTIONS=MAP_COLUMNS_BY_POSITION
</p>
</ol>

</li>

<li>RDBMS data sources (such as DB2, Oracle, etc) - In this case, the suffix used to define the data source type is "_CONNECTION", and the resulting property (e.g. "LT0_DS1_CONNECTION") is assigned an RDBMS connection identifier (e.g. "DB2") and also optionally a physical table name that exists under the RDBMS database associated with that identifier (e.g. "EMPLOYEE").
<pre>
#----------- Data Source 1: DB2 table definition--------
LT0_DS1_CONNECTION=DB2 EMPLOYEE
LT0_DS1_C0=FIRSTNME
LT0_DS1_C0=ID
</pre>


<p>Finally, an RDBMS connection identifier (e.g. "DB2") should have 4 associated properties defined using the 4 suffixes: "_DRIVER", 
"_URL", "_USR" and "_PWD". Between them, these 4 properties identify the specific RDBMS database to federate:
</p>

<pre>
#----------- DB2 table connection definition--------
DB2_DRIVER=com.ibm.db2.jcc.DB2Driver
DB2_URL=jdbc:db2://localhost:50000/sample
DB2_USR=myuser
DB2_PWD=mypasswd
</pre>
</li>
</ol>

There are also some additional options that can be set on a per datasource basis, by setting the <b>&lt;DATASOURCEID&gt;_OPTIONS</b> parameter:<br /><br />
	<ul>
		<li><b>MAP_COLUMNS_BY_POSITION</b>:<p/>Perform default column mapping by position for this data source (rather than by name).
		This is useful when you know that the columns in the data source table are ordered the same as the columns of the parent logical table's definition.
		In contrast, when mapping columns by name, GaianDB searches for matching column names in the underlying data source for each logical table column.
		Note that both column mapping policies can be overridden for any given column by using a specific mapping. 
		<pre>&lt;DSID&gt;_OPTIONS=MAP_COLUMNS_BY_POSITION</pre>
		</li>
		<li><b>DOUBLE_QUOTED_COLUMNS</b>:<p/>*NOTE* THIS OPTION IS NOW REDUNDANT: IT WILL BE IGNORED.<p/>
		GaianDB now automatically recognises non-ordinary identifers or identifiers having lower case characters and wraps them in delimiter characters
		(escaping nested delimiters too) when necessary to query them. This means any column name from supported RDBMS providers (and most others too)
		can be loaded and queried.
		<p/>
		<li><b>Notes on handling of columns having special characters with different RDBMS providers, e.g. MySQL or MSSQLServer:</b><p/>
		GaianDB will automatically use the correct delimiter chars to wrap delimited identifiers when it queries any of its supported RDBMS providers.
		<p/>FYI: Most RDBMS providers use the double-quote (") as an identifier delimiter character. However, MySQL uses the 
		back-quote character (`) as default delimiter, and MSSQLServer delimits identifiers having special characters with square brackets, e.g: [O'Ne@l].
		With both of these providers, double quoted columns are actually interpreted as strings rather than column names.
		Note: You may choose to start MySQL in ANSI mode, which makes it interpret *both* back and double quotes as identifier delimiters:
		<pre>./mysqld-nt.exe --ansi --standalone &</pre>
		For more information on RDBMS provider behaviours with respect to this, refer to:
		<a href="http://doc.ispirer.com/sqlways/Output/SQLWays-1-035.html">http://doc.ispirer.com/sqlways/Output/SQLWays-1-035.html</a>
		</li>
	</ul>
	
<hr><h4><a name="contents209">Configuration file: Global System properties and identifiers</a></h4>
<p>These properties control the general behaviour of a GaianDB node. These system properties, like all others, are dynamic;
therefore they may be changed while the associated GaianDB node is running and their new values will be used from the next query.</p>

<table class='data'>
  <thead>
    <tr>
      <th><b>Property</b></th>
      <th><b>Default</b></th>
	  <th><b>Description</b></th>
    </tr>
  </thead>
  <tbody>
	  <tr>
		<td><b>LOGLEVEL</b></td>
		<td>NONE</td>
		<td>The level of logging to use. This can only be one of: [NONE, LESS, MORE, ALL].<br />
		If NONE, then no logging is performed. Otherwise logging is performed to a file in the current working directory. This file will be named 'gaiandb.log' or  'gaiandb&lt;port&gt;.log' if the GaianDB node is not running on the default port (6414).<br /><br />
		This can be set as an argument when launching a GaianDB node with 'launchGaianServer.bat' in which case
		it will be fixed to this value until the node is restarted. Otherwise the value defined in the properties file will be used, or it will default to NONE.<br /><br />
		Try to avoid using 'ALL' when processing a heavy query load.</td>
	  </tr>
	  <tr>
		<td><b>LOGFILE_MAX_SIZE_MB</b></td>
		<td>100MB</td>
		<td>
		The maximum size (in MegaBytes) for the log file according to your system.
		</td>
	  </tr>
	  <tr>
		<td><b>DISCOVERY_PORT</b></td>
		<td>7777</td>
		<td>The port used to perform autonomic GaianDB node discovery.</td>
	  </tr>
	  <tr>
		<td><b>DISCOVERY_IP</b></td>
		<td>230.255.255.255</td>
		<td>Use this variable to define a broadcast mask or multicast group address used to discover other reachable
		GaianDB nodes. When this variable is not defined (i.e. when its value is null), the default MULTICAST group address 230.255.255.255
		is used. When the variable is set to an empty string (i.e. ''), GaianDB node discovery will be disabled.<br /><br />
		Broadcast messages can only reach machines within the domains which the local machine is itself a member of. Subnet broadcasts may reach further.
		Multicast messages may propagate beyond domain gateways if these were set up specifically for that purpose.<br /><br />
		For example, the DISCOVERY_IP variable may be used as:
		<ul>
		<li>A broadcast mask address: e.g. 255.255.255.255 for all machines in the local domains,
		  or 9.255.255.255 for all machines in the local domains with a 9.x.x.x address.</li>
		<li>A multicast group address to seek out all nodes that also use that group ip address.
		  To use multicast, use a common group address from the range 224.0.0.1 to 239.255.255.255.
		  <b>Note:</b> if the variable is not defined GaianDB will by default be using multicast address 230.255.255.255</li>
		<li>A unicast (1-to-1 broadcast) server address to only discover one potential node at that address.
		  <b>Note:</b> unicast messages are propagated on by domain gateways.</li>
		</ul></td>
	  </tr>
	  <tr>
		<td><b>MULTICAST_INTERFACES</b></td>
		<td><i>Default network interface only</i></td>
		<td>This property only applies if DISCOVERY_IP designates a Multicast address, and it identifies 
		the interfaces over which multicast discovery will be performed.
		<br /><br />
		The property value must be a comma separated list of the IP addresses that the local host has assigned for any of the network
		interfaces that should be used.</td>
	  </tr>
	  <tr>
		<td><b>DISCOVERY_GATEWAYS</b></td>
		<td><i>None</i></td>
		<td>A comma separated list of IP addresses, each of which identifies the host of a GaianDB node
		which we want to use as a Discovery Gateway to discover other nodes.
		<br /><br />
		<b>Note:</b> this is different to creating a <a href="#contents215">hard-wired gateway connection</a>
		to another node to bridge two GaianDB networks. A Discovery Gateway simply forwards on the node discovery request from one
		GaianDB node to another GaianDB node; the two nodes then establish a connection directly.
		Further traffic does not flow through the discovery gateway.
		This is useful in situations where two (or more) nodes may be able to communicate, but cannot automatically discover each other
		due to restrictions on the network; and where it is possible to setup a Discovery Gateway node to act as a discovery intermediary.
		</td>
	  </tr>
	  <tr>
		<td><b>MIN_DISCOVERED_CONNECTIONS</b></td>
		<td>2</td>
		<td>The number of GaianDB nodes which this GaianDB node will attempt to connect itself to
		and maintain a two-way connection with. Beyond that number it may still accept connection requests from other nodes but will
		not initiate any more itself.<br />This setting is set to 2 by default in the configuration file, which is the expected value to grow the
		network of GaianDBs in an optimal way (to achieve a balance for reducing bottlenecks, minimising network diameter and avoiding
		fragmentation).</td>
	  </tr>
	  <tr>
		<td><b>MAX_DISCOVERED_CONNECTIONS</b></td>
		<td>10</td>
		<td>The maximum number of GaianDB connections that a node will allow.</td>
	  </tr>
	  <tr>
		<td><b>ACCESS_HOSTS_PERMITTED</b></td>
		<td><i>Any</i></td>
		<td>Use this variable to define a comma-separated list of hosts which this GaianDB node will accept
	connections to and process queries from. Connections to other hosts will be disconnected and connection attempts from
	hosts that are not in the list will be rejected. When this variable is not defined (i.e. when its value is null), the GaianDB node
	will allow connections to any other node. When the variable is set to an empty string (i.e. ''), no connections are allowed.</td>
	  </tr>
	  <tr>
		<td><b>DISCOVERY_HOSTS</b> <i>(deprecated)</i></td>
		<td></td>
		<td>Deprecated property name, now replaced with ACCESS_HOSTS_PERMITTED (see above).</td>
	  </tr>
	  <tr>
		<td><b>ACCESS_HOSTS_DENIED</b></td>
		<td><i>None</i></td>
		<td>Use this variable to define a comma-separated list of hosts which this GaianDB node will
	refuse to connect to and will not process queries from. Connections to denied hosts will be disconnected and connection attempts from them will be rejected. 
	When this variable is not defined (i.e. when its value is null) or set to an empty string (i.e. ''), the parameter will have 
	no effect.
	<br /><br />
	<b>Note:</b> if a host is in both the ACCESS_HOSTS_PERMITTED and ACCESS_HOSTS_DENIED lists then it will be DENIED.</td>
	  </tr>
	  <tr>
		<td><b>ACCESS_CLUSTERS</b></td>
		<td><i>No restrictions</i></td>
		<td>Use this variable to define a comma-separated list of private IDs identifying private clusters 
	which this GaianDB node belongs to. Other nodes which do not have a cluster ID matching one of these will then not be able to
	connect or send queries to this node.
	<br /><br />
	This is a way of partitioning your GaianDB into private clusters, so that certain nodes can only 'see' and interact with the other nodes in their cluster.</td>
	  </tr>
	  <tr>
		<td><b>DEFINED_GAIAN_CONNECTIONS</b></td>
		<td><i>No hardwired connections</i></td>
		<td>Use this variable to define a comma-separated list of identifiers for hard-wired connections to create to other Gaian databases, when these
	cannot be automatically discovered (for example, if they are in a separate domain or in a network that doesn't support IP Multicast).
	<br /><br />
	Each connection identifier 'XXX' refers to 4 other properties which must also be defined and which designate the JDBC connection details for the Gaian
	connection: XXX_DRIVER, XXX_URL, XXX_USR and XXX_PWD.
	<br/><br/>
	For example:
	<pre>DEFINED_GAIAN_CONNECTIONS=CONN1

CONN1_DRIVER=org.apache.derby.jdbc.ClientDriver
CONN1_URL=jdbc:derby://conn1host/gaiandb;create=true
CONN1_USR=gaiandb
CONN1_PWD=conn1passw0rd</pre>
	
	For more information please refer to <a href="#contents215">Hard-wiring connections between GaianDB nodes (incl setting up gateways)</a>.
	</td>
	  </tr>
	  <tr>
		<td><b>MAX_PROPAGATION</b></td>
		<td><i>None</i></td>
		<td>This controls the propagation depth of queries (i.e. how many other GaianDB nodes a query can propagate through the network to, from this GaianDB node). The configuration setting can be overridden using the <a href="#contents321">'maxDepth'</a> argument in the GaianDB SQL query.
		<br /><br />
		If no value is specified (neither in the query nor in config) or if a negative value is used, then there will be no max propagation constraint (i.e. queries will flood the whole network).</td>
	  </tr>
	  <tr>
		<td><b>MAX_POOLSIZES</b></td>
		<td>10</td>
		<td>This controls the maximum size of the pool of concurrent 'transport layer' connections that a GaianDB node can have with each 'logical' connection to either:
		<ul>
			<li>Another GaianDB node</li>
			<li>A data source of this node</li>
		</ul>
		The default value for this parameter is 10, meaning that a node will not cache connections beyond a concurrent workload of 10 simultaneous queries.
		It will have to re-acquire connections for each new query beyond this limit.
		For example, in a logical connection between two GaianDB nodes, there can be (by default) a maximum of 10 concurrent transport layer connections.
		However, if one of these nodes is also in contact with a third node, it would also potentially cache 10 other connections to this other node;
		meaning that the node in question would actually cache up to a maximum of 20 concurrent transport layer connections overall.
		</td>
	  </tr>
	  <tr>
		<td><b>MAX_INBOUND_CONNECTION_THREADS</b></td>
		<td>1000</td>
		<td>The maximum number of threads GaianDB accepts as client connections.
		If this limit is reached, then additional connection attempts will wait (i.e. hang) until a client connection becomes available or
		until the JDBC connection-timeout is reached (approx 2.5 minutes).<p/>
		Note: The number of inbound connection threads into a node will be closely tied to the sum of pool sizes on nodes that are connected to it (these will be capped by
		their MAX_POOLSIZES parameter) plus the number of client application connections against the node.<p/>
		For workload management purposes, query throughput is preferably controlled by adjusting the MAX_POOLSIZES parameter rather than MAX_INBOUND_CONNECTION_THREADS
		because, crucially, it will simply cause queries to be rejected (returning no data) when its limit is reached rather than make them hang.
		Specifically, when multiple queries reaching a node all find themselves concurrently having to make a new connection attempt against another 
		node (due to a connection pool being empty), only 1 attempt will be permitted at a time, thus delaying surplus queries to the point where they are rejected.
		</td>
	  </tr>
	  <tr>
		<td><b>GAIAN_NODE_USR</b></td>
		<td>gaiandb</td>
		<td>Set this to override the default system user (and schema) in order to safeguard your configuration against
	updates from others. This describes	the user (and schema) for the physical derby database that supports the local Gaian node.
	It is used when creating or accessing the local database and schema. 
	Changing this property only takes effect when the system is restarted.
	IMPORTANT: You need to have a corresponding entry defined for this user in derby.properties, where you specify the password for this Derby user:
<pre>
# This derby property enforces user authentication:
derby.connection.requireAuthentication=TRUE
 
# This is the default user/password setting for GAIAN_NODE_USR 'gaiandb':
derby.user.gaiandb=passw0rd
</pre>
	Alternatively, if you just wish to set up a separate database schema within the local Gaian node, it is better to define a separate
	user id and associated password (alongside the Gaian one) in file 'derby.properties'.
	In order to reference the GaianDB stored procedure APIs from your new schema, you will then
	need to fully qualify their location relative to the 'gaiandb' schema, e.g. <code>call gaiandb.listlts()</code>.</td>
	  </tr>
	  <tr>
		<td><b>ALLOW_SQL_API_CONFIGURATION</b></td>
		<td>false</td>
		<td>This property allows configuration of this GaianDB node through the SQL API.
		The management API commands may be preferable to specifying everything in the configuration file as they perform error checking and often set multiple properties per command.
	<br /><br />
	Before you enable this property, you may wish to prevent other people from also modifying your configuration through the
	SQL API by setting your own GAIAN_NODE_USR user id property; and then its associated password in the derby.properties file.
	As an example, the password for user id 'gaiandb' in derby.properties is set like this: <code>derby.user.gaiandb=passw0rd</code>.
	<br /><br />
	For more information, please see the section on <a href="#contents177">Using the management API to apply configuration updates</a>.
	</td>
	  </tr>
	  <tr>
		<td><b>ALLOW_PROPAGATED_WRITES</b></td>
		<td>false</td>
		<td>This property allows propagated <a href="#contents145">sub-queries</a> containing <code>insert</code>/<code>update</code>/<code>delete</code>/<code>call</code> SQL
	operations to be executed on this GaianDB node.
	<br /><br />
	This can affect any of the data sources you expose through logical 
	tables. This will also allow remote management of this configuration file if property 
	'ALLOW_SQL_API_CONFIGURATION' is also set, and <b>regardless</b> of your node's user id and password; as the commands are propagated through the GaianDB network and executed locally.
	<br /><br />
	Set this property if you are happy to allow other nodes to change your data (and potentially also your node's configuration).</td>
	  </tr>
	  <tr>
		<td><b>GAIAN_CONNECTIONS_CHECKER_HEARTBEAT_MS</b></td>
		<td>5000</td>
		<td>This value (in milliseconds) is the maximum time GaianDB will wait to
	receive a response to a connection request or maintenance (keep-alive) message. Beyond that timeout, the GaianDB connection
	in question is assumed to be unavailable so it is dropped and its associated resources are reclaimed.</td>
	  </tr>
	  <tr>
		<td><b>LOCALDERBY</b></td>
		<td></td>
		<td>This is a hard-coded RDB connection identifier property which can be used as a shortcut to
	designate the local GaianDB Derby database connection, rather than having to create a separate one and having to
	specify DRIVER, URL, USR and PWD properties for it, as these are all known by the system. For example:
<pre>
LT1_DS0_CONNECTION=LOCALDERBY TABLE1
</pre>
	    </td>
	  </tr>
	  
	  <tr>
		<td><b>LOGICAL_TABLES_HAVING_BASIC_VIEWS_ONLY</b></td>
		<td></td>
		<td>This property is used for performance reasons - to instruct GaianDB to only create the basic views for a newly added logical table.
		Indeed view creation can take a long time if your application needs to create hundreds or thousands of logical tables.
		The 6 standard views normally created are: the basic one having the same name as the logical table, and then views with suffixes:
		_0,_1_P,_X and_XF, which designate: query to depth 0 (local node only), depth 1, with_provenance, explain and 'explain to file graph.dot'.
		Below is an example of how to set the property such that logical tables LTX and LTY only have the basic views (querying all nodes, with no extra data)
		created for them.
	
<pre>
LOGICAL_TABLES_HAVING_BASIC_VIEWS_ONLY=LTX,LTY
<!--
=>>>>>>>>>>>>>>>>>>>>>      NOT IMPLEMENTED:

#--------- LT0 view suffixes to be created. Various allowed combinations are listed below:
#LT0_VIEW_SUFFIXES=                     # Undefined (or commented out) - All 6 views will be created (as in the final example below)
LT0_VIEW_SUFFIXES=                      # No suffixes - only create the basic logical table view, named 'LT0'.
LT0_VIEW_SUFFIXES=_P                    # Create the basic view and the view having suffix '_P' (i.e. 'LT0_P'), to expose extra provenance columns. 
LT0_VIEW_SUFFIXES=_0,_1_P,_X,_XF        # Create the basic view and all 5 others: i.e:

<<<<<<<<<<<<<<<<<<<<<=		NOT IMPLEMENTED
--> 
</pre>
		</td>
	  </tr>
	  
	  
	  <tr>
		<td><b>SQL_RESULT_FILTER</b></td>
		<td>None</td>
		<td><a name="contents404"></a>
			This property designates a java policy class implementing the com.ibm.gaiandb.policyframework.SQLResultFilter interface.
			The class may also be an extention of abstract class com.ibm.gaiandb.policyframework.SQLResultFilterX which provides extended capabilities.
			The implementation class' role is to apply a filter on the result of queries executed on the node based on query context properties: 
			e.g: forwarding node, user credentials, queried logical table & assocatied data sources (including nodes where the query is next to be propagated to).
			This plugin interface also makes it possible to restrict query propagation or stop a query from being executed against a logical table or individual
			data sources. In order to identify and enable the plugin class, set this property in gaiandb_config.properties. Here's an example:
			<pre>SQL_RESULT_FILTER=com.ibm.gaiandb.policyframework.PolicyRowFilter</pre>
			To write your own result filter class, follow these steps:
			<ul>
				<li>Create a class which implements SQLResultFilter or extends abstract class SQLResultFilterX. The methods in these classes will be called
				at different points during the query life cycle. Each method has a double purpose: 1) to pass contextual information to the
				plugin relating to the query's current state and 2) to request an instruction or filtered update from the plugin to control query processing or modify
				the query results. To start with, you may wish to make each method print a simple log message and return true, -1 or null (this will let the
				query proceed as if there were no control instructions or filtering).				
				</li>
				<li>Configure GaianDB to load your plugin and call into it at runtime: For this you need to set the SQL_RESULT_FILTER property (as shown above)
				and you also need to add your plugin class path location (or encapsulating jar file name) to the GaianDB node's startup classpath,
				e.g, in launchGaianServer.bat: 
				<pre>SET CLASSPATH=%CLASSPATH%;C:\temp\TestFilter.jar</pre>
				</li>
				<li>Make modifications to your plugin class such as: writing a custom authenticator in method setUserCredentials(); or controlling the routing of queries,
				e.g. by returning false in method setForwardingNode() when you would wish your node to halt queries received from certain nodes; or by returning -1
				in method nextQueriedDataSource() to prevent a query from reaching a certain file, RDBMS table or from propagating to certain nodes. Use methods
				filterRow() or filterRowsBatch() to eliminate records from the result or change their content.
				</li>
				<li>Note that the method nextQueriedDataSource() in SQLResultFilterX passes an additional dataSourceID to the plugin which can be used to lookup 
				an associated NodeID for data sources that resolve to GaianDB nodes. To lookup general configuration information, you can use the SQL API stored 
				procedures. There are also a few available java shortcuts for looking up some useful information directly:
				<pre>
GaianDBConfig.getGaianConnections() // returns array of connection ids
GaianDBConfig.getConnectionURL(String cid) // returns the URL for a gaian connection
GaianDBConfig.getGaianNodeID() // returns local NodeID
GaianDBConfig.getGaianNodeID(String nodeDefName) // returns NodeID for a given dataSourceID referencing a gaiandb node
				</pre>
				</li>
			</ul>
		</td>
	  </tr>
	  <tr>
		<td><b>SQL_QUERY_FILTER</b></td>
		<td>None</td>
		<td>This property names a java policy class implementing the com.ibm.gaiandb.policyframework.SQLQueryFilter interface. 
	The implementation class' role is to apply a filter onto the query. 
	At the moment, gaiandb only supports reducing the number of queried columns or changing/removing/adding predicates to the qualifiers.
	<pre>SQL_QUERY_FILTER=com.ibm.gaiandb.policyframework.PolicySQLFilter</pre></td>
	  </tr>
  </tbody>
</table>		
<br />

<hr><h3><a name="contents177">Using the management API to apply configuration updates</a></h3>
<p>To apply configuration updates, the configuration file is ultimately more flexible, but the management API offers numerous
advantages as well:</p>
<ul>
	<li>Ability to query logical tables and data sources in the whole network of GaianDB nodes; without needing to access each config
	file independently.</li>
	<br/><li>Ability to interrogate the <u>loaded</u> system configuration, including some information that is not visible
	in the configuration file. E.g. with '<code>call listrdbc()</code>' which lists active connections or with
	'<code>call listds()</code>' which lists properties of data sources.</li>
	<br/><li>Configuration shortcuts: e.g. '<code>setltforrdbtable()</code>' or '<code>setltforfile()</code>'; which provide the ability to define a
	new logical table simply by matching it to a certain data source that it should federate. The system automatically queries
	the data source extracting its meta-data and builds a logical table and attached data source based on the column
	definitions in the meta-data.</li>
	<br/><li>Validation/error checking of input parameters</li>
	<br/><li>Ability to set constructs (e.g. logical tables, data sources) and properties remotely on any GaianDB node that is accessible
	on the network (assuming the configuration of the node allows this).</li>
</ul>

<p>This section lists the configuration management API stored procedures. All of these procedures are invoked using the keyword '<code>call</code>' followed by the procedure name and arguments. For example: '<code>call setltforfile()</code>'.</p>

<p>The following acronyms are used in procedure and/or argument names:</p>

<table class='data'>
  <thead>
    <tr>
      <th width="180"><b>Acronym/Token</b></th>
      <th width="844"><b>Meaning</b></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="180">rdbc</td>
      <td width="844">Relational Database Connection</td>
    </tr>
    <tr class='odd'>
      <td width="180">lt</td>
      <td width="844">Logical Table. A logical table name 'ltname' is limited to 80 chars</td>
    </tr>
    <tr>
      <td width="180">ds</td>
      <td width="844">Data Source. A data source name 'dsname' is limited to 20 chars</td>
    </tr>
    <tr class='odd'>
      <td width="180">dsname</td>
      <td width="844">Data Source Name. A name chosen by the user to identify the data source</td>
    </tr>
    <tr>
      <td width="180">dsid</td>
      <td width="844">Data Source ID. A composite value variable: '&lt;ltname&gt;_DS&lt;dsname&gt;'</td>
    </tr>
    <tr class='odd'>
      <td width="180">cid</td>
      <td width="844">JDBC Connection ID: Any name, limited to 20 chars</td>
    </tr>
    <tr>
      <td width="180">nodeid</td>
      <td width="844">GaianDB node identifier: When running on default port 6414, this is just &lt;hostname&gt;, otherwise it is: &lt;hostname&gt;:&lt;portnumber&gt;</td>
    </tr>
    <tr class='odd'>
      <td width="180">options</td>
      <td width="844">Possible options are: 'INMEMORY [INDEX ON &lt;column name&gt;]'</td>
    </tr>
    <tr>
      <td width="180">columns</td>
      <td width="844">Ordered list of physical table's column names which the logical table's columns map to (only needed if these are not all the same)</td>
    </tr>
    <tr class='odd'>
      <td width="180">*</td>
      <td width="844">Denotes list variables, with Comma Separated Values. Note that a comma may also be used within a column's definition</td>
    </tr>
  </tbody>
</table>

<p>The '<code>list<i>xxx</i></code>' procedures take no arguments and return a ResultSet:</p>

<table class='data'>
  <thead>
   <tr>
     <th><b>Procedure</b></th>
     <th><b>Description</b></th>
   </tr>
  </thead>
<tbody>
  <tr>
    <td>call listspfs()</td>
    <td>Show all stored procedures and functions in schema 'gaiandb'.</td>
  </tr>
  <tr class='odd'>
    <td>call listapi()</td>
    <td>Show init SQL used to define GaianDB API stored procedures.</td>
  </tr>
  <tr>
    <td>call listconfig()</td>
    <td>Show all configuration properties and their values.</td>
  </tr>
  <tr class='odd'>
    <td>call listwarnings()</td>
    <td>Show all recent warnings generated on the servers in the whole network.</td>
  </tr>
  <tr>
    <td>call listlts()</td>
    <td>Show logical table definitions in the whole network.</td>
  </tr>
  <tr class='odd'>
    <td>call listderbytables()</td>
    <td>Show table and column defs of physical Derby tables in the 'gaiandb' database of all GaianDB nodes.</td>
  </tr>
  <tr>
    <td>call listexplain(ltname)</td>
    <td>Show explain route and row counts for a logical table query or a distributed subquery.</td>
  </tr>
  <tr class='odd'>
    <td>call listflood()</td>
    <td>Show connections/topology traversed by a flood query - with no access to data sources in the network.</td>
  </tr>
  <tr>
    <td>call listrdbc()</td>
    <td>Show loaded rdb connections in whole network.</td>
  </tr>
  <tr class='odd'>
    <td>call listds()</td>
    <td>Show loaded data sources in whole network.</td>
  </tr>
  <tr>
    <td>call listqueries(depth)</td>
    <td>Show all the running queries. If depth is 0, it will show the queries on the node, if depth is -1 it will show all queries in the whole network.</td>
  </tr>
  <tr class='odd'>
    <td>call cancelquery(queryId)</td>
    <td>Cancels a running query according to its queryId</td>
  </tr>
</table>

<p>The others procedures are used to modify a node's configuration and take arguments &amp; don't return anything:</p>
<table class='data'>
  <thead>
   <tr>
     <th><b>Procedure</b></th>
     <th><b>Description</b></th>
   </tr>
  </thead>
<tbody>
   <tr class='odd'>
  	<td>call addgateway(ipaddress)</td>
  	<td>Add a gateway node in the network by specifying its IP address.</td>
  </tr>
  <tr>
    <td>call gconnect(cid, host)</td>
    <td>Establish a hard-wired GaianDB connection using default port/user/password values (6414/gaiandb/&lt;pwd from derby.properties&gt;)</td>
  </tr>
  <tr class='odd'>
    <td>call gconnectx(cid, host, port, usr, pwd)</td>
    <td>setup a hard-wired GaianDB connection, using different port/user/password from the default values.</td>
  </tr>
  <tr>
    <td>call gdisconnect(cid)</td>
    <td>Disconnect from a hard-wired GaianDB connection.</td>
  </tr>
  <tr class='odd'>
    <td>call getfilestats(file_path)</td>
    <td>Get details about a file.</td>
  </tr>
  <tr>
    <td>call nestexec(sql_query, sql_nested)</td>
    <td>Nest a query within another query.</td>
  </tr>
  <tr class='odd'>
    <td>call removeds(dsid)</td>
    <td>Remove data source.</td>
  </tr>
  <tr>
    <td>call removegateway(ipaddress)</td>
    <td>Remove a gateway.</td>
  </tr>
  <tr class='odd'>
    <td>call removelt(ltname)</td>
    <td>Remove Logical Table and all attached data sources.</td>
  </tr>
  <tr>
    <td>call removerdbc(cid)</td>
    <td>Remove Relational Database Connection - Only works if it is not active with dependant attached data sources.</td>
  </tr>
  <tr class='odd'>
    <td>call setaccessclusters(clusters*)</td>
    <td>Set list of private clusters which this GaianDB node belongs to.</td>
  </tr>
  <tr>
    <td>call setconfigproperty(key, value)</td>
    <td>Set a specific configuration file property (to list them all use listconfig())</td>
  </tr>
  <tr>
    <td>call setconfigproperties( SQLQUERY_RETURNING_PROPERTY_KEYS_AND_VALUES )</td>
    <td>Set a batch of configuration properties -
    pass in a SQL query string as argument which should return 2 columns, the first representing properties and the second their values.
    WARNING: Whilst this API will check whether properties already exist and update them appropriately when they do, it is not as safe to call this API
    for defining structures like logical tables or data sources as it is to use the purpose built APIs, e.g. setlt(), setdsvti, etc.
    Great care must be taken when defining properties directly.</td>
  </tr>
  <tr class='odd'>
    <td>call setdiscoveryhosts(hosts*)</td>
    <td>Set list of hosts that may be discovered and connected to.</td>
  </tr>
  <tr>
    <td>call setdiscoveryip(ipaddress)</td>
    <td>Set discovery address. This should be a broadcast mask or multicast group.</td>
  </tr>  
  <tr class='odd'>
    <td>call setdsexcel(ltname, dsname, filename, options*, columns*)</td>
    <td>Set Excel file data source for Logical Table, with source name, file name, options and column mappings.</td>
  </tr>
  <tr>
    <td>call setdsfile(ltname, dsname, filename, options*, columns*)</td>
    <td>Set File data source for Logical Table, with source name, file name, options and column mappings.</td>
  </tr>
  <tr class='odd'>
    <td>call setdslocalderby(ltname, dsname, table, options*, columns*)</td>
    <td>Set RDBMS local Derby table data source for Logical Table, with source name, physical table, options and column mappings.</td>
  </tr>
  <tr>
    <td>call setdsrdbtable(ltname, dsname, cid, tableExpression, options*, columns*)</td>
    <td>Set RDBMS table data source for Logical Table, with source name, connection id, physical table or composite table expression (which may involve joins and where clauses), options and column mappings.
    Remember to fully qualify table names if they are not located in the default schema, by explicitly prefixing them with their schema name.</td>
  </tr>
  <tr class='odd'>
    <td>call setdsvti(ltname, dsname, vticlass, args*, options*, columns*)</td>
    <td>Set custom-made Derby virtual table interface data source for Logical Table, with arguments as above.</td>
  </tr> 
  <tr>
    <td>call setloglevel(level)</td>
    <td>Set the log level. Possible values are: 'NONE', 'LESS', 'MORE', 'ALL'.</td>
  </tr>
  <tr class='odd'>
    <td>call setlt(ltname, ltdef*, ltconstants*)</td>
    <td>Set Logical Table manually; with columns definitions and constant columns definitions.</td>
  </tr>  
  <tr>
    <td>call setltconstants(ltname, ltconstants*)</td>
    <td>Set Logical Table constant columns (the table must be defined). This overwrites existing constant columns for that table.</td>
  </tr>
  <tr class='odd'>
    <td>call setltforexcel(ltname, spreadsheetparameters*)</td>
    <td>Set Logical Table to federate an excel spreadsheet. The different parameters are detailed into the <a href="#contents201">Federate an existing Excel</a> section.</td>
  </tr> 
  <tr>
    <td>call setltforfile(ltname, filename)</td>
    <td>Set Logical Table to federate a csv File, with column defs derived from the file (named COLUMN1, COLUMN2, etc).</td>
  </tr>
  <tr class='odd'>
    <td>call setltfornode(ltname, nodeid)</td>
    <td>Set Logical Table mirroring the definition for the given Logical Table Name on another GaianDB node, so its data can be queried remotely.</td>
  </tr>  
  <tr>
    <td>call setltforrdbtable(ltname, cid, tableExpression)</td>
    <td>Set Logical Table to federate an RDBMS table data source or composite table expression (which may involve joins and where clauses), with columns defs derived from the RDBMS table.
    Remember to fully qualify table names if they are not located in the default schema, by explicitly prefixing them with their schema name.</td>
  </tr>
  <tr class='odd'>
    <td>call setmaxpoolsizes(size)</td>
    <td>Set the maximum size of the data source pools.</td>
  </tr>
  <tr>
    <td>call setmaxpropagation(depth)</td>
    <td>Set the max propagation depth for a query.</td>
  </tr>
  <tr class='odd'>
    <td>call setminconnections(numconnections)</td>
    <td>Set the number of gaian connections to establish and maintain 2-way connections with.</td>
  </tr>
  <tr>
    <td>call setmsgbrokerdetails(host, port, topic)</td>
    <td>Set message broker host, port and topic values.</td>
  </tr>  
  <tr class='odd'>
    <td>call setnodeconstants(nodeconstants*)</td>
    <td>Set list of constant columns for the GaianDB node.</td>
  </tr>       
  <tr>
    <td>call setrdbc(cid, driver, url, usr, pwd)</td>
    <td>Set Connection ID with DRIVER, URL, USR, PWD identifying a Relational Database Connection.</td>
  </tr>
  <tr class='odd'>
    <td>call setsourcelist(listid, cids*)</td>
    <td>Set a list of JDBC connection ids which may be referenced/federated by distributed nested queries.</td>
  </tr>
</tbody>
</table>
</pre>
<p><b>Note</b>: the majority of arguments are of type VARCHAR, except for '<i>port</i>', '<i>numconnections</i>', '<i>depth</i>' and '<i>size</i>' which are of type INTEGER.
Maximum VARCHAR sizes for each argument are shown when running procedure 'call listspfs()', as seen in <a href="WorkedExamples.html">WorkedExamples.html</a>.
All VARCHAR arguments must be delimited using single quotes. The arguments are best understood by working through the examples
shown under <a href="#contents52">Quick table federation examples</a> and in document <a href="WorkedExamples.html">WorkedExamples.html</a>.</p>

<br/>




<hr><h3><a name="contents67">Pluralized data sources</a></h3>
<p>
Pluralized data sources allow access to multiple end-points using a single data source definition, when these essentially have the same federation properties
(i.e. identical options and column mappings). 
Pluralizing a data source can allow access to an undetermined set of end-points, resolved at runtime.
It also saves the maintenance complexity of having to configure many similar data source definitions or regularly having to re-configure definitions when
their end-point identifiers are variable.

This feature is currently implemented for flat file data sources (e.g. CSV) and for custom VTIs.
</p>

<p>Pluralization configuration syntax:</p>
<UL>
<LI>For flat files (e.g. CSV):</LI>
<pre>
&lt;Data Source ID&gt;_VTI=com.ibm.db2j.FileImport
&lt;Data Source ID&gt;_OPTIONS=PLURALIZED [USING WILDCARD | USING REGEX]
&lt;Data Source ID&gt;_ARGS=&lt;Absolute or relative path expression containing any number of '*' wildcard characters or a REGEX pattern&gt;

# Note: When no pattern scheme is specified, the default is "USING WILDCARD"

# Example for data source ID 'LT0_DS0', to access a set of files in a folder structure under the parent folder of the GaianNode's working directory:
LT0_DS0_VTI=com.ibm.db2j.FileImport
LT0_DS0_OPTIONS=INMEMORY,PLURALIZED
LT0_DS0_ARGS=../*testfiles/datafile*.dat

# Example using a REGEX pattern:
# Note: The REGEX cannot contain ^ $ ( ) characters to avoid confusion with filenames
LT0_DS0_VTI=com.ibm.db2j.FileImport
LT0_DS0_OPTIONS=INMEMORY,PLURALIZED USING REGEX
LT0_DS0_ARGS=/home/user[0-9]+/workspace[1-3]/.*testfiles/datafile[2]?.dat

</pre>
<LI>For custom VTIs</LI>
<pre>
&lt;Data Source ID&gt;_OPTIONS=PLURALIZED [WITH ENDPOINT CONSTANTS &lt;list of logical table column ids separated by spaces&gt;]

# Note: Optional end-point constants are column values returned by the custom VTI if it implements the PluralizedVTI interface.
# Each column ID is specified using the letter 'C' as prefix followed by the index of the logical table column for which it is a constant value for each pluralized instance. 

# Background: Custom VTIs are classes implemented by users to access their own particular back end data sources.
# These typically extend the AbstractVTI class and may implement various other Derby VTI interfaces.
# The purpose of declaring these as PLURALIZED would be to easily access a plurality of end-points that they allow access to.
# For example, a VTI may wish to access data from a plurality of web services having variable IP addresses.
# At runtime, a VTI implementing the PluralizedVTI interface would be requested its "data source instance IDs" by GaianDB.
# In this example this may resolve to a list of IP addresses.
# Next, GaianDB would request from the VTI (again, through the PluralizedVTI interface) the "end-point constants" for each of the instance IDs.
# The VTI would then return constant values associated with the end-point identifiers (e.g ipaddress, hostname, ...).
# This information allows GaianDB to perform some early filtering to avoid querying end-points if a query's predicates excludes them based on their constant values.  

# Example: to set logical table columns C3 and C4 at runtime with constant values for each pluralized instance exposed by SamplePluralizedVTI:
LTX_DS0_VTI=myproject.SamplePluralizedVTI
LTX_DS0_OPTIONS=PLURALIZED WITH ENDPOINT CONSTANTS C3 C4

# The logical table definition might be (following the example in the discussion above):
LTX_DEF=LATITUDE INT, LONGITUDE INT, HOSTNAME VARCHAR(50), IPADDRESS VARCHAR(50), TSTAMP TIMESTAMP, CPU INT

</pre>
</UL>
<p>




<hr><h3><a name="contents66">In-Memory tables and indexes on their columns</a></h3>
<p>
Rows from an RDBMS database table, File or any other data source can be loaded into memory by GaianDB. This speeds up data access
considerably. The rows loaded in memory can also be indexed to speed up data access even further. GaianDB currently only
supports 1 index per data source.</p>

<p>To load / unload a table in / from memory for a data source id 'LT0_DSFILE1' (i.e. logical table 'LT0', data source 'FILE1'), and optionally define &amp; build an index on the in-memory table (on column PHONE):</p>
<UL>
<LI>Use API stored procedures at the command line as in the examples:</LI>
<pre>
#First, to view all data sources and identify the relevant data source ids:
sql> call listds()

#Then, apply updates by setting the associated '_OPTIONS' property of the data source id:
sql> call setconfigproperty('LT0_DSFILE1_OPTIONS', 'INMEMORY')
sql> call setconfigproperty('LT0_DSFILE1_OPTIONS', 'INMEMORY INDEX ON PHONE')
sql> call setconfigproperty('LT0_DSFILE1_OPTIONS', '')
</pre>
<LI>Alternatively, set the OPTIONS property in the configuration file directly for the relevant data source, as in the examples:</LI>
<pre>
LT0_DSFILE1_OPTIONS=INMEMORY
LT0_DSFILE1_OPTIONS=INMEMORY INDEX ON PHONE

To unload, remove the value or comment the property out:
LT0_DSFILE1_OPTIONS=
#LT0_DSMYFILE_OPTIONS=INMEMORY INDEX ON PHONE
</pre>
</UL>
<p>
<b>Note</b>: the In-Memory options, like all configuration options, are dynamic: Files may be loaded and unloaded from memory and indexes built or dropped
while the GaianDB server is running simply by setting/unsetting the options. Also note that any changes in a file data source
which is loaded in memory will trigger a reload into memory (and index re-build if applicable) whenever a query is issued against it.
</p>
<p><b>Note</b>: only predicate conditions involving an indexed column which are not OR'ed with other
predicates not involving it will take advantage of the index for performance improvement.</p>

<hr><h3><a name="contents92">Constant Column definitions</a></h3>

<p>Constants Columns are columns that are defined with constant values for a specific logical table, or for all logical tables on a particular GaianDB node.
They form part of the definition of a logical table and are included in the table's data when it is queried.
Each GaianDB node that exposes data through the same logical table may have different values defined for its constant columns.
The constant columns can also be defined, updated or removed dynamically.</p>

<p>A common usage for a constant column is to annotate a logical table with a particular context.
For example, you could include a column that identifies an 'instance' of a logical table as running on a GaianDB node in OFFICE1.
This 'context' can then be defined locally and independently for every node in the network - identifying each 'instance' uniquely.</p>

<p>To define a constant column 'OFFICE VARCHAR(50)' with the value 'OFFICE1':</p>
<UL>
<LI>Use API stored procedure at the command line, as follows:</LI>
<pre>
#Define a node wide constant
call setnodeconstants('OFFICE VARCHAR(50) OFFICE1')

#To reduce the scope of the constant column to a unique logical table 'LT0':
call setlt('LT0', 'LOCATION VARCHAR(20), NUMBER INT', 'OFFICE VARCHAR(50) OFFICE1')
</pre>
<LI>Or in the configuration file, set the NODE_CONSTANTS property directly, as follows:</LI>
<pre>
#Define a node wide constant
NODE_CONSTANTS=OFFICE VARCHAR(50) OFFICE1

#When setting at the logical table definition level, constant columns are defined separately from the other columns:
LT0_DEF=LOCATION VARCHAR(20), NUMBER INT
LT0_CONSTANTS=OFFICE VARCHAR(50) OFFICE1
</pre>
</UL>
<p>Then, to retrieve data for logical table 'LT0' from Gaian Nodes that are running in 'OFFICE1', issue the query:</p>
<pre>select * from LT0 where OFFICE = 'OFFICE1'</pre>

<p>
Unlike key partitioning as used by existing relational databases, constant column definitions and updates never involve any
data movements. Constant columns are better thought of as belonging to a logical table's meta-data rather than as real data
columns; which is what default or generated columns in standard relational databases are.
The reason for this is that the constant column data does not form part of the logical table's underlying data source's raw data.
It is added dynamically at runtime when required. This minimises storage requirements and allows for greater flexibility,
as the constant columns and their values can be dynamically altered at any time.
</p>
<p>For constant column definitions, the following SQL Standard data types <b>cannot</b> currently be used:</p>
<pre>   BIT, BINARY, VARBINARY, LONGVARBINARY, BLOB </pre>





<hr><h3><a name="contents64">Using the LISTQUERIES and CANCELQUERY procedures as well as the GDB_TIMEOUT and GDB_WID features</a></h3>
<p>In short:<p/>
<table class='data'>
  <thead>
   <tr>
     <th><b>Feature</b></th>
     <th><b>Description</b></th>
   </tr>
  </thead>
<tbody>
	<tr>
		<td>call listqueries(&lt;depth&gt;)</td>
		<td>Procedure which gives you meta-data information about queries that are either in progress or cached.
		A depth of -1 will give you information about the state of all queries and their forwarded and spawned sub-queries throughout network.</td>
	</tr>
	<tr class='odd'>	
		<td>call cancelquery(&lt;queryID&gt;)</td>
		<td>Procedure which allows you to abort a query given a queryID that you have found in the listing from listqueries()</td>
	</tr>
	<tr>
		<td>GDB_TIMEOUT=&lt;timeout duration in milliseconds&gt;</td>
		<td>A SQL comment option you can specify at the end of queries (e.g. select * from T -- GDB_TIMEOUT=1000)
		This will cause the query and all its forwarded and spawned sub-queries throughout the network to be aborted when the duration has elapsed (or shortly after).</td>
	</tr>
	<tr class='odd'>
		<td>GDB_WID=&lt;workload id&gt;</td>
		<td>A SQL comment option (like GDB_TIMEOUT) which is used to specify an arbitrary workload id name which will appear in the 
		result of the listqueries() procedure against all queries derived from the original user query (including forwarded and spawned sub-queries).
		This is useful from an application point of view to identify the queryIDs which may need cancelling when a long running query has spawned several others.</td>
	</tr>
</tbody></table>
	<p/>Below is an example walk-through of the usage of listqueries() and cancelquery().<p/>
<pre>
sql>
sql> select * from LT0_P --GDB_WID=myuid-123
select * from LT0_P --GDB_WID=myuid-123
======================================================================================================================================
LOCATION                      |MISC                          |GDB_NODE            |GDB_LEAF                                          |
======================================================================================================================================
IIIIIIIIIIII1111111111        |3                             |voyager:6415        |./csvtestfiles/datafile2.dat                      |
ADAMSON                       |4                             |voyager:6415        |./csvtestfiles/datafile2.dat                      |
S97634datafile2               |32                            |voyager:6415        |./csvtestfiles/datafile2.dat                      |
ZZZZZZZZZZZZ1111111111        |3                             |voyager:6415        |./csvtestfiles/datafile2.dat                      |
ZZZZZ                         |1                             |voyager:6415        |./csvtestfiles/datafile2.dat                      |
YYYYYYYYYYY2222222222         |62                            |voyager:6416        |./csvtestfiles/datafile3.dat                      |
BLAHBLAH                      |3                             |voyager:6416        |./csvtestfiles/datafile3.dat                      |
SHG*&^22datafile3             |62                            |voyager:6416        |./csvtestfiles/datafile3.dat                      |
FFFFFFFFFFFK2222222222        |62                            |voyager:6416        |./csvtestfiles/datafile3.dat                      |
111111111                     |12                            |voyager             |./csvtestfiles/datafile.dat                       |
WWWWWWWWW                     |32                            |voyager             |./csvtestfiles/datafile.dat                       |
991111111                     |72                            |voyager             |./csvtestfiles/datafile.dat                       |
SZZZSK_DAVIDSFILE             |22                            |voyager             |./csvtestfiles/datafile.dat                       |
AAAAAAAAA                     |3                             |voyager             |./csvtestfiles/datafile.dat                       |
CCCCCCCCC                     |5                             |voyager             |./csvtestfiles/datafile.dat                       |
SYSK_DATAFILE1!!              |150                           |voyager             |./csvtestfiles/datafile.dat                       |
TTTTTTTTT                     |29                            |voyager             |./csvtestfiles/datafile.dat                       |
======================================================================================================================================
Fetched 17 rows. Total Time: 90ms (Execution Time: 88ms)
</pre>

<p>Once you have run the query, and while it's running, you can now list all the queries running on your Gaian node or on the whole network. By using '0' as the argument to listqueries(), you query only the local node.
 And by using '-1' you query the whole network, this might take a bit longer to get all the information.<br/><br/>
Below is an example, you can see that the query issued with the GDB_WID of 'myuid-123' has now run and has been cached on 3 nodes.
<pre>
sql>
sql> call listqueries(-1)
call listqueries(-1)
========================================================================================================================================================================
GDB_NODE            |QUERYID                         |DEPTH   |STATE        |LTNAME      |QUERYHASH    |START_TS                  |QUERY_MS   |NBROWS   |GDB_WID       |
========================================================================================================================================================================
voyager:6415        |voyager:1332423156434:6         |       1|EXECUTE      |SUBQUERY    |94FEC723     |2012-03-22 13:32:36.439   |         19|        0|-             |
voyager:6416        |voyager:1332423156434:6         |       1|EXECUTE      |SUBQUERY    |94FEC723     |2012-03-22 13:32:36.437   |          5|        0|-             |
voyager:6415        |voyager:6415:1332423092841:2    |       0|CACHED       |LT0         |FC4C3FE3     |2012-03-22 13:31:32.841   |         68|       17|myuid-123     |
voyager:6416        |voyager:6415:1332423092841:2    |       1|CACHED       |LT0         |FC4C3FE3     |2012-03-22 13:31:32.884   |         20|        4|myuid-123     |
voyager             |voyager:6415:1332423092841:2    |       1|CACHED       |LT0         |FC4C3FE3     |2012-03-22 13:31:32.87    |         38|        8|myuid-123     |
voyager:6416        |voyager:6415:1332423049787:1    |       1|CACHED       |LT0         |E71B3BDD     |2012-03-22 13:30:49.818   |         13|        4|-             |
voyager             |voyager:6415:1332423049787:1    |       1|CACHED       |LT0         |E71B3BDD     |2012-03-22 13:30:49.801   |         20|        8|-             |
voyager:6416        |voyager:6415:1332423032873:0    |       1|CACHED       |LT0         |E7FFC30C     |2012-03-22 13:30:32.899   |         17|        4|-             |
voyager             |voyager:6415:1332423032873:0    |       1|CACHED       |LT0         |E7FFC30C     |2012-03-22 13:30:32.894   |         12|        8|-             |
voyager:6415        |voyager:1332422972404:1         |       1|CACHED       |LT0         |E7FFC30C     |2012-03-22 13:29:32.463   |         54|        5|-             |
voyager:6416        |voyager:1332422972404:1         |       1|CACHED       |LT0         |E7FFC30C     |2012-03-22 13:29:32.459   |         46|        4|-             |
========================================================================================================================================================================
Fetched 11 rows. Total Time: 38ms (Execution Time: 34ms)
</pre>
<p>If you launched a long running query, its STATE would likely be EXECUTE (or FETCH/RE-FETCH in the case of a JOIN), and if you think that the query might be looping or you need to cancel it, you can use cancelquery() as follows:
<pre>
sql>
sql> call cancelquery('voyager:6415:1332423092841:2')
call cancelquery('voyager:6415:1332423092841:2')
</pre>

<br/>

<hr><h3><a name="contents65">Connection maintenance configuration in intermittent/high latency/low bandwidth networks</a></h3>

<p>The GAIAN_CONNECTIONS_CHECKER_HEARTBEAT_MS configuration parameter defines the maximum time GaianDB will wait to receive a response to a connection request, query request or maintenance (keep-alive) message. Beyond that timeout, the GaianDB connection in question is assumed to be unavailable so it is dropped and its associated resources are reclaimed.</p>

<p>The default value is 5000 milliseconds. You can choose to:</p>

<ul>
<li>Increase this value in high latency networks to give the nodes enough time to discover each other and maintain their connections, and for
them to determine whether a long-running query is actually hanging.</li>
<li>Decrease this value to make nodes more reactive to nodes that are not responding to query messages or connection establishment
and maintenance messages.</li>
</ul>

<p><b>Note</b>: DriverManager.setLoginTimeout(timeout_ms) cannot be relied on because not all operating systems support setting a timeout on
blocking socket calls.</p>

<hr><h3><a name="contents215">Hard-wiring connections between GaianDB nodes (incl setting up gateways)</a></h3>
<p>It may sometimes be necessary to hard-wire connections between GaianDB nodes, for example: in physical networks that do not support IP Multicast and so automatic discovery is not possible (which is often the case in wireless networks) or in order to connect GaianDB networks from different domains together. This can be done by forcing GaianDB nodes
to act as gateways between the different network domains (Fig. 8). Note that for a pair of nodes from 2 disparate domains to
act as gateways, connections should be hard-wired in both directions between the nodes. It is also preferable to have
several gateway pairs between such networks to avoid bottlenecks. In Fig. 8 the gateway pairs are (6,7), (7,8) and (5,18).</p>
<center>
<TABLE class='image'>
   <TR class='image'>
   <TD class='image'><img src="./images/gaiandb2.gif"></TD></TR>
   <TR class='image'>
     <TD class='image' align='center'>Fig. 8 - Joining multiple network domains with GaianDB gateways</TD></TR>
</TABLE>
</center>

<p>You can establish a hard-wired connection by:</p>
<ol>
<li>
Use of one of the <a href="#contents177">API procedures</a> below to connect to a GaianDB node running on a given host, giving a ConnectionID of your choice
(as long as it does not conflict with already defined RDBMS connection IDs):</p>
<pre>
call gconnect( &lt;ConnectionID&gt;, &lt;HostName&gt; )
call gconnectx( &lt;ConnectionID&gt;, &lt;HostName&gt;, &lt;Port Number&gt;, &lt;Remote Node UserName&gt;, &lt;Remote Node Password&gt; )
</pre>
</li>
<li>

Alternatively, using the configuration property 'DEFINED_GAIAN_CONNECTIONS' and associated connection properties in the configuration file
as described <a href="#contents209">above</a>.
</li>
</ol>
<br />
<p><b>Discovery Gateways</b></p>
<p>In situations where two (or more) nodes may be able to communicate, but the issue is that they cannot automatically discover each other due to restrictions on the network; it is possible to setup a Discovery Gateway node to act as a discovery intermediary. This is different to creating a hard-wired gateway connection. A Discovery Gateway simply forwards on the node discovery request from one GaianDB node to another GaianDB node; the two nodes then establish a connection directly. Further traffic does not flow through the discovery gateway.</p>
<p>Discover gateways can be defined using the configuration file parameter DISCOVERY_GATEWAYS, as described <a href="#contents209">above</a>.</p>



<hr><h3><a name="contents99">Text file federation configuration options (e.g: how to specify different record and field separators)</a></h3>

<p>
Properties that govern how a flat file is federated by GaianDB can be altered using a 'control file'.
As an example, the GaianDB installation comes with a data file '&lt;GaianDB-install-folder&gt;/csvtestfiles/datafile.dat' which has a control file named 'datafile.dat.properties'
in the same folder. Control file names should always have the '.properties' extension. The contents of the 'datafile.dat.properties' file is shown below. 
Notice that it contains mostly hashed out properties. These are given for convenience and show some of the labels or default values that may be used.
Most character sequences should work as record or field separators.
</p>

<pre>
RecordSeparator=LF

# Others: CR-LF, New Line, Empty Line, FF

#FieldSeparator=Tab,Space,CR,LF,CR-LF,Comma,Semicolon
#FieldStartDelimiter=
#FieldEndDelimiter=
#HasDelimeterAtEnd=

#ColumnWidths=
#Version=
#Format=
#MessageFile=
#ColumnDefinition=FALSE  #set this to TRUE if the first row in the file has a list of column names.

#DataCodeset=
#DataLocale=
</pre>

<p>Note that a control file does not always have to reside in the same location as it's associated data file.
GaianDB resolves the location of a control file based on certain precedence rules. The block below describes these.
Notice how a 'FileImportDefaults.properties' file can apply to multiple data files in an entire folder hierarchy at it's level and below it.
Also notice how the control files don't have to be located with the data files, but can instead come under a 'FileImportControls' folder in the GaianDB install folder.
</p>
<pre>
Resolution of a control file's location, for a data file whose path is: '/a/b/datafile.dat'.

The first of the following files that exists will be chosen:
(Note that 'FileImportDefaults' and 'FileImportControls' are hard-coded location strings)
(Note also that the &lt;GaianDB-node-workspace-folder&gt; will be the working directory of the process unless you have set the java system property: 'derby.system.home')

1) /a/b/datafile.dat.properties
2) /a/b/FileImportDefaults.properties
3) &lt;GaianDB-node-workspace-folder&gt;/FileImportControls/a/b/datafile.dat.properties
4) &lt;GaianDB-node-workspace-folder&gt;/FileImportControls/a/b/FileImportDefaults.properties
5) &lt;GaianDB-node-workspace-folder&gt;/FileImportControls/b/datafile.dat.properties
6) &lt;GaianDB-node-workspace-folder&gt;/FileImportControls/b/FileImportDefaults.properties
7) &lt;GaianDB-node-workspace-folder&gt;/FileImportControls/datafile.dat.properties
8) &lt;GaianDB-node-workspace-folder&gt;/FileImportControls/FileImportDefaults.properties

If no control file is resolved using this process, the default CSV format is assumed.
</pre>

<hr><h2><a name="contents306">Security</a></h2>

<P>GaianDB is built on Derby - so it implicitly includes all Derby security features. For these, please refer to the <a href="http://db.apache.org/derby/docs/10.8/ref/index.html">Derby user docs</a>.</P>

<hr><h3><a name="contents307">Communication encryption using SSL (Secure Sockets Layer)</a></h3>
<P>
Gaian uses Derby's SSL capability to provide private (encrypted) communications with it's clients.
Note that Gaian nodes running SSL may also connect to non-SSL nodes - however in this case, only queries flowing *to* the SSL nodes 
and data flowing *back* from the SSL nodes are encrypted. Connections to non-SSL nodes are not encrypted, even if they originate
from an SSL node. To ensure private communications across a full network of Gaian nodes, you need to enable SSL on 
all of them. Additionally, communications beyond Gaian to back-end data sources may also need to be encrypted using
their own privacy/encryption mechanism.<P/>

<hr><h4><a name="contents3071">Server Configuration for SSL</a></h4>

To enable SSL for a Gaian node, you need to set property 'derby.drda.sslMode' in Derby's property file at location 
'&lt;GAIAN_WORKSPACE&gt;/derby.properties' and also ensure you have configured a keyStore file and password as described below.
This will cause the node to only accept SSL client connection requests.<P/>
Property 'derby.drda.sslMode' is initially commented out in derby.properties (default value 'off'). There are 3 valid settings:
<pre>
derby.drda.sslMode=off
derby.drda.sslMode=basic
derby.drda.sslMode=peerAuthentication
</pre>

The Key Store configuration required when 'derby.drda.sslMode' is not 'off' is described below. The keyStore and password are used to
encrypt inbound connections. The third setting 'derby.drda.sslMode=peerAuthentication' is an extension to 'basic' - which additionally
causes the Derby server to only allow connections from "certified" clients. For more detail on this feature, please consult Derby documentation:
<a href="http://db.apache.org/derby/docs/10.8/adminguide/cadminssl.html">http://db.apache.org/derby/docs/10.8/adminguide/cadminssl.html</a>
<P/>

A Key pair is required on the Gaian server for SSL to work. Below are example commands to generate one:
<ul>
<li>Short command example which prompts user for missing fields:
<pre>keytool -genkey -alias derbyServerKey -keystore ./.keyStore</pre></li>
<li>Full command example, with no interactive prompts:
<pre>keytool -genkey -dname "CN=Bob Jones, OU=Research, O=IBM, L=Yorktown Heights, S=New York State, C=USA" -alias derbyServerKey -keypass passw0rd -keystore ./.keyStore -storepass passw0rd</pre></li>
</ul>
		
At startup, Gaian will use the following default values for keyStore file name and password:
<pre>
Default keyStore file:		&ltGAIAN_WORKSPACE&gt/.keyStore
Default keyStore password:	Gaian system user password (defined in derby.properties, property derby.user.&ltgaian_user&gt), e.g: passw0rd
</pre>

You can override the defaults above by setting environment variable JAVA_OPTS (referenced in launchGaianServer.sh(/.bat)), e.g:
<pre>export JAVA_OPTS="-Xmx256m -Djavax.net.ssl.keyStore=~/.myKeyStore -Djavax.net.ssl.keyStorePassword=myKeyStorePwd"</pre>

<hr><h4><a name="contents3072">Client Setup for SSL</a></h4>

All JDBC clients wishing to connect to a Gaian/Derby SSL node must specify argument "ssl=basic" or "ssl=peerAuthentication" in
their Connection URL, e.g:
<pre>jdbc:derby://localhost:6414/gaiandb;ssl=basic</pre>

Gaian's JDBC client tools easily expose SSL configuration:
<ul>
<li>The UI dashboard has a drop-down list with all valid SSL modes</li>
<li>Gaian's command line interface tool allows you to specify the SSL mode when invoked, e.g:
<pre>queryDerby.sh -ssl=basic "select * from LT0"</pre></li>
</ul>


<hr><h3><a name="contents308">User authentication</a></h3>
<P>
This is enabled by default using derby's authentication capability. See file 'derby.properties' for details.
The default GaianDB system user/schema is 'gaiandb'. The system password for this user only applies if authentication is enabled.</LI>
</P>

<hr><h3><a name="contents309">User access restriction to chosen databases</a></h3>
<P>
Derby has a <a href="http://db.apache.org/derby/docs/10.8/ref/rrefsetuseraccess.html">mechanism to restrict access by authenticated users to certain designated databases only</a>.
To do this - access must first be given in advance via Derby procedure call, e.g: CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.database.fullAccessUsers', 'GAIANDB').
Note that a GaianDB install includes a 'GAIANDB' database against which this procedure has already been called to allow access by user GAIANDB.
This procedure is also automatically called during startup of a GaianNode if it needed to re-create its own database and after doing so.
After that, this global security feature is switched on by setting (or un-commenting) the appropriate property in derby.properties 
as follows: "derby.database.defaultConnectionMode=noAccess"; and then re-starting the node.
</P>

<hr><h3><a name="contents310">Password scrambling</a></h3>
<P>
All passwords defined in the GaianDB configuration file ('gaiandb_config.properties' by default) are encoded at system startup, and
every new password is also automatically encoded every time an API update call is executed.  The configuration file is automatically updated and saved whenever any of these changes are made.</p>
<p><b>Note</b>: the GaianDB system password itself is defined in 'derby.properties' and is not encoded. However, for connection establishment and maintenance, GaianDB transmits an encoded version of its password to other Gaian Nodes.</p>
</P>


<hr><h2><a name="contents315">Advanced Features</a></h2>

<hr><h3><a name="contents321">Special SQL Query Options (with_provenance, explain, maxDepth, ...)</a></h3>
<p>
Below are all optional logical table arguments and nested query arguments for distributed queries. Refer to the section
on <a href="#contents145">'Issuing Distributed SQL Queries'</a> for details. Note that arguments may be combined in a comma
separated list, e.g:</p>
<pre>select * from new com.ibm.db2j.GaianQuery('select puzzlename, price from puzzles', 'with_provenance, maxSourceRows=10, ORDER BY price', 'SOURCELIST=TOYS') Q</pre>
<p><b>Logical Table Arguments:</b></p>
<table class="data">
	<thead>
		<tr>
		<th>Argument name</th><th>Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
		<td>maxDepth=N</td><td>Use table argument maxDepth=&lt;depth&gt; to specify propagation ripple depth of a distributed query. This takes precedence over the configuration property: 'MAX_PROPAGATION'. 
		<br/>This is particularly useful with subqueries, to instruct each subquery from each node to propagate out to a certain depth. 
		<br/>When no value is specified or a negative value is used, queries will flood the whole network.</td>
		</tr>
		<tr>
		<td>maxSourceRows=N</td><td>The MAXIMUM number of rows that should be retrieved from each individual data source in the network.</td>
		</tr>
		<tr>
		<td>with_provenance</td><td>Requests that the <a href="#contents234">provenance columns</a> be included in the returned results set.</td>
		</tr>
		<tr>
		<td>explain [in &lt;filename.dot&gt;]</td><td>Requests that the <a href="#contents270">explain columns</a> be included in the
	returned results set, and optionally specify a filename to which to write a textual representation of the query route in the 'DOT' language.</td>
		</tr>
		<tr>
		<td>ORDER BY &lt;column list&gt;</td><td>Specifies an order for the rows from each source to be extracted in. This is useful
	in conjunction with 'maxSourceRows' to retrieve a set number of ordered rows from each data source.</td>
		</tr>
	</tbody>
</table>

<p><b><a name="contents342">Nested Query Arguments:</a></b></p>
<table class="data">
	<thead>
		<tr><th>Argument</th><th>Description</th></tr>
	</thead>
	<tbody>
		<tr><td>SOURCELIST=&lt;sourcelist name&gt;</td><td>Use this to specify a list name for data sources. Every GaianDB node that wishes to expose data through this data source list can set the property:<br>
	&lt;sourcelist name&gt;_SOURCELIST=&lt;list of connection ids&gt; to define the comma separated list of RDBMS connection ids which a Nested Query targeting that sourcelist will run its nested query against, e.g.
		<br/>
		<pre>TOYS_SOURCELIST=TOYRUS_DB, HAMLEYS_DB
		
TOYRUS_DB_DRIVER=com.ibm.db2.jcc.DB2Driver
TOYRUS_DB_URL=jdbc:db2://localhost:50000/toysrusdb
TOYRUS_DB_USR=toys
TOYRUS_DB_PWD=passw1rd
		
HAMLEYS_DB_DRIVER=com.mysql.jdbc.Driver
HAMLEYS_DB_URL=jdbc:mysql://localhost:3306/hamleysdb
HAMLEYS_DB_USR=root
HAMLEYS_DB_PWD=passw2rd
		</pre>	
		</td>
		</tr>
	</tbody>
</table>
<br />
<hr><h3><a name="contents234">Provenance Columns: Special columns identifying origin of data rows</a></h3>
<p>All Logical Tables have a number of special columns associated with them which can be used to identify the origin of data rows - these are not visible by default.<br>
The special columns are:
</p>
<table class="data">
	<thead>
 	<tr>
		<th width="137">Column name</th>
		<th width="132">Type</th>
		<th width="638">Description</th>
 	</tr>
 	</thead>
	<tr>
		<td width="137">GDB_NODE </td>
		<td width="132">VARCHAR(20)</td>
		<td width="638">The host name (and port if not the default 6414) of the Gaian Node where the row originated from.</td>
	</tr>
	<tr>
		<td width="137">GDB_LEAF </td>
		<td width="132">VARCHAR(20)</td>
		<td width="638">The File name or JDBC URL and DB Table name or the source of the column data.</td>
	</tr>
</table>

<p>To include these, use option 'with_provenance' in the query or use the managed view with a "_P" suffix. For example, to
retrieve all rows from logical table 'LT0' and have the provenance columns in the returned ResultSet, issue the query:
<pre>select * from new com.ibm.db2j.GaianTable('LT0', 'with_provenance') LT0ALIAS</pre>
which is equivalent to:
<pre>select * from LT0_P</pre>
E.g.
<pre>sql> select * from LT0_P
select * from LT0_P
==================================================================================================================================================
LOCATION                      |MISC                          |NUMBER     |GDB_NODE            |GDB_LEAF                     	                 |
==================================================================================================================================================
111111111                     |12                            |          0|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
WWWWWWWWW                     |32                            |          3|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
991111111                     |72                            |          0|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
SZZZSK_DAVIDSFILE             |22                            |          7|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
AAAAAAAAA                     |3                             |          1|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
CCCCCCCCC                     |5                             |          3|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
SYSK_DATAFILE1!!              |150                           |          4|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
TTTTTTTTT                     |29                            |          2|IBM5JIFD09VU18      |./csvtestfiles/datafile.dat                       |
==================================================================================================================================================
Fetched 8 rows. Total Time: 30ms (Execution Time: 11ms)</pre>
</p>

<br />
<hr><h3><a name="contents270">Explain Queries: Getting and showing the route of a query</a></h3>
<P>An explain query allows a user to obtain information about the route of a query through the network of GaianDB nodes.</p>
<p>To run an explain query, use option 'explain' in the query or use the managed view with a "_X" suffix. When issuing an explain query, you can only query against the set of EXPLAIN columns:</p>

<table class="data">
	<thead>
		<tr>
			<th width="137">Column name</th>
			<th width="638">Description</th>
		</tr>
 	</thead>
	<tbody>
		<tr>
			<td>GDBX_FROM_NODE</td>
			<td>The origin NodeID of a path segment, or &ltSQL QUERY&gt if the origin is the querying client process.</td>
		</tr>
		<tr>
			<td>GDBX_TO_NODE</td>
			<td>The destination NodeID of a path segment.</td>
		</tr>
		<tr>
			<td>GDBX_PRECEDENCE</td>
			<td>The precedence of the route ending in this path segment over other alternate routes leading to the same destination nodeID. The value may be 'F' (first to reach node (maybe via a long route)), 'S' (shorter), 'L' (longer).</td>
		</tr>
		<tr>
			<td>GDBX_DEPTH</td>
			<td>The number of segments/hops/edges that were traversed and ending in this segment. When GDBX_FROM_NODE is &ltSQL QUERY&gt then GDBX_DEPTH is 0.</td>
		</tr>
		<tr>
			<td>GDBX_COUNT</td>
			<td>The cumulative number of records retrieved through this path segment as a result of running the query. The GDBX_COUNT for the path segment at depth 0 gives the total number of records retrieved.</td>
		</tr>
	</tbody>
</table>
<p>Here is an example:</p>
<PRE>select GDBX_FROM_NODE, GDBX_TO_NODE from new com.ibm.db2j.GaianTable('LT0', 'explain') GT</pre>

This is equivalent to using the managed view for explain queries on logical table 'LTO' (use suffix "_X"):

<pre>select GDBX_FROM_NODE, GDBX_TO_NODE from T0_X</PRE>

<P><b>Note</b>: a 'select *' explain query will return the explain rows with the explain columns filled in but also every
other column of the table with null entries (as they do not make sense in the context of an explain query).</P>
	
<p><B>Query Route Visualisation:</B></p>
	<p>In order to visualise the query route, you may also specify a file name at query execution time, e.g.
	<pre>select GDBX_FROM_NODE, GDBX_TO_NODE from new com.ibm.db2j.GaianTable('LT0', 'explain in graph.dot') GT</pre>
	This will write the file in the DOT script language to the directory where the GaianDB server was launched from. This DOT file holds a simple text representation of a graph that shows the route of a query through the network of GaianDB nodes.
	Programs such as GraphViz, which can be downloaded from:
	<a href="http://www.graphviz.org/Download.php">http://www.graphviz.org/Download.php</a>, can then produce an image in a variety of
	different formats (jpg, gif, svg, ...) from the DOT script (Fig.6 ).
    <br/><br />
     <center>
     <TABLE class='image'>
     <TR class='image'><TD class='image'><a Href="./images/explain2.gif"><img src="./images/explain2.gif" ></TD></TR>
     <TR class='image'><TD class='image' align='center'>Fig. 6 - GaianDB Explain Examples with GraphViz</TD></TR>
    </TABLE>
    </center>
	<p>As a shorthand, you can use the managed view with a "_XF" prefix to automatically run an explain query and write the results to a 'graph.dot' file in the directory where the GaianDB server was launched from. For example:</p>
	<pre>select * from LT0_XF</pre>
	<br />
	
<hr><h3><a name="contents273">Specifying advanced table and column mappings</a></h3>
<p>When defining a table you can specify a number of advanced column mappings, for example to define a column that holds a constant value, or one that is the result of executing a function based upon the value held in another column.
</br>
Here is an example configuration:</p>
<pre>
LTDAT2_DEF=COLUMN1 VARCHAR(255), BLAH VARCHAR(255), COLUMN3 VARCHAR(255), COLUMN4 VARCHAR(255), COLUMN5 VARCHAR(255), COLUMN6 VARCHAR(255), COLUMN7 VARCHAR(255), COLUMN8 VARCHAR(255), REFERENCE INT
LTDAT2_CONSTANTS=

LTDAT2_DS0_CONNECTION=LOCALDERBY new com.ibm.db2j.FileImport('C:/GAIANDB-2/csvtestfiles/datafile.dat') F
LTDAT2_DS0_OPTIONS= MAP_COLUMNS_BY_POSITION

#Specify  that first column has constant String value 'Lucky7'
LTDAT2_DS0_C1='Lucky7'
#Specify that column 9 has the constant value 12
LTDAT2_DS0_C9=12
#Specify that column 7 is a substring of the value in column 2
LTDAT2_DS0_C7=substr(COLUMN2, 3, 5)
</pre>
In this instance column1 will always hold 'Lucky7', column 9 will always hold the value '12', and column 7 will use a substring of the value in column 2 of the physical file.
These will in effect become constant columns values for the data source.
<br>
You can also use the SQL API calls to achieve similar configuration:
<PRE>
    call setlt('LTDAT2', 'COLUMN1 VARCHAR(255), BLAH VARCHAR(255), COLUMN3 VARCHAR(255), COLUMN4 VARCHAR(255), COLUMN5 VARCHAR(255), COLUMN6 VARCHAR(255), COLUMN7 VARCHAR(255), COLUMN8 VARCHAR(255), REFERENCE INT', '')
    
    call setdsrdbtable(
        'LTDAT2',
        '0',  <i>--You can use FILE1 or any other identifier here to defined the datasource name.</i>
        'LOCALDERBY', 
        'new com.ibm.db2j.FileImport(''C:/GAIANDB-2/csvtestfiles/datafile.dat'') F', 
        'MAP_COLUMNS_BY_POSITION', 
        '''Lucky7'', C9=12, C7  = substr(COLUMN2,3,5)'
    )
</PRE>
<B>Note:</B> that all explicitly defined column mappings (6th argument) override option 'MAP_COLUMNS_BY_POSITION'. 
  The explicit mappings themselves are positional unless a further explicit column index specifier is given (e.g. "C9=")
  Also - white space is trimmed wherever appropriate... (e.g. "C7=x" is equivalent to " C7  	= x ")
<p>
 Here is a screenshot of a SELECT against both API calls:
<center>
<TABLE class='image'>
   <TR class='image'>
     <TD class='image'><a Href="./images/gaiandb7.gif"><img src="./images/gaiandb7.gif"  ></TD>
   <TR class='image'>
     <TD class='image' align='center'>Fig. 7 - Results of column mapping with constant columns</TD>
</TABLE>
</center>
<P>
Here is another example where we add an new RDBMS connection (in this example a DB2 database)  and a extra table data source to LTDAT2 with some columns mappings:
<PRE>
call setrdbc('DB2C', 'com.ibm.db2.jcc.DB2Driver', 'jdbc:db2://localhost:50000/sample', 'db2usr', 'db2paswd')

call setdsrdbtable(
	'LTDAT2',
	'DB2DS1',
	'DB2C',
	'EMPLOYEE',
	'MAP_COLUMNS_BY_POSITION',
	'''Lucky9'', C7  = substr(FIRSTNME,3,5)'
)
</PRE>
These API calls above will create the following configuration :
<PRE>
DB2C_DRIVER=com.ibm.db2.jcc.DB2Driver
DB2C_URL=jdbc:db2://localhost:50000/sample
DB2C_USR=db2usr
#scrambled password
DB2C_PWD='FJ[;I9EG

LTDAT2_DSDB2DS1_CONNECTION=DB2C EMPLOYEE
LTDAT2_DSDB2DS1_OPTIONS=MAP_COLUMNS_BY_POSITION
LTDAT2_DSDB2DS1_C1='Lucky9'
LTDAT2_DSDB2DS1_C7=substr(FIRSTNME,3,5)
</PRE>
<p>
 Here is now a screenshot of a SELECT against LTDAT2 after these extra API calls: 
 <p>
 <b>Note:</b> in Blue some of the new records from the DB2 EMPLOYEE table (not all are shown).
<center>
<TABLE class='image'>
   <TR class='image'>
     <TD class='image'><a Href="./images/gaiandb8.gif"><img src="./images/gaiandb8.gif"  ></TD>
   <TR class='image'>
     <TD class='image' align='center'>Fig. 8 - Results of column mappings with constant columns from 2 datasources</TD>
</TABLE>
</center>


<br/>

<hr><h3><a name="contents274">SQL Query as a Logical Table Data Source</a></h3>
<p>The <code>setltforrdbtable</code> stored procedure can be used to federate the result of a SQL Query as the data source to a Logical Table.</p>

Command syntax:
<pre>
sql> call setltforrdbtable(&lt;New Logical Table Name&gt;, &lt;Database Connection&gt;, &lt;Selection Predicate&gt;)
</pre>
The following example defines a data source returning query results from <code>select * from employee where isManager='Y'</code>. This format only works where there is a single table in the Selection Predicate. 
<pre>sql> call setltforrdbtable('db2employee', 'db2conn', 'employee where isManager=''Y''')
</pre>

If a Join is required then the selection predicate should be specified as a select query in brackets, followed by an alias. 
The following example is the equivalent of executing <code>select * from (select e.id, e.name, d.name employee as e, department as d where e.deptid=d.deptid) q</code>. The "q" is the query alias

<pre>
sql> call setltforrdbtable('db2employee', 'db2conn', '(select e.id, e.name, d.name employee as e, department as s where e.deptid=d.deptid) q')
</pre>

</hr>

<hr><h3><a name="contents275">Message Storer: Message Broker Integration (e.g. use with sensors)</a></h3>
<p>GaianDB can use the IBM Microbroker client to subscribe to messages coming from sensors or any message queue and persist the data locally.</p>

<h4>Description</h4>
<p>The message storing functionality is enabled if the properties MSGBROKER_HOST and MSGBROKER_PORT are set. The topic can be specified on the command line (using -mt <topic>) or by setting the MSGBROKER_TOPIC property.</p>
<p>The messages received by GaianDB are written to a local Derby table called BROKER_MSGS using the Gaian node's schema; so, for a node called GAIANDB, the table will be GAIANDB.BROKER_MSGS.</p>
<p>To control the amount of storage used by the database, stored messages can be set to expire by using the MSGSTORER_ROWEXPIRY_HOURS property.</p>
<p>The schema for the BROKER_MSGS table can be changed to store parts of the message if required. The property MSGSTORER_MSGCOLS allows the user to define additional columns where those parts can be stored. A regular expression (regex) like string is used to match message formats as well as embedded Timestamp formats. Currently the format string can only be used to split messages which have comma delimiters.</p>

Finally, each message is added to the BROKER_MSGS table as follows:
<ul>
<li>The topic is stored in its own column. 
<br/>If the topic string has '/' separators the string is split and each sub-topic is as well stored in its own column.</li>
<li>The message is stored in its own column.</li>
</ul>

<h4>Installation</h4>
<ul>
<li>Download the <a href="http://www-01.ibm.com/support/docview.wss?rs=171&uid=swg24006006&loc=en_US&cs=utf-8&lang=en">IA92: WBI Brokers - Java implementation of WebSphere MQ Telemetry transport</a> SupportPac.</li>
<li>Unzip the ia92.zip file, navigate to the J2SE directory and copy the wmqtt.jar file into the GaianDB install's lib directory.</li>
<li>Edit the launchGaianServer script for your platform and make sure the 'wmqtt.jar' is added to the CLASSPATH variable.</li>
<li>Add the MSGBROKER_* properties to the gaiandb_config.properties (see below).</li>
<li>Start or restart your GaianDB node to load the new settings.</li>
</ul>

<h4>An example</h4>
<p>Our GaianDB node will subscribe to the topic <code>transactions/#</code> on broker host <code>mybroker.mydomain.com</code> on port <code>1883</code> and the messages will expire after 24 hours.
As well, we want to extract some data from the message and store it individually. We'd like to extract and store the <code>Firstname</code>, <code>Surname</code> and <code>Timestamp</code>.</p>

<p>We add the following lines to the gaiandb_config.properties file for our node:
<pre>
MSGBROKER_HOST=mybroker.mydomain.com
MSGBROKER_PORT=1883
MSGBROKER_TOPIC=transactions/#   # For more information on topic formats see the IBM documentation on <a href="http://publib.boulder.ibm.com/infocenter/wmqv7/v7r0/index.jsp?topic=%2Fcom.ibm.mq.amqtat.doc%2Ftt60330_.htm">Topic Strings</a>.
MSGSTORER_ROWEXPIRY_HOURS=24     # Define an expiry period for stored messages
MSGSTORER_MSGCOLS=', Firstname VARCHAR(20), Surname VARCHAR(20), tstamp TIMESTAMP (yyyyMMdd,HHmmss.SSS)'   # Define more columns to store parts of the message
</pre>
</p>
<p>The GaianDB node is restarted to load the new settings. At startup, the node will subscribe to the topic.</p>
<p>The first message reaches the node on topic 'transactions/atm/bristol':
<br/><code>'Bristol, John, Smith, 20070919,201554.514, 500'</code></p>

<p>The BROKER_MSGS table will be created with the following columns and the values for the first message inserted:</p>
<pre>
====================================================================================================================
|TOPIC        |T1  |T2      |T3   |T4   |T5   |MESSAGE        |MSG_RECEIVED     |Firstname |Surname |tstamp        |
====================================================================================================================
|&lt;full topic&gt; |atm |bristol |null |null |null |&lt;full message&gt; |&lt;insertion time&gt; |John      |Smith   |1190229354514 |
====================================================================================================================
</pre>
<p>Every subsequent message will be stored in a similar manner.</p>

<br />
<hr><h3><a name="contents401">Custom VTIs</a></h3>
<p>
It is possible to expand the types of data sources that GaianDB is able to federate by creating custom 
Virtual Table Interfaces (VTIs) for them. This section details the custom VTIs that come as part of the GaianDB.</p>

<hr><h4><a name="contents402">IBM Content Analytics Restful Interface (ICAREST)</a></h4>
<p>IBM Content Analytics is an advanced search and analytics platform. The ICAREST VTI integrates with the IBM Content 
Analytics restful web interface to enable its use as a GaianDB data source.</p>
<p>There are four types of query that are supported:</p>
<ul>
<li><i>search</i> - document keyword search</li>
<li><i>count</i> - document keyword search result count</li>
<li><i>doctext</i> - document text retrieval</li>
<li><i>docbytes</i> - document bytes retrieval</li>
</ul>
<p>To configure the ICAREST VTI for use, you need to specify the URL to query for each type of query. This is done by adding the 
following properties in the appropriate gaiandb_config.properties file:</p>
<pre>
ICAREST.search.url=http://localhost:8394/api/v10/search?output=application/xml&scope=All&query=$0
ICAREST.count.url=http://localhost:8394/api/v10/search?output=application/xml&scope=All&query=$0
ICAREST.doctext.url=http://localhost:8394/api/v10/search/preview?query=search&collection=$0
ICAREST.docbytes.url=http://localhost:8393/search/ESFetchServlet?cid=$0
</pre>
<p>The ICAREST VTI can then be invoked using the form:</p>
<pre>
select * from new com.ibm.db2j.ICAREST('<i>query type</i>,<i>query parameters</i>') IR
</pre>
<p>For example:</p>
<pre>
--Search for all documents containing the text 'coconuts'
select * from new com.ibm.db2j.ICAREST('search,coconuts') IR
</pre>
<p><b>Note:</b> The query parameters are specified as a comma separated list and will be subsituted into the 
underlying 'query' (in this case, the URL to use) in place of $0, $1, $... appropriately.</p>
<p>There are additional optional parameters than can be specified. Where not specified, sensible default values will be used.</p>
<ul>
	<li>
		<b>Fetch batch size:</b><br />
		This defines the number of results that are fetched per-request to the IBM Content Analytics restful web 
		interface. This also represents the maximum number of results that will be passed to the 
		<a href="#contents404">SQL_RESULT_FILTER</a>, if one is specified.<br />
		This parameter should be tweaked based on the speed of your IBM Content Analytics restful web interface and
		filtering implementation.<br />
		The default value is 10 and a custom value can be defined by specifying the '&results=' query parameter on the
		URL for the appropriate query type in the gaiandb_config.properties file, as follows:
<pre>
#Fetch 1000 search results at a time
ICAREST.search.url=http://localhost:8394/api/v10/search?output=application/xml&scope=All&query=$0<b>&results=1000</b>
</pre>
	</li>
</ul>
<ul>
	<li>
		<b>Fetch buffer size:</b><br />
		This defines the maximum number of result batches that are held in memory at one time; waiting for Derby to 
		consume them. The main use of this parameter is to protect against memory over-use on resource constrained 
		systems.<br />		
		The default value is 20 and a custom value can be defined in the gaiandb_config.properties file as follows:
<pre>
#Buffer a max of 20 batches of fetches in memory
ICAREST.fetchbuffersize=20
</pre>
		<p>Caching has an important effect on the underlying behaviour and performance of this VTI:</p>
		When caching is enabled, the behaviour of the VTI is as follows:
		<ul>
			<li>Query the restful web interface as fast as possible (in batches of 'fetch batch size').</li>
			<li>Store the results to the cache on disk as they are retrieved.</li>
			<li>Asynchronously filter the results (if required) and populate the in memory buffer as much as possible 
			(waiting for more space on the buffer, as Derby consumes the previous result batches, or more 
			results from the restful interface).</li>
		</ul>
		<br />
		When caching is <u>disabled</u>, this parameter has a much greater effect and the behaviour of the VTI is 
		as follows:
		<ol>
			<li>Query the restful web interface for a batch.</li>
			<li>Filter the result batch, if necessary.</li>
			<li>Attempt to synchronously populate the in memory buffer with the batch. Waiting until there is more
			space on the buffer, as Derby consumes the previous result batches, or there aremore results from the restful interface.</li>
			<li>Repeat steps 1 - 3 until all results are retrieved.</li>
		</ol>
		<br />
		</li>
</ul>
<hr><h4><a name="contents403">Spatial Query</a></h4>
<p>
A spatial database is optimized to store and query data that is related to objects in space; including points, lines 
and polygons. The Spatial Query VTI enables the use of spatial databases in DB2 and Oracle as GaianDB data sources.</p>
<p>There are two types of query that are supported:</p>
<ul>
<li><i>distance</i> - takes two geometries and returns the shortest distance between any point in the first geometry to any point in the second geometry.</li>
<li><i>within</i> - takes two geometries as input parameters and returns 1 if the first geometry is completely within the second geometry. Otherwise, 0 (zero) is returned.</li>
</ul>
<p>The geometries can be specified as references or GML.</p>
<p>To configure the Spatial Query VTI for use, you need to specify the RDBMS source for GaianDB to query against.
This is done by adding the following properties in the appropriate gaiandb_config.properties file:</p>
<pre>
SpatialQuery.SOURCE=GEODB1
</pre>
<p>This should reference a RDBMS source defined in the gaiandb_config.properties file, or created using the 
'call setrdbc(...)' command, as in <a href="#contents53">this example</a>.</p>
<p>The Spatial Query VTI can then be invoked using the form:</p>
<pre>
select * from new com.ibm.db2j.SpatialQuery('<i>query type</i>,<i>query parameters</i>') SQ
</pre>
<p><b>Note:</b> The query parameters are specified as a comma separated list and will be subsituted into the 
underlying 'query' (in this case, the DB2 or ORACLE spatial query to issue, see below) in place of $0, $1, $... 
appropriately.</p>
<p>There are additional optional parameters than can be specified. Where not specified, sensible default values will be used.</p>
<ul>
	<li>
		<b>The underlying spatial queries</b><br />
		These specify the actual spatial queries that GaianDB issues against the RDBMS source, with the appropriate
		query parameters substituted in place.<br />
		Custom values can be defined in the gaiandb_config.properties file as follows:
<pre>
#DB2 spatial queries - one of these will be picked if the driver indirectly reference by the SOURCE property is recognised to be DB2 

#Example "within" query when geometries are provided as GML
SpatialQuery.DB2.SQL.WITHIN.GML=\
select ref, dnum from esadmin.geo_table where db2gse.st_within(geo, db2gse.st_geometry( cast ('$0' as clob(2g)), db2gse.st_srsid(geo)) )=1
<p/>
#Example "within" query when geometries are provided as REF
SpatialQuery.DB2.SQL.WITHIN.REF=\
select g1.ref, g1.dnum from esadmin.geo_table g1, esadmin.geo_table g2 where db2gse.st_within(g1.geo, g2.geo)=1 and g2.ref='$0'
<p/>
#Example "distance" query when geometries are provided as GML
SpatialQuery.DB2.SQL.DISTANCE.GML=\
select ref, dnum from esadmin.geo_table where db2gse.st_distance(geo, db2gse.st_geometry( cast('$0' as clob(2g)), db2gse.st_srsid(geo) ), '$2')<$1
<p/>
#Example "distance" query when geometries are provided as REF
SpatialQuery.DB2.SQL.DISTANCE.REF=\
select g1.ref, g1.dnum from esadmin.geo_table g1, esadmin.geo_table g2 where db2gse.st_distance(g1.geo, g2.geo, '$2')<$1 and g2.ref='$0'
<p/>
##########################################################################################################################################

#Oracle spatial queries - one of these will be picked if the driver indirectly reference by the SOURCE property is recognised to be ORACLE

SpatialQuery.ORACLE.SQL.WITHIN.GML=...
SpatialQuery.ORACLE.SQL.WITHIN.REF=...
SpatialQuery.ORACLE.SQL.DISTANCE.GML=...
SpatialQuery.ORACLE.SQL.DISTANCE.REF=...
<p/>
##########################################################################################################################################

SpatialQuery.cache.expires=600
SpatialQuery.DISTANCE.UNIT=KILOMETER
<p/>
SpatialQuery.SOURCE=GEODB1
<p/>
GEODB1_DRIVER=com.ibm.db2.jcc.DB2Driver
GEODB1_URL=jdbc:db2://localhost:50001/AFGIS
GEODB1_USR=DavidVyvyan
GEODB1_PWD='0x1F@^D>
</pre>
	</li>
</ul>
<hr><h2><a name="contents325">Supported RDBMS Data sources</a></h2>
<p>
All Relational Database Management Systems (RDBMS) that have a client JDBC driver should work with GaianDB.</p>
<p>
The following RDBMS providers and preferred JDBC drivers have been tested:
</p>
<ul>
   <li>Apache Derby 10.5.x, 10.8.3.1 (with included JDBC drivers)</li>
   <li>IBM DB2 8.x, 9.x, 10.5 (with included JDBC drivers)</li>
   <li>Microsoft SQL Server (Express 2005 & 2008) - with JDBC library: sqljdbc4.jar</li>
   <li>MySQL 5.1, 5.6 - with JDBC library: mysql-connector-java-5.1.25-bin.jar</li>
   <li>Oracle 10g, XE 11.2 - with JDBC library: ojdbc6.jar</li>
</ul>
<br/>


<hr><h2><a name="contents330">Supported SQL Types for Logical Tables Definitions</a></h2>
<ul>
<li>This is the list of SQL types supported in GaianDB Logical Table definitions, along side the equivalent SQL types for each RDBMS supported by GaianDB.</li><p/>
<table class='data'>
	<thead>
		<tr>
			<th>GaianDB SQL Types</th>
			<th colspan=2>Apache Derby 10.8</th>
			<th colspan=2>IBM DB2 10.5</th>
			<th colspan=2>Oracle 11g</th>
			<th colspan=2>MySQL 5.6</th>
			<th colspan=2>Microsoft SQL Server 2008</th>
		</tr>
 	</thead>
 	<tbody>
 		<tr>
 			<th>CHAR[ACTER](n)</th>
 			<td class="green"></td>
 			<td><b>CHAR(n)</b><br> where 1 &lt; n &lt; 254, default is 1</td>
 			<td class="green"></td>
 			<td><b>CHAR(n)</b><br> where 1 &lt; n &lt; 254, default is 1</td>
 			<td class="orange"></td>
 			<td><b>CHAR(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>TINYTEXT</b>,<br><b>TEXT(n)</b>,<br><b>CHAR(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>CHAR(n)</b>,<br><b>TEXT(n)</b>(will be deprecated) <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>VARCHAR(n)</th>
 			<td class="green"></td>
 			<td><b>VARCHAR(n)</b><br> where 1 &lt; n &lt; 32672</td>
 			<td class="green"></td>
 			<td><b>VARCHAR(n)</b><br> where 1 &lt; n &lt; 32672</td>
 			<td class="orange"></td>
 			<td><b>VARCHAR2(n)<br>VARCHAR(n)<br>CHAR VARYING(n)<br>CHARACTER VARYING(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>TEXT(n)</b>,<br><b>VARCHAR(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>VARCHAR(n)</b> <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>LONGVARCHAR</th>
 			<td class="green"></td>
 			<td><b>LONG VARCHAR</b><br>max length 32700</td>
 			<td class="orange"></td>
 			<td><b>LONG VARCHAR</b> (deprecated)</td>
 			<td class="orange"></td>
 			<td><b>LONG</b> (deprecated), use <b>CLOB/NCLOB</b></td>
 			<td class="orange"></td>
 			<td><b>TEXT(n)</b>,<br><b>MEDIUMTEXT</b>,<br><b>VARCHAR(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>VARCHAR(n)</b> <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>BINARY</th>
 			<td class="green"></td>
 			<td><b>CHAR(n) FOR BIT DATA</b>,<br> where 1 &lt; n &lt; 254, default 1</td>
 			<td class="green"></td>
 			<td><b>CHAR(n) FOR BIT DATA</b>,<br> where 1 &lt; n &lt; 254, default 1</td>
 			<td class="orange"></td>
 			<td><b>RAW(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>BINARY(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>BINARY(n)</b> <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>VARBINARY(n)</th>
 			<td class="green"></td>
 			<td><b>VARCHAR(n) FOR BIT DATA</b>,<br> where 1 &lt; n &lt; 32672</td>
 			<td class="green"></td>
 			<td><b>VARCHAR(n) FOR BIT DATA</b>,<br> where 1 &lt; n &lt; 32672</td>
 			<td class="orange"></td>
 			<td><b>RAW(n)</b> <a href="#footnote-1">[1]</td>
 			<td class="orange"></td>
 			<td><b>VARBINARY(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>VARBINARY(n)</b> <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>LONGVARBINARY</th>
 			<td class="green"></td>
 			<td><b>LONG VARCHAR FOR BIT DATA</b>,<br>max length 32700</td>
 			<td class="green"></td>
 			<td><b>LONG VARCHAR FOR BIT DATA</b>,<br>max length 32700</td>
 			<td class="orange"></td>
 			<td><b>RAW(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>BLOB(n)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>BINARY(n)</b>,<br><b>VARBINARY(n)</b> <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>BIGINT</th>
 			<td class="green"></td>
 			<td><b>BIGINT</b><br>-9223372036854775808 <br>to 9223372036854775807</td>
 			<td class="green"></td>
 			<td><b>BIGINT</b><br>-9223372036854775808 <br>to 9223372036854775807</td>
 			<td class="green"></td>
 			<td><b>NUMBER(p)</b> where 10 &lt;= p &lt; 19</td>
 			<td class="green"></td>
 			<td><b>BIGINT</b></td>
 			<td class="green"></td>
 			<td><b>BIGINT</b></td>
 		</tr>
 		<tr>
 			<th>INT[EGER]</th>
 			<td class="green"></td>
 			<td><b>INTEGER</b><br>-2147483648 to 2147483647</td>
 			<td class="green"></td>
 			<td><b>INTEGER</b><br>-2147483648 to 2147483647</td>
 			<td class="green"></td>
 			<td><b>INTEGER</b><br><b>NUMBER(p)</b> where 5 &lt;= p &lt; 10</td>
 			<td class="green"></td>
 			<td><b>INT[EGER]</b></td>
 			<td class="green"></td>
 			<td><b>INT</b></td>
 		</tr>
 		<tr>
 			<th>SMALLINT</th>
 			<td class="green"></td>
 			<td><b>SMALLINT</b><br>-32768 to 32767</td>
 			<td class="green"></td>
 			<td><b>SMALLINT</b><br>-32768 to 32767</td>
 			<td class="green"></td>
 			<td><b>SMALLINT</b><br><b>NUMBER(p)</b> where p &lt; 5</td>
 			<td class="green"></td>
 			<td><b>SMALLINT</b></td>
 			<td class="green"></td>
 			<td><b>SMALLINT</b></td>
 		</tr>
 		<tr>
 			<th>TINYINT</th>
 			<td class="red"></td>
 			<td>n/a</td>
 			<td class="red"></td>
 			<td>n/a</td>
 			<td class="green"></td>
 			<td><b>NUMBER(3)</b></td>
 			<td class="green"></td>
 			<td><b>TINYINT</b></td>
 			<td class="green"></td>
 			<td><b>TINYINT</b></td>
 		</tr>
 		<tr>
 			<th>DOUBLE</th>
 			<td class="green"></td>
 			<td><b>DOUBLE</b><br>-1.79769e+308 to 1.79769e+308 <br>& 2.225e-307 to -2.225e-307</td>
 			<td class="green"></td>
 			<td><b>DOUBLE</b><br>-1.79769e+308 to 1.79769e+308 <br>& 2.225e-307 to -2.225e-307</td>
 			<td class="green"></td>
 			<td><b>DOUBLE PRECISION</b>,<br><b>NUMBER</b>,<br><b>FLOAT</b> <a href="#footnote-1">[1]</a></td>
 			<td class="green"></td>
 			<td><b>DOUBLE [PRECISION]</b></td>
 			<td class="green"></td>
 			<td><b>FLOAT</b></a></td>
 		</tr>
 		<tr>
 			<th>FLOAT(p)</th>
 			<td class="green"></td>
 			<td><b>FLOAT(p)</b><br>precision &lt; 23 = REAL,<br>precision &gt; 24 = DOUBLE,<br>default precision is 53</td>
 			<td class="green"></td>
 			<td><b>DOUBLE</b></td>
 			<td class="green"></td>
 			<td><b>FLOAT(p)</b></td>
 			<td class="orange"></td>
 			<td><b>FLOAT(p)</b> <a href="#footnote-1">[1]</a></td>
 			<td class="green"></td>
 			<td><b>FLOAT(p)</b> <a href="#footnote-1">[1]</a></td>
 		</tr>
 		<tr>
 			<th>FLOAT</th>
 			<td class="green"></td>
 			<td><b>FLOAT</b><br>-1.79769e+308 to 1.79769e+308 <br>& 2.225e-307 to -2.225e-307</td>
 			<td class="green"></td>
 			<td><b>FLOAT</b><br>-1.79769e+308 to 1.79769e+308 <br>& 2.225e-307 to -2.225e-307</td>
 			<td class="green"></td>
 			<td><b>DOUBLE PRECISION</b>,<br><b>FLOAT</b></td>
 			<td class="green"></td>
 			<td><b>DOUBLE</b></td>
 			<td class="green"></td>
 			<td><b>FLOAT</b></td>
 		</tr>
 		<tr>
 			<th>DEC[IMAL](p,s),<br>NUMERIC(p,s)</th>
 			<td class="green"></td>
 			<td><b>DECIMAL</b>,<br><b>NUMERIC</b><br>1 &lt; precision &lt; 31,<br>scale &lt;= precision,<br>precision default = 5,<br>scale default = 0</td>
 			<td class="orange"></td>
 			<td><b>DECIMAL</b>,<br><b>NUMERIC</b>,<br><b>DECFLOAT</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>DECIMAL</b>,<br><b>NUMERIC</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>DECIMAL</b> <a href="#footnote-1">[1]</td>
 			<td class="green"></td>
 			<td><b>DECIMAL</b>,<br><b>NUMERIC</b></td>
 		</tr>
 		<tr>
 			<th>REAL</th>
 			<td class="green"></td>
 			<td><b>REAL</b><br>-3.402e+38 to 3.402e+38,<br>& 1.175e+37 to -1.175e+37</td>
 			<td class="green"></td>
 			<td><b>REAL</b><br>-3.402e+38 to 3.402e+38,<br>& 1.175e+37 to -1.175e+37</td>
 			<td class="green"></td>
 			<td><b>REAL</b></td>
 			<td class="green"></td>
 			<td><b>FLOAT</b></td>
 			<td class="green"></td>
 			<td><b>REAL</b></td>
 		</tr>
 		<tr>
 			<th>BLOB(length)</th>
 			<td class="green"></td>
 			<td><b>BLOB</b><br>where 1 &lt; length &lt; 2,147,483,647 (2GB)<br> length can be sufffixed with {K |M |G}<br>default = 2GB</td>
 			<td class="green"></td>
 			<td><b>BLOB</b><br>2GB</td>
 			<td class="orange"></td>
 			<td><b>BLOB</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>BLOB</b>,<br><b>TINYBLOB</b>,<br><b>MEDIUMBLOB</b>,<br><b>LONGBLOB</b>  <a href="#footnote-1">[1]</td>
 			<td class="green"></td>
 			<td><b>VARBINARY(max)</b>,<br><b>IMAGE</b></td>
 		</tr>
 		<tr>
 			<th>CLOB(length)</th>
 			<td class="green"></td>
 			<td><b>CLOB</b><br>where 1 &lt; length &lt; 2,147,483,647 (2GB)<br> length can be sufffixed with {K |M |G}<br>default = 2GB</td>
 			<td class="green"></td>
 			<td><b>CLOB</b><br>2GB</td>
 			<td class="orange"></td>
 			<td><b>CLOB</b> <a href="#footnote-1">[1]</a></td>
 			<td class="orange"></td>
 			<td><b>TEXT</b>,<br><b>TINYTEXT</b>,<br><b>MEDIUMTEXT</b>,<br><b>LONGTEXT</b> <a href="#footnote-1">[1]</a></td>
 			<td class="green"></td>
 			<td><b>VARBINARY(max)</b>,<br><b>TEXT</b></td>
 		</tr>
 		<tr>
 			<th>DATE</th>
 			<td class="green"></td>
 			<td><b>DATE</b><br>formats:<br>yyyy-mm-dd,<br>mm/dd/yyy,<br>dd.mm.yyyy</td>
 			<td class="green"></td>
 			<td><b>DATE</b><br>formats:<br>yyyy-mm-dd,<br>mm/dd/yyy,<br>dd.mm.yyyy</td>
 			<td class="red"></td>
 			<td>n/a</td>
 			<td class="green"></td>
 			<td><b>DATE</b></td>
 			<td class="green"></td>
 			<td><b>DATE</b></td>
 		</tr>
 		<tr>
 			<th>TIME</th>
 			<td class="green"></td>
 			<td><b>TIME</b><br>formats:<br>hh:mi[:ss],<br>hh.mi[.ss],<br>hh[:mi] {AM|PM}</td>
 			<td class="green"></td>
 			<td><b>TIME</b><br>formats:<br>hh:mi[:ss],<br>hh.mi[.ss],<br>hh[:mi] {AM|PM}</td>
 			<td class="green"></td>
 			<td><b>TIME</b></td>
 			<td class="green"></td>
 			<td><b>TIME</b></td>
 			<td class="green"></td>
 			<td><b>TIME</b></td>
 		</tr>
 		<tr>
 			<th>TIMESTAMP</th>
 			<td class="green"></td>
 			<td><b>TIMESTAMP</b><br>formats:<br>yyyy-mm-dd hh:mi:ss[.nnnnnn],<br>yyyy-mm-dd-hh.mi.ss[.nnnnnn]</td>
 			<td class="green"></td>
 			<td><b>TIMESTAMP</b><br>formats:<br>yyyy-mm-dd hh:mi:ss[.nnnnnn],<br>yyyy-mm-dd-hh.mi.ss[.nnnnnn]</td>
 			<td class="green"></td>
 			<td><b>TIMESTAMP</b>,<br><b>DATE</b></td>
 			<td class="green"></td>
 			<td><b>DATETIME</b>,<br><b>TIMESTAMP</b></td>
 			<td class="green"></td>
 			<td><b>DATETIME</b>,<br><b>DATETIME2</d>,<br><b>SMALLDATETIME</b></td>
 		</tr>
 		<tr>
 			<th>BIT</th>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 			<td class="green"></td>
 			<td><b>BIT</b></td>
 			<td class="green"></td>
 			<td><b>BIT</b></td>
 		</tr>
 		<tr>
 			<th>BOOLEAN</th>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 			<td class="green"></td>
 			<td><b>BOOL[EAN]</b></td>
 			<td class="red"></td>
 			<td><a href="#footnote-2">[2]</a></td>
 		</tr>
 	</tbody>
</table>
<p id="footnote-1" class="footnote">[1] Restricted to Derby's range for this type. Truncation or overflow may happen if larger values than Derby can handle are used.</p>
<p id="footnote-2" class="footnote">[2] No equivalent, but the concept of a BOOLEAN and BIT types can be created using INTEGER, SMALLINT, TINYINT, CHAR(1), NUMBER(1), BIT (when present) etc ...</p>
<p/>
<li>This is the list of SQL and native RDBMS types which are dealt with differently by GaianDB:</li><p/>

<table class="data">
	<thead>
		<tr>
			<th>Provider</th>
			<th>Native Types</th>
			<th colspan=2>GaianDB behaviour</th>
		</tr>
 	</thead>
 	 	<tbody>
 		<tr>
 			<th>SQL Standard</th>
 			<td>ARRAY</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr>
 			<th>SQL Standard</th>
 			<td>DATALINK</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr>
 			<th>SQL Standard</th>
 			<td>DISTINCT</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
  		<tr>
 			<th>SQL Standard</th>
 			<td>JAVA_OBJECT</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr>
 			<th>SQL Standard</th>
 			<td>OTHER</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr>
 			<th>SQL Standard</th>
 			<td>REF</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr>
 			<th>SQL Standard</th>
 			<td>STRUCT</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr class="odd">
 			<td colspan=4></td>
 		</tr>
 		 <tr>
 			<th>DB2</th>
 			<td>DECFLOAT</td>
 			<td class="green"></td>
 			<td>Converted to DECIMAL(31,0)</td>
 		</tr>
 		<tr>
 			<th>DB2</th>
 			<td>VARGRAPHIC</td>
 			<td class="green"></td>
 			<td>DB2 JDBC Driver converts it to VARCHAR</td>
 		</tr>
 		<tr>
 			<th>DB2</th>
 			<td>GRAPHIC</td>
 			<td class="green"></td>
 			<td>DB2 JDBC Driver converts it to VARCHAR</td>
 		</tr>
 		<tr>
 			<th>DB2</th>
 			<td>DBCLOB</td>
 			<td class="green"></td>
 			<td>DB2 JDBC Driver converts it to VARCHAR</td>
 		</tr>
 		<tr class="odd">
 			<td colspan=4></td>
 		</tr>
 		<tr>
 			<th>SQL Server</th>
 			<td>NTEXT</td>
 			<td class="orange"></td>
 			<td>Converted to LONGVARCHAR, will be deprecated in future versions of SQLServer.</td>
 		</tr>
 		<tr>
 			<th>SQL Server</th>
 			<td>NCHAR</td>
 			<td class="green"></td>
 			<td>Converted to CHAR</td>
 		</tr>
 		<tr>
 		 	<th>SQL Server</th>
 			<td>NVARCHAR</td>
 			<td class="green"></td>
 			<td>Converted to VARCHAR</td>
 		</tr>
 		<tr>
 		 	<th>SQL Server</th>
 			<td>XML</td>
 			<td class="green"></td>
 			<td>Converted to VARCHAR(32672)</td>
 		</tr> 
 		<tr>
 		 	<th>SQL Server</th>
 			<td>TIMESTAMP/ROWVERSION</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to BINARY</td>
 		</tr>
 		<tr>
 		 	<th>SQL Server</th>
 			<td>UDT</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to VARBINARY</td>
 		</tr> 	
 		<tr>
 		 	<th>SQL Server</th>
 			<td>MONEY</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to 8 bytes DECIMAL</td>
 		</tr> 	
 		<tr>
 		 	<th>SQL Server</th>
 			<td>SMALLMONEY</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to 4 bytes DECIMAL</td>
 		</tr> 
 		<tr>
 		 	<th>SQL Server</th>
 			<td>HIERARCHYID</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to VARCHAR</td>
 		</tr> 
 		<tr>
 		 	<th>SQL Server</th>
 			<td>UNIQUEIDENTIFIER</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to VARCHAR</td>
 		</tr> 
 		<tr>
 		 	<th>SQL Server</th>
 			<td>GEOGRAPHY</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to VARCHAR</td>
 		</tr> 
 		<tr>
 		 	<th>SQL Server</th>
 			<td>GEOMETRY</td>
 			<td class="green"></td>
 			<td>SQLServer JDBC Driver converts it to VARCHAR</td>
 		</tr> 
 		<tr>
 		 	<th>SQL Server</th>
 			<td>SQL_VARIANT</td>
 			<td class="red"></td>
 			<td>SQLServer JDBC Driver error:<br> com.microsoft.sqlserver.jdbc.SQLServerException: The "variant" data type is not supported.</td>
 		</tr>  		
 		<tr>
 			<th>SQL Server</th>
 			<td>CURSOR</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr>
 			<th>SQL Server</th>
 			<td>UNSIGNED</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>	
 		<tr class="odd">
 			<td colspan=4></td>
 		</tr>
 		<tr>
 			<th>MySQL</th>
 			<td>UNSIGNED</td>
 			<td class="red"></td>
 			<td>Not supported</td>
 		</tr>
 		<tr class="odd">
 			<td colspan=4></td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>CURSOR</td>
 			<td class="red"></td>
 			<td>Not Supported</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>NCHAR</td>
 			<td class="green"></td>
 			<td>Converted to CHAR</td>
 		</tr>
<!-- Does not exist? (unable to create a table having an NVARCHAR type in Oracle - only NVARCHAR2 is recognised)
 		<tr>
 			<th>Oracle</th>
 			<td>NVARCHAR</td>
 			<td class="green"></td>
 			<td>Converted to VARCHAR</td>
 		</tr>
-->
 		<tr>
 			<th>Oracle</th>
 			<td>NCLOB</td>
 			<td class="green"></td>
 			<td>Converted to CLOB</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>NVARCHAR2</td>
 			<td class="green"></td>
 			<td>Converted to VARCHAR</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>TIMESTAMP WITH LOCAL TIME ZONE</td>
 			<td class="green"></td>
 			<td>Converted to TIMESTAMP</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>TIMESTAMP WITH TIME ZONE</td>
 			<td class="green"></td>
 			<td>Converted to TIMESTAMP - Extracted using: "&ltCOL&gt AT LOCAL"</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>INTERVAL YEAR TO MONTH</td>
 			<td class="green"></td>
 			<td>Converted to INTEGER, holding the equivalent number of months</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>INTERVAL DAY TO SECOND</td>
 			<td class="green"></td>
 			<td>Converted to DOUBLE, holding the equivalent number of seconds</td>
 		</tr>
		<tr>
 			<th>Oracle</th>
 			<td>ROWID</td>
 			<td class="green"></td>
 			<td>Converted to VARCHAR(4000)</td>
 		</tr>
 		<tr>
 			<th>Oracle</th>
 			<td>UROWID</td>
 			<td class="green"></td>
 			<td>Converted to VARCHAR(4000)</td>
 		</tr>
 	</tbody>
 </table>
<p/>

<li>Data Types information was gathered using the following RDBMS providers' resources:
	<ul>
		<li><a href="http://db.apache.org/derby/docs/10.8/ref/crefsqlj31068.html">Apache Derby 10.8 Data Types</a></li>
		<li><a href="http://publib.boulder.ibm.com/infocenter/db2luw/v10r5/index.jsp?topic=%2Fcom.ibm.db2.luw.sql.ref.doc%2Fdoc%2Fr0008483.html&resultof=%22data%22%20%22types%22%20%22type%22%20">IBM DB2 10.5 Data Types</a></li>
		<li><a href="http://msdn.microsoft.com/en-us/library/ms378715(v=sql.105).aspx">Microsoft SQL Server 2008 Data Types</a></li>
		<li><a href="http://dev.mysql.com/doc/refman/5.6/en/data-type-overview.html">MySQL 5.6 Data Types</a></li>
		<li><a href="http://docs.oracle.com/cd/E11882_01/server.112/e26088/sql_elements001.htm#SQLRF0021">Oracle 11g Data Types</a></li>
	</ul>
</li>

<li>Type casting policy for comparison expressions in queries:
	<ul>
		<li>For comparison predicates between a logical table column and a contant value (e.g. "WHERE LOCATION > 'ABC'"), the types on each side of the comparison operator are expected to be
			comparable (refer to the section on "Data type assignments and comparison, sorting, and ordering" in the <a href="http://db.apache.org/derby/docs/10.8/ref">Derby Reference Manual</a>.</li>
		<li>Further to this, for each data source federated under a logical table, when the type of the logical column does not match the type of the physical data source column, GaianDB will explicitly
			CAST the physical column to the logical type to make the query work. This is true for all RDBMS providers, <b>*except MySQL*</b> (which will work without it as it has a weak column typing policy).
			This may mean in certain cases (except with MySQL) that a column index will not be used, which is a limitation at present.
			For example, a predicate such as: "WHERE MyDoubleColumnMappedToAnIntegerInDB2 > 3000.1" will cause GaianDB to CAST the DB2 column to a DOUBLE type in the query that is executed against DB2, 
			and that may mean that a predefined index on that column will not be used. The alternative would clearly be to CAST the double value 3000.1 to an INTEGER in this case. This will be addressed in future.</li>
	</ul>
</li>

</ul>

<hr><h2><a name="contents335">Supported Number of Logical Tables</a></h2>
<ul>
<li>The supported number of logical tables for a GaianDB node depends upon:
	<ul><li>the JVM memory heap size allocated to the node</li>
	<li>the size of the table definitions</li>
	<li>the number of data sources for the logical tables</li>
	<li>the number of connected nodes.</li>
	</ul></li><br/>
<li>The following table shows supported values for a Gaian Node with two connections to other nodes,
logical table definitions of up to 100 columns, and one data source defined per table.</li>
<br/>
<table class='data'>
<thead><tr><th>JVM memory heap size</th><th>Connected nodes</th><th>Supported Logical Tables<super>*</super></th></tr></thead>
<tr><td>128MB</td><td>2</td><td>400</td></tr>
<tr><td>256MB</td><td>2</td><td>1200</td></tr>
</table>
<font size=-1><super>*</super>Defined with 100 columns and one data source per table.</font>
</ul>

<hr><h2><a name="contents346">Error Messages</a></h2>

<p> Find the documentation for GaianDB's error messages in <a href="javadoc-errors/index.html">this document</a>.

<hr><h2><a name="contents359">FAQ & Troubleshooting</a></h2>
<ul>
	<li><p><b>My GaianDB node fails to start properly</b></p>
	First, verify that:
	<ul>
	  <li>the correct version of Java is installed (Java 7 or above from IBM or SUN). <b>Note</b>: the directory containing the 'java' executable from the correct install must appear in your PATH variable ahead of any other Java install directory.</li>
	  <li>no other instance of GaianDB or Derby or any other program is currently using the port needed by GaianDB (by default it would be 6414). <b>Note</b>: the default GaianDB node port can be changed to avoid conflicts. Please see <a href="#contents115">GaianDB node usage</a> for more information.</li>
	  <li>you have an IP address associated with the expected network device and that you can ping this address. On Windows, if you are on DHCP, try
		'ipconfiguration /release', then 'ipconfiguration /renew' to refresh your IP address. On Unix check your network properties and, if needed, stop and restart DHCP client.</li>
	</ul>

	<p>Also disable any other devices that may have other (potentially conflicting) associated IP addresses. If your GaianDB node still fails to start, the problem may
		be related to your network or other hardware and/or drivers.</p>
	<p>On Windows, try starting your machine in SAFE MODE to disable non-essential drivers. If GaianDB only
	works in SAFE MODE you will need to investigate by trial and error which of your hardware/drivers is causing the error.</p>
	<p>If your GaianDB node still does not work, please <a href="#contents400">Contact Us</a>.</p>
	</li>
	
	<li><p><b>A GaianDB node is not automatically connecting itself to the network / is unable to discover other nodes</b></p>
	Here are some possible reasons / steps to take:
	<ul>
		<li>The physical network does not support IP multicast (often the case with wireless), or the new GaianDB node is in a
		separate domain: You will have to fix these conditions or setup a manual connection as explained in
		<a href="#contents215">Hard-wiring connections between GaianDB nodes (incl setting up gateways)</a></li>
		<li>Your hostname does not resolve to an IP address: This tends to happen more on Unix systems, but can also happen on Windows.
		Refer to paragraph: <a href="#contents337">Supported Operating Systems</a></li>
		<li>You may have a second IP address that is interfering. When you run 'ipconfig' from a Windows command prompt, check for any unexpected
		active adapters (commonly using an ip address starting with: '169...'). This condition should be resolved by identifying the
		software which is responsible for this adapter and disabling it. As a short term fix, try running 'ipconfiguration /release',
		then 'ipconfiguration /renew' whilst the IBM Gaian Database is running, and it should automatically discover other nodes.</li>
		<li>On Unix systems, run 'ifconfig' from a command prompt, if the default network device (usually eth0) does not have an IP, try re-running your
		DHCP client application.</li>
		<li>On MAC OS X, open your Network Configuration Properties panel and verify that your default network device settings.</li>
		<li>This can also be due to firewall issues:</li>
	</ul>
	</li>
	
	<li><p><b>What firewall settings does GaianDB require?</b></p>
	<p>
	If your system uses a firewall, you may need to set up some custom rules to allow GaianDB to function
	fully and to allow discovery &amp; dynamic connections between nodes.
	</p>
	The required rules are:
	<ul>
		<li>Allow outgoing connections</li>
		<li>Open the ports for each node you run (e.g. the default port for a GaianDB node is 6414)</li>
	</ul>

	<li><p><b>GaianDB runs out of memory</b></p>
	<p>Increase the JVM memory heap size when starting up the GaianDB server in
	'launchGaianServer.bat' (Windows) or 'launchGaianServer.sh' (Unix), by modifying the memory option: &quot;-Xmx&quot;. For example, a value of &quot;-Xmx128m&quot;
	corresponds to 128MB of memory.</p></li>

	<li><p><b>My GaianDB node hangs on startup. Log file ('gaiandb.log') shows message "Could not connect to Derby Network Server on host 0.0.0.0 ..."</b></p>
	<p>Firstly, note that the host value 0.0.0.0 is a mask value which tells the derby network server to allow connections from any host. If you are getting the above error, it
	usually means your network configuration is incorrect. Ensure your hostname is configured correctly, e.g. on Unix systems, verify that /etc/hosts has a correct
	ip address mapping for it.</p>
	</li>

	<li><p><b>Unable to connect to a GaianDB node - client connections hang and connections between nodes are not stable</b></p>
	<p>
	Some old IBM Java 6 builds have a known DriverManager synchronization locking bug. Update your version of IBM java to avoid this. GaianDB
	version 1.03 also exhibits similar issues when many nodes are all started at once. This is fixed in later versions.</p>
	</li>

	<li><p><b>Data Partitioning across GaianDB Nodes</b></p>
	<p>
	When building a partitioned database across multiple Gaian Nodes, the data will usually be split between nodes
	according to a certain variable (e.g. 'by sensor name', 'by device serial number', etc.).</p>
	<p>Each Gaian Node's physical leaf node does not need to keep that constant information in every row of every column
	of its tables. Instead, for many RDBMSs (e.g. Derby, DB2), a DEFAULT column can be used.</p>
	For Derby and DB2, this is defined in the table definition (when creating a table) using the SQL syntax:
	<pre>'&lt;ColName&gt; &lt;ColType&gt;[WITH] DEFAULT &lt;DefaultValue&gt;'</pre>
	Another, more efficient way to accomplish the same result, is to define <a href="#contents92">constant columns</a> in the Gaian DB configuration file (e.g.	gaiandb_config.properties).
	</li>

	<li><p><b>What can I do to help diagnose a Distributed Query failure?</b></p>
	<p>If you are running the query from the 'queryDerby' CLP then both client and server warnings should be visible to you.
	Otherwise, to see server warnings, run the stored procedure: <pre>call listwarnings()</pre>
	If these do not help solve the problem try switching logging on to level 'MORE' (try not to use ALL). 
	Use the API to do this: <pre>call setloglevel('MORE')</pre> and have a look at file 'gaiandb.log'.</p>
	</li>

	<li><p><b>A Logical Table Definition update is not dynamically applied when re-running a previously executed query</b></p>
	<p>This can happen because SQL queries are cached by Derby. Therefore, new queries against the modified logical table should
	be slightly different (e.g. have an extra space in them) to force Derby to reload the definition of the logical table.
	This issue should not occur if you are using the GaianDB managed views for the logical tables.</p>
	</li>

	<li><p><b>SQL queries including sets of '=' predicates which are all OR'ed together take longer than expected to execute</b></p>
	<p>This is a Derby issue. Sets of '=' predicates (on any types, incl INT or VARCHAR) which are all OR'ed together are not passed
	down by Derby to GaianDB. 
	<br/>To solve this, a range predicate must be added so that the other predicates will be pushed down. E.g. for positive
	int a: '<code>where a=1 or a=2</code>' doesn't get passed down, but this equivalent would: '<code>where a=1 or a=2 or a<-1</code>'.
	</p>
	</li>

	<li><p><b>SQL queries including an 'in ( list )' predicate take longer to execute than expected</b></p>
	<p>Similar to the above, this is another known Derby limitation. Derby does not push down any predicates to federated data sources
	if they contain an 'in ( list )' fragment.</p>
	</li>

	<li><p><b>How do I federate my own Derby database if it is not running the same version of Derby as GaianDB?</b></p>
	You can't reference 2 derbyclient.jar files on the classpath of 'launchGaianServer.bat' or 'launchGaianServer.sh' and so you need to use the same Derby version for
	running GaianDB as for connecting to your existing database. 
	<br/>GaianDB should work fine with versions of Derby beyond 10.5, so you just need to replace
	the 3 Derby jars (derby.jar, derbyclient.jar, derbynet.jar) in the GaianDB install with the ones from your separate Derby install (this must be done on a
	fresh install of GaianDB, i.e. where there is no 'gaiandb' database folder). 
	<br/>There is also a way to upgrade the version of a database that is less than 10.5. To do this, first make a backup copy of your back-level Derby database in case the upgrade doesn't work, then connect to it with the 10.5 client driver and use the option 'upgrade=true' in the connection URL.<br/>
	</li>
</ul>
<br/>

<hr><h2><a name="contents121">Features</a></h2>
<UL>
	<li>Small footprint (&lt; 4MB) and therefore easily deployable: just ship a zip-executable file (including a local configuration file)
	that will unzip	and start the server. Nothing else to do to start the federation!</li>
	<LI>Federated access to JDBC RDBMS and CSV Flat files.</LI>
	<li>Access Omnifind text indexes (of either 'Yahoo' or 'Enterprise' editions).</li>
	<li>Over 30 stored procedure management API calls to effectively manage the configuration of Logical Tables, their data sources and other
	system features and properties. These make it possible to have a global view of the system with its 'listxxx' commands and to use its
	'setxxx' commands to easily apply (and validate) configuration updates against any accessible GaianDB node on the network.</li>
	<LI>Resources pooling and multithreading support: multiple federated tables in same logical table definition are queried concurrently.</li>
	<LI>Message Broker client listener to decompose and store messages and the topics they were published under.</li>
	<LI>Command line interface: Pre-defined batch file 'queryDerby.bat' is a Command Line Processor for GaianDB. 'testDerby.bat'
	has a pre-canned query for verifying that the install completed successfully.</li>
	<LI>Different Logging levels: NONE, LESS,MORE, ALL</li>
	<LI>In-Memory Data Sources and Indexing: Files and RDBMS tables can be loaded into memory and indexed to improve query performance.</li>
	<LI>Performance metrics (query time, number of rows retrieved...)</li>
	<LI>Special provenance columns: GAIAN_NODE, GAIAN_LEAF (queryable using option: 'with_provenance')</li>
	<LI>Constant column definitions for context annotations and query routing.</li>
	<li>Scale-free network topology (Few to Many &amp; Many to Few) to be leveraged in query propagation</li>
	<li>Possibility to specify maximum depth of queries,  e.g. to obtain a quick view of data at 3 levels deep when it is
	not necessary to query all nodes in the federation.</li>
	<li>Breadth-first query propagation to all GaianDB nodes in the network: Loop detection/handling in query propagation,
	minimising network load and avoiding duplicates.</li>
	<LI>Error tolerance and Partial Results: GaianDB manages its connections such that data is always retrieved from active
	connected GaianDB nodes and their federated data sources. When unreachable GaianDB nodes or data sources become active again,
	they are automatically accessible again by the network</LI>
	<LI>Configuration  Registry (local or distributed) has a simplified properties file
	node definitions.</LI>
	<LI>Fully Dynamic reload/refresh of configuration: All updates (e.g. new logical table definitions, data sources, etc) are loaded and applied
	without having to restart the GaianDB server.</LI>
	<LI>Explain queries: Gives a description of a query path through the network of databases and a count of rows that would be returned by each node.</LI>
	<li>Basic security: User authentication and low-level automatic encryption of passwords in the configuration file.</li>
	<li>GaianDB node connection maintenance: When a GaianDB node discovers and connects to a new node, it maintains JDBC connections
	in both directions (between itself and the new node) by issuing periodic maintenance function calls to the new node.</li>
	<li>Detection and cancellation of hanging queries (not mistaken for long-running queries)</li>
	<li>Performance Improvements: Client and Server side SQL Prepared Statement caching; Buffered and batched multi-threaded record fetching</li>
	<li>Automated dynamic management of SQL VIEWS for logical tables and their derivative definitions containing provenance columns or explain columns</li>
	<li>A Policy plugin interface to manipulate the incoming SQL queries or filter returned records</li>
	<li>Flexible GaianDB node discovery using configuration variable 'DISCOVERY_IP' to specify a broadcast mask or multicast group address</li>
	<li>Ability to federate Excel spreadsheets</li>
	
	<li>Dashboard with tabs for: connection establishment, topology view, metrics monitoring and query processing</li>	
	<li>Fine grained discovery options (discovery via gateways and cluster membership control)</li>
	<li>Access control to allow/disallow SQL API configuration and propagated writes</li>
	<li>Connectivity resilience to network variability in terms of latency and bandwidth</li>
	<li>Sepcialised data source options for flexible column mappings (mapping by position and quotable columns)</li>
	<li>Ability to propagate 'pass-through' CRUD operations (create/insert/update/delete/call) in GaianQuery sub-queries</li>
	<li>Specialised API procedures & functions, e.g. listnodes, addgateway</li>
	<li>Specialised configuration capability to limit the number of inbound connection threads</li>
	<li>System management of log files such that their disk space usage is limited</li>
	<li>Capability to specify a node name when starting GaianDB</li>
	<li>Specialised column mappings and physical table expression flexibility - can now hold composite SQL expressions</li>
</UL>

<hr><h2><a name="contents400">Authors/Contacts</a></h2>
David Vyvyan (Development and Authoring): Senior Software Engineer, IBM Hursley Labs, UK:
<a href="mailto:drvyvyan@uk.ibm.com">drvyvyan@uk.ibm.com</a><br>
Patrick Dantressangle (Consultancy): Senior Technical Staff Member, Information Management Architect, IBM Hursley Labs, UK:
<a href="mailto:dantress@uk.ibm.com">dantress@uk.ibm.com</a><br>
Graham Bent (Consultancy): Senior Technical Staff Member,  IBM Hursley Labs, UK:
<a href="mailto:GrahamBent@uk.ibm.com">GrahamBent@uk.ibm.com</a><br>

<br/>

</BODY>
</html>
