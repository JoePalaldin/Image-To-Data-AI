# Image-To-Data-AI
Open source Java API to process dynamic image sources, extract data, and stream data.

The focus of this project is to automatically monitor and consume data from dynamically updated image sources which cannot be easily consumed using other tools like Chrome Driver for example.  Image to Data AI is an open source Apached licensed frame work.

The project is built using Java 1.6 and Netbeans 6.9. The project leverages Java FX which includes certain lower level paintComponent() methods which improve the performance of the tool.  Some of these components have been removed from more recent versions of the JDK, or if they do exist in more recent versions, some things have been changed that impact performance.  The only draw back with Java 1.6 is that more recent SSL certificates used by some web sites do not exist in the Java 6.45 JDK.  The work around is use Bouncy Castle and add the latest security files to your JRE install.  

The example project includes a Netbeans project with an example implementation that extracts Forex volume data from a Trading View web page which includes a dynamically updated web control.  The application supports multiple monitors and allows the user to select the display monitor that is being monitored using an update timer.  The application will monitor whatever exists on the target display.  After each timer update a screen shot is taken for the selected monitor and placed in a work area scroll view.  A processing box can be sketched to define a specific area of the image that will be sent to an image processing method which will perform the data extraction at each timer interval. The data objects collected should implement java.io.Serializable.  The example looks for the volume bars at the bottom of the control and extracts a series of relative volume values ranging from zero to volume max, with volume max being equal to the pixel height of the volume indicator which is recognized during the image analysis.

A simple TCP class is provided to connect clients and stream data objects after they are created.
