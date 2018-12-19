<h1> Exporting ZEPL notebooks </h1>
Once you've worked on your notebook in ZEPL, you can also export it outside of our service for usage either on your Apache Zeppelin or Jupyter services.

<br/>
## Export into Apache Zeppelin notebook format

You can export your notebook into Apache Zeppelin file from ZEPL notebook page by using `Export to Zeppelin` menu as shown below:

<br/>

<img src="../../img/export_notebook/01_zepl_export_menu.png" class="image-box big-img" />

<br/>

We support export to all Apache Zeppelin versions starting from v. 0.7.0. Please select from dropdown menu the version of Apache Zeppelin that you're using and click on it. Then you will have your notebook file (.json or .zpln) downloaded. Once downloaded you can import your notebook file into Apache Zeppelin instance from it’s `Import note` menu on home page as shown below:

<br/>

<img src="../../img/export_notebook/02_zeppelin_import_menu.png" class="image-box big-img" />

<br/>
<br/>
Note that in case you have problem to import notebook into Apache Zeppelin because of file size limitation (by default Zeppelin is configured to limit 1MB on import) you can change `zeppelin.websocket.max.text.message.size` property under `ZEPPELIN_HOME/conf/zeppelin-site.xml` as shown below:

```xml
<property>
  <name>zeppelin.websocket.max.text.message.size</name>
  <value>52428800</value>
  <description>Size in characters of the maximum text message to be received by websocket. Defaults to 1024000</description>
</property>
```
Above changes would set max notebook file limit to 50Mb. Alternatively you can set `ZEPPELIN_WEBSOCKET_MAX_TEXT_MESSAGE_SIZE` environment variable under `ZEPPELIN_HOME/conf/zeppelin-env.sh` as well. For more information on configuration please refer to official Apache Zeppelin documentation.
