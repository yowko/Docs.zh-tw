---
title: 作法：以 SSL 設定 IIS 裝載的 WCF 服務
description: 瞭解如何將裝載于 IIS 的 WCF 服務設定為使用 HTTP 傳輸安全性，此安全性需要向 IIS 註冊的憑證。
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 960005761d3bed917142141976e9f9094094b34c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257648"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>作法：以 SSL 設定 IIS 裝載的 WCF 服務

本主題說明如何設定 IIS 裝載的 WCF 服務以使用 HTTP 傳輸安全性。 HTTP 傳輸安全性必須使用 SSL 憑證才能註冊到 IIS。 如果您沒有 SSL 憑證，則可以使用 IIS 來產生測試憑證。 接下來，您必須將 SSL 繫結加入至網站，並設定網站的驗證屬性。 最後，您需要將 WCF 服務設定為使用 HTTPS。  
  
### <a name="creating-a-self-signed-certificate"></a>建立自我簽署憑證  
  
1. 開啟網際網路資訊服務管理員 (inetmgr.exe)，並在左側樹狀檢視中選取您的電腦名稱。 在螢幕右側選取 [伺服器憑證]  
  
     ![IIS Manager 首頁畫面](media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. 在 [伺服器憑證] 視窗中，按一下 [**建立 Self-Signed 憑證**...]。 連結。  
  
     ![使用 IIS 建立自我&#45;簽署的憑證](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. 輸入自我簽署憑證的易記名稱，然後按一下 **[確定]**。  
  
     ![建立自我&#45;的已簽署憑證對話方塊](media/mg-mycert.jpg "mg_MyCert")  
  
     新建立的自我簽署憑證詳細資料現在會顯示在 [ **伺服器憑證** ] 視窗中。  
  
     ![伺服器憑證視窗](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     產生的憑證會安裝在 [受信任的根憑證授權單位] 存放區中。  
  
### <a name="add-ssl-binding"></a>加入 SSL 繫結  
  
1. 在 [Internet Information Services 管理員] 中，展開 [ **網站** ] 資料夾，然後在畫面左側的樹狀檢視中，展開 [ **預設的網站** ] 資料夾。  
  
2. 按一下 [系結 **...** ]。 在視窗右上方部分的 [ **動作** ] 區段中連結。  
  
     ![加入 SSL 繫結](media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. 在 [網站系結] 視窗中，按一下 [ **新增** ] 按鈕。  
  
     ![站台繫結對話方塊](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. 在 [ **新增網站** 系結] 對話方塊中，為 [類型] 選取 [HTTPs]，並選取您剛才建立的自我簽署憑證的易記名稱。  
  
     ![站台繫結範例](media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>設定 SSL 的虛擬目錄  
  
1. 仍舊在網際網路資訊服務管理員中，選取包含您的 WCF 安全服務的虛擬目錄。  
  
2. 在視窗的中間窗格中，選取 [IIS] 區段中的 [ **SSL 設定** ]。  
  
     ![虛擬目錄的 SSL 設定](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. 在 [SSL 設定] 窗格中，選取 [**需要 SSL** ] 核取方塊，然後在畫面右側的 [**動作**] 區段中按一下 [套用 **] 連結。**  
  
     ![虛擬目錄 SSL 設定](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>設定 HTTP 傳輸安全性的 WCF 服務  
  
1. 在 WCF 服務的 web.config 中，將 HTTP 繫結設定為使用傳輸安全性，如下列 XML 所示。  
  
    ```xml  
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
  
2. 指定您的服務和服務端點，如下列 XML 所示。  
  
    ```xml  
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
  
## <a name="example"></a>範例  

 下列是使用 HTTP 傳輸安全性之 WCF 服務的 web.config 檔的完整範例  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- [在網際網路資訊服務中裝載](hosting-in-internet-information-services.md)
- [Internet Information Service 裝載指示](../samples/internet-information-service-hosting-instructions.md)
- [網際網路資訊服務裝載最佳做法](internet-information-services-hosting-best-practices.md)
- [使用內嵌程式碼的 IIS 裝載](../samples/iis-hosting-using-inline-code.md)
