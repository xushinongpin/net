by Tali Smith

The fastest and easiest way to install PHP on Internet Information Services \(IIS\) is by using the Microsoft® Web Platform Installer \(Web PI\). Web PI completely automates setting up IIS, FastCGI, and the latest version of PHP from the php.net Web site. With Web PI, you can navigate to the "Web Platform" tab and select "PHP" under "Framework and Runtimes" customize link. Alternately, use the instructions that follow as guidance for installing PHP with Windows® Installer or using a compressed \(Zip\) file installation.

There are two builds for each PHP version: one is thread-safe, and one is not \(referred to as the non-thread-safe \[NTS\] version\). The thread-safe version is designed for environments where the Web server core can keep the PHP engine in memory, running multiple treads of execution for different Web requests simultaneously. The architecture of IIS and the FastCGI extension provide an isolation model that keeps requests separate, removing the need for a thread-safe version. The NTS version does not have any of the code that allows PHP to manage multiple threads. As a result, there is a performance improvement on IIS when using the NTS version when compared to the tread-safe version because the NTS version avoids unnecessary thread-safety checks \(FastCGI ensures a single-threaded execution environment\).

## Install PHP {#install-php}

There are two main ways to install PHP on a Windows®-based computer: download the Windows Installer or use the Windows Zip file from the[PHP Web site](https://www.php.net/downloads.php). Either method will get PHP working, but both have some extra steps that are needed to make PHP work well.

### Windows Installer {#windows-installer}

The Windows Installer version can get a complete PHP environment up and running, but the installation of extensions can be confusing. By default, no extensions are installed, and this can adversely affect the usefulness of the PHP installation. Alternately, all of the extensions can be installed; this results in an unstable system because some of the extensions can conflict with others. It is generally easier to use the Zip file installation.

### Zip File Installation {#zip-file-installation}

To use the Zip file installation, follow the instructions in[Using FastCGI to Host PHP Applications on IIS 7.0 and Above](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-applications-on-iis/using-fastcgi-to-host-php-applications-on-iis). The Zip file installation installs many of the extensions that are available for the Windows Installer version; however, none of the extensions are enabled until their entries in the Php.ini file are set up.

1. Download the
   [latest non-thread-safe Zip file package](https://www.php.net/downloads.php)
   with binaries of PHP. Under
   **Windows Binaries**
   , click on the most current PHP non-thread-safe Zip package to download the PHP files.
2. Unpack the files to a directory of your choice \(for example,
   `C:\PHP`
   \) on your IIS server.
3. Rename the
   **Php.ini-recommended**
   to
   **php.ini**
   .
4. Open the**Php.ini**file in a text editor, then uncomment and modify settings as follows:

   * Set
     **fastcgi.impersonate = 1**
     .
 
     FastCGI under IIS supports the ability to impersonate security tokens of the calling client. This allows IIS to define the security context that the request runs under.
   * Set
     **cgi.fix\_pathinfo = 0**
 
     The
     **cgi.fix\_pathinfo**
     provides
     **PATH\_INFO/PATH\_TRANSLATED**
     support for Common Gateway Interface \(CGI\). Setting this to 1 will cause PHP CGI to fix its paths to conform to the specification.
   * Set
     **cgi.force\_redirect = 0**
     .
   * Set
     **open\_basedir**
     to point to a folder or network path where the content of the Web site\(s\) is located.
   * Set
     **extension\_dir**
     to point to a location where PHP extensions reside. For PHP 5.2.X, this is typically
     **extension\_dir = "./ext"**
     .
   * Set
     **error\_log="C:php\_errors.log"**
 
     This can help with troubleshooting.
   * Enable the required PHP extension by un-commenting corresponding lines. More information follows in the section,[Extensions](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php#Extensions_1).

     ![](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php/_static/image1.jpg)  
     _Figure 1 Windows extensions_

5. Click on
   **Start**
   ,
   **Settings**
   ,
   **Control Panel**
   , and then double-click on the
   **System**
   icon \(using the class view\).
6. Click on the
   **Advanced system settings**
   link in the left column.
7. From the
   **System Properties**
   window, click on the
   **Advanced**
   tab, and then click on the
   **Environment Variables**
   button at the bottom.
8. Select the**Path**variable from the**System Variables**section, and then click on**Edit**. Add:`c:\php`to your system path.

   ![](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php/_static/image3.jpg)  
   _Figure 2: Edit System Variable_

9. Click
   **OK**
   until you have exited the System Properties window.
10. Start IIS Manager by clicking on
    **Start**
    ,
    **Programs**
    ,
    **Administrative Tools**
    , and then
    **Internet Information Services \(IIS\) Manager**
    .
11. From the
    **IIS Manager**
    , click on the
    _hostname_
    of your server in the
    **Connections**
    panel on the left.
12. Double-click on the**Handler Mappings**icon.

    ![](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php/_static/image5.jpg)  
    _Figure 3: Internet Information Services \(IIS\) Manager_

13. From the**Handler MappingsActions**panel, click on**Add Module Mapping**.

    ![](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php/_static/image7.jpg)  
    _Figure 4: Handler Mappings_

14. Type the following information into the appropriate text boxes, and then click**OK**.

    * Request path:
      **\*.php**
    * Module
      **: FastCGImodule**
    * Executable:
      **C:\php\php-cgi.exe**
    * Name:
      **FastCGI**

    ![](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php/_static/image1.gif)  
    _Figure 5: Add Script Map_

15. Click
    **OK**
    , and then
    **c**
    lick
    **Yes.**
16. In the left panel, click on your server's
    _hostname_
    , and then double-click on the
    **Default Document**
    icon.
17. From the
    **Actions**
    panel on the right, click
    **Add**
    .
18. Enter
    **index.php**
    as the new default document name, and then click
    **OK**
    .
19. Enter
    **default.php**
    as the new default document name, and then click
    **OK**
    .
20. In the left panel, click on your server's
    _hostname_
    .
21. In the
    **Actions**
    panel on the right, click
    **Restart**
    .
22. Create a new text document, and save it as`c:\inetpub\wwwroot\phpinfo.php`with the following content:

    XML
    Copy
    ```
    <
    ?php
     phpinfo(); 
    ?
    >
    ```

23. You should now see the PHP information page at`http://localhost/phpinfo.php`.

    ![](https://docs.microsoft.com/en-us/iis/application-frameworks/install-and-configure-php-on-iis/install-and-configure-php/_static/image9.jpg)  
    _Figure 6: PHP information page_



