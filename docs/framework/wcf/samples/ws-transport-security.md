---
title: "WS 傳輸安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3435eab63cf745607b6ecf61b12123966f80442b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transport-security"></a><span data-ttu-id="31af2-102">WS 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="31af2-102">WS Transport Security</span></span>
<span data-ttu-id="31af2-103">這個範例會示範搭配 <xref:System.ServiceModel.WSHttpBinding> 繫結來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="31af2-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="31af2-104">根據預設，`wsHttpBinding` 繫結會提供 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="31af2-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="31af2-105">當針對傳輸安全性設定時，此繫結會支援 HTTPS 通訊。</span><span class="sxs-lookup"><span data-stu-id="31af2-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="31af2-106">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="31af2-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="31af2-107">`wsHttpBinding` 會指定並設定在用戶端和服務的應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="31af2-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31af2-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="31af2-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31af2-109">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="31af2-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31af2-110">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="31af2-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="31af2-111">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="31af2-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31af2-112">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="31af2-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="31af2-113">此範例中的程式碼為相同的[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)服務。</span><span class="sxs-lookup"><span data-stu-id="31af2-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="31af2-114">您必須建立一個憑證並使用 [Web 伺服器憑證精靈] 指派憑證，再建置及執行範例。</span><span class="sxs-lookup"><span data-stu-id="31af2-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="31af2-115">組態檔設定中的端點定義與繫結定義會啟用 `Transport` 安全性模式，如同下列用戶端的範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="31af2-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="31af2-116">指定的位址會使用 https:// 配置。</span><span class="sxs-lookup"><span data-stu-id="31af2-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="31af2-117">繫結組態會將安全性模式設定為 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="31af2-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="31af2-118">相同的安全性模式必須指定在服務的 Web.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="31af2-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="31af2-119">因為本範例中所使用的憑證是使用 Makecert.exe 所建立的測試憑證，所以當您嘗試從瀏覽器存取 https: 位址時 (例如 https://localhost/servicemodelsamples/service.svc)，會顯示安全性警示。</span><span class="sxs-lookup"><span data-stu-id="31af2-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="31af2-120">若要允許 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端適當地使用測試憑證，就必須在用戶端新增某些其他程式碼以便隱藏安全性警示。</span><span class="sxs-lookup"><span data-stu-id="31af2-120">To allow the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="31af2-121">使用實際執行憑證時，不需要這個程式碼及伴隨的類別。</span><span class="sxs-lookup"><span data-stu-id="31af2-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  
  
```  
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 <span data-ttu-id="31af2-122">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="31af2-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="31af2-123">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="31af2-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="31af2-124">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="31af2-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="31af2-125">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="31af2-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="31af2-126">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="31af2-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="31af2-127">請確定您已執行[網際網路資訊服務 (IIS) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="31af2-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="31af2-128">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="31af2-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="31af2-129">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="31af2-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31af2-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="31af2-130">See Also</span></span>
