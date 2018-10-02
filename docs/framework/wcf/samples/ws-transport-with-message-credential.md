---
title: 使用訊息認證的 WS 傳輸
ms.date: 03/30/2017
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
ms.openlocfilehash: 44f37e3576b508e679d45a3cbafacfb5a68a7838
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030177"
---
# <a name="ws-transport-with-message-credential"></a><span data-ttu-id="932f0-102">使用訊息認證的 WS 傳輸</span><span class="sxs-lookup"><span data-stu-id="932f0-102">WS Transport With Message Credential</span></span>
<span data-ttu-id="932f0-103">這個範例會示範結合訊息中傳遞的用戶端認證來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="932f0-103">This sample demonstrates the use of SSL transport security in combination with client credential being carried in the message.</span></span> <span data-ttu-id="932f0-104">這個範例會使用 `wsHttpBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="932f0-104">This sample uses the `wsHttpBinding` binding.</span></span>  
  
 <span data-ttu-id="932f0-105">根據預設，`wsHttpBinding` 繫結會提供 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="932f0-105">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="932f0-106">當針對傳輸安全性設定時，此繫結會支援 HTTPS 通訊。</span><span class="sxs-lookup"><span data-stu-id="932f0-106">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="932f0-107">HTTPS 會保護在網路上傳輸之訊息的機密性與完整性。</span><span class="sxs-lookup"><span data-stu-id="932f0-107">HTTPS provides confidentiality and integrity protection for the messages that are transmitted over the wire.</span></span> <span data-ttu-id="932f0-108">但是，可以用來驗證服務之用戶端的驗證機制集合會受限於 HTTPS 傳輸所支援的機制。</span><span class="sxs-lookup"><span data-stu-id="932f0-108">However the set of authentication mechanisms that can be used to authenticate the client to the service is limited to what the HTTPS transport supports.</span></span> <span data-ttu-id="932f0-109">Windows Communication Foundation (WCF) 提供`TransportWithMessageCredential`設計來克服這項限制的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="932f0-109">Windows Communication Foundation (WCF) offers a `TransportWithMessageCredential` security mode that is designed to overcome this limitation.</span></span> <span data-ttu-id="932f0-110">如果是設定這種安全性模式，傳輸安全性就會用來提供所傳輸訊息的機密性與完整性，以及用來執行服務驗證。</span><span class="sxs-lookup"><span data-stu-id="932f0-110">When this security mode is configured, the transport security is used to provide confidentiality and integrity for the transmitted messages and to perform the service authentication.</span></span> <span data-ttu-id="932f0-111">不過，用戶端驗證是由用戶端認證直接置於訊息的方式執行。</span><span class="sxs-lookup"><span data-stu-id="932f0-111">However, the client authentication is performed by putting the client credential directly in the message.</span></span> <span data-ttu-id="932f0-112">這可讓您使用任何認證類型來支援訊息安全性模式，用戶端驗證，同時保有傳輸安全性模式的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="932f0-112">This allows you to use any credential type that is supported by the message security mode for the client authentication while keeping the performance benefit of transport security mode.</span></span>  
  
 <span data-ttu-id="932f0-113">在這個範例中，`UserName` 認證類型會用來驗證服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="932f0-113">In this sample, a `UserName` credential type is used to authenticate the client to the service.</span></span>  
  
 <span data-ttu-id="932f0-114">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務。</span><span class="sxs-lookup"><span data-stu-id="932f0-114">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="932f0-115">`wsHttpBinding` 繫結會指定並設定在用戶端和服務的應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="932f0-115">The `wsHttpBinding` binding is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="932f0-116">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="932f0-116">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="932f0-117">在此範例中的程式碼是幾乎完全相同的[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)服務。</span><span class="sxs-lookup"><span data-stu-id="932f0-117">The program code in the sample is almost identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="932f0-118">服務合約則另外提供一項作業 - `GetCallerIdentity`。</span><span class="sxs-lookup"><span data-stu-id="932f0-118">There is one additional operation provided by the service contract - `GetCallerIdentity`.</span></span> <span data-ttu-id="932f0-119">這個作業會將呼叫者身分識別名稱傳回呼叫者。</span><span class="sxs-lookup"><span data-stu-id="932f0-119">This operation returns the name of the caller's identity to the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="932f0-120">您必須建立一個憑證並使用 [Web 伺服器憑證精靈] 指派憑證，再建置及執行範例。</span><span class="sxs-lookup"><span data-stu-id="932f0-120">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="932f0-121">組態檔設定中的端點定義與繫結定義會啟用 `TransportWithMessageCredential` 安全性模式，如同下列用戶端的範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="932f0-121">The endpoint definition and binding definition in the configuration file settings enable `TransportWithMessageCredential` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="932f0-122">指定的位址會使用 https:// 配置。</span><span class="sxs-lookup"><span data-stu-id="932f0-122">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="932f0-123">繫結組態會將安全性模式設定為 `TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="932f0-123">The binding configuration sets the security mode to `TransportWithMessageCredential`.</span></span> <span data-ttu-id="932f0-124">相同的安全性模式必須指定在服務的 Web.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="932f0-124">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="932f0-125">當您嘗試存取 https 時，因為此範例中使用的憑證是使用 Makecert.exe 所建立的測試憑證，會顯示安全性警示： 位址，例如`https://localhost/servicemodelsamples/service.svc `，從您的瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="932f0-125">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as  `https://localhost/servicemodelsamples/service.svc `, from your browser.</span></span> <span data-ttu-id="932f0-126">若要允許 WCF 用戶端，才能使用測試憑證中的位置，已新增一些額外的程式碼用戶端以隱藏安全性警示。</span><span class="sxs-lookup"><span data-stu-id="932f0-126">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="932f0-127">使用實際執行憑證時，不需要這個程式碼及伴隨的類別。</span><span class="sxs-lookup"><span data-stu-id="932f0-127">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```
  
 <span data-ttu-id="932f0-128">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="932f0-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="932f0-129">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="932f0-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="932f0-130">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="932f0-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="932f0-131">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="932f0-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="932f0-132">請確定您已執行[Internet Information Services (IIS) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="932f0-132">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
3.  <span data-ttu-id="932f0-133">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="932f0-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="932f0-134">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="932f0-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="932f0-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="932f0-135">See Also</span></span>
