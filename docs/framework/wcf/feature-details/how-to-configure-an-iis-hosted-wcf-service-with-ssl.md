---
title: "HOW TO：以 SSL 設定 IIS 裝載的 WCF 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：以 SSL 設定 IIS 裝載的 WCF 服務
本主題說明如何設定 IIS 裝載的 WCF 服務以使用 HTTP 傳輸安全性。  HTTP 傳輸安全性必須使用 SSL 憑證才能註冊到 IIS。  如果您沒有 SSL 憑證，則可以使用 IIS 來產生測試憑證。  接下來，您必須將 SSL 繫結加入至網站，並設定網站的驗證屬性。  最後，您需要將 WCF 服務設定為使用 HTTPS。  
  
### 建立自我簽署憑證  
  
1.  開啟網際網路資訊服務管理員 \(inetmgr.exe\)，並在左側樹狀檢視中選取您的電腦名稱。  在螢幕右側選取 \[伺服器憑證\]  
  
     ![IIS Manager 首頁畫面](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg\_INetMgrHome")  
  
2.  在 \[伺服器憑證\] 視窗中，按一下 \[**建立自我簽署憑證**\]連結。  
  
     ![使用 IIS 建立自我簽署憑證](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg\_CreateSelfSignedCert")  
  
3.  輸入自我簽署憑證的易記名稱，然後按一下 \[**確定**\]。  
  
     ![建立自我簽署憑證對話方塊](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg\_MyCert")  
  
     新建立的自我簽署憑證詳細資料會顯示在 \[**伺服器憑證**\] 視窗。  
  
     ![伺服器憑證視窗](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg\_ServerCertificateWindow")  
  
     產生的憑證會安裝在 \[受信任的根憑證授權單位\] 存放區中。  
  
### 加入 SSL 繫結  
  
1.  仍舊在網際網路資訊服務管理員中，依序展開螢幕左側樹狀檢視中的 \[**網站**\] 和 \[**預設的網站**\] 資料夾。  
  
2.  按一下 \[**繫結**\]。連結視窗右上方部分中的 \[**動作**\] 區段。  
  
     ![加入 SSL 繫結](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg\_AddSSLBinding")  
  
3.  在 \[網站繫結\] 視窗中按一下 \[**新增**\] 按鈕。  
  
     ![站台繫結對話方塊](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg\_SiteBindingsDialog")  
  
4.  在 \[**新增網站繫結**\] 對話方塊中，選取 https 的類型和您剛建立的自我簽署憑證的易記名稱。  
  
     ![站台繫結範例](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg\_MyCertBinding")  
  
### 設定 SSL 的虛擬目錄  
  
1.  仍舊在網際網路資訊服務管理員中，選取包含您的 WCF 安全服務的虛擬目錄。  
  
2.  在視窗的中間窗格中，選取 IIS 區段中的 \[**SSL 設定**\]。  
  
     ![虛擬目錄的 SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg\_SSLSettingsForVDir")  
  
3.  在 \[SSL 設定\] 窗格中選取 \[**需要 SSL**\] 核取方塊，並在螢幕右側的 \[**動作**\] 區段中按一下 \[**套用**\] 連結。  
  
     ![虛擬目錄 SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg\_VDirSSLSettings")  
  
### 設定 HTTP 傳輸安全性的 WCF 服務  
  
1.  在 WCF 服務的 web.config 中，將 HTTP 繫結設定為使用傳輸安全性，如下列 XML 所示。  
  
    ```  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
        </bindings>  
  
    ```  
  
2.  指定您的服務和服務端點，如下列 XML 所示。  
  
    ```  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
  
    ```  
  
## 範例  
 下列是使用 HTTP 傳輸安全性之 WCF 服務的 web.config 檔的完整範例  
  
```  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
 <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
  
```  
  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## 請參閱  
 [在網際網路資訊服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)   
 [Internet Information Service 裝載指示](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)   
 [網際網路資訊服務裝載最佳做法](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)   
 [使用內嵌程式碼的 IIS 裝載](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)