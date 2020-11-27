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
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="abd91-103">作法：以 SSL 設定 IIS 裝載的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="abd91-103">How to: Configure an IIS-hosted WCF service with SSL</span></span>

<span data-ttu-id="abd91-104">本主題說明如何設定 IIS 裝載的 WCF 服務以使用 HTTP 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="abd91-104">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="abd91-105">HTTP 傳輸安全性必須使用 SSL 憑證才能註冊到 IIS。</span><span class="sxs-lookup"><span data-stu-id="abd91-105">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="abd91-106">如果您沒有 SSL 憑證，則可以使用 IIS 來產生測試憑證。</span><span class="sxs-lookup"><span data-stu-id="abd91-106">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="abd91-107">接下來，您必須將 SSL 繫結加入至網站，並設定網站的驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="abd91-107">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="abd91-108">最後，您需要將 WCF 服務設定為使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="abd91-108">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="abd91-109">建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="abd91-109">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="abd91-110">開啟網際網路資訊服務管理員 (inetmgr.exe)，並在左側樹狀檢視中選取您的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="abd91-110">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="abd91-111">在螢幕右側選取 [伺服器憑證]</span><span class="sxs-lookup"><span data-stu-id="abd91-111">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="abd91-112">![IIS Manager 首頁畫面](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="abd91-112">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="abd91-113">在 [伺服器憑證] 視窗中，按一下 [**建立 Self-Signed 憑證**...]。</span><span class="sxs-lookup"><span data-stu-id="abd91-113">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="abd91-114">連結。</span><span class="sxs-lookup"><span data-stu-id="abd91-114">Link.</span></span>  
  
     <span data-ttu-id="abd91-115">![使用 IIS 建立自我&#45;簽署的憑證](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="abd91-115">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="abd91-116">輸入自我簽署憑證的易記名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="abd91-116">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="abd91-117">![建立自我&#45;的已簽署憑證對話方塊](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="abd91-117">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="abd91-118">新建立的自我簽署憑證詳細資料現在會顯示在 [ **伺服器憑證** ] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="abd91-118">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="abd91-119">![伺服器憑證視窗](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="abd91-119">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="abd91-120">產生的憑證會安裝在 [受信任的根憑證授權單位] 存放區中。</span><span class="sxs-lookup"><span data-stu-id="abd91-120">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="abd91-121">加入 SSL 繫結</span><span class="sxs-lookup"><span data-stu-id="abd91-121">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="abd91-122">在 [Internet Information Services 管理員] 中，展開 [ **網站** ] 資料夾，然後在畫面左側的樹狀檢視中，展開 [ **預設的網站** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="abd91-122">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="abd91-123">按一下 [系結 **...** ]。</span><span class="sxs-lookup"><span data-stu-id="abd91-123">Click the **Bindings….**</span></span> <span data-ttu-id="abd91-124">在視窗右上方部分的 [ **動作** ] 區段中連結。</span><span class="sxs-lookup"><span data-stu-id="abd91-124">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="abd91-125">![加入 SSL 繫結](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="abd91-125">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="abd91-126">在 [網站系結] 視窗中，按一下 [ **新增** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="abd91-126">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="abd91-127">![站台繫結對話方塊](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="abd91-127">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="abd91-128">在 [ **新增網站** 系結] 對話方塊中，為 [類型] 選取 [HTTPs]，並選取您剛才建立的自我簽署憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="abd91-128">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="abd91-129">![站台繫結範例](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="abd91-129">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="abd91-130">設定 SSL 的虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="abd91-130">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="abd91-131">仍舊在網際網路資訊服務管理員中，選取包含您的 WCF 安全服務的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="abd91-131">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="abd91-132">在視窗的中間窗格中，選取 [IIS] 區段中的 [ **SSL 設定** ]。</span><span class="sxs-lookup"><span data-stu-id="abd91-132">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="abd91-133">![虛擬目錄的 SSL 設定](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="abd91-133">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="abd91-134">在 [SSL 設定] 窗格中，選取 [**需要 SSL** ] 核取方塊，然後在畫面右側的 [**動作**] 區段中按一下 [套用 **] 連結。**</span><span class="sxs-lookup"><span data-stu-id="abd91-134">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="abd91-135">![虛擬目錄 SSL 設定](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="abd91-135">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="abd91-136">設定 HTTP 傳輸安全性的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="abd91-136">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="abd91-137">在 WCF 服務的 web.config 中，將 HTTP 繫結設定為使用傳輸安全性，如下列 XML 所示。</span><span class="sxs-lookup"><span data-stu-id="abd91-137">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2. <span data-ttu-id="abd91-138">指定您的服務和服務端點，如下列 XML 所示。</span><span class="sxs-lookup"><span data-stu-id="abd91-138">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="abd91-139">範例</span><span class="sxs-lookup"><span data-stu-id="abd91-139">Example</span></span>  

 <span data-ttu-id="abd91-140">下列是使用 HTTP 傳輸安全性之 WCF 服務的 web.config 檔的完整範例</span><span class="sxs-lookup"><span data-stu-id="abd91-140">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abd91-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abd91-141">See also</span></span>

- [<span data-ttu-id="abd91-142">在網際網路資訊服務中裝載</span><span class="sxs-lookup"><span data-stu-id="abd91-142">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="abd91-143">Internet Information Service 裝載指示</span><span class="sxs-lookup"><span data-stu-id="abd91-143">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="abd91-144">網際網路資訊服務裝載最佳做法</span><span class="sxs-lookup"><span data-stu-id="abd91-144">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="abd91-145">使用內嵌程式碼的 IIS 裝載</span><span class="sxs-lookup"><span data-stu-id="abd91-145">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
