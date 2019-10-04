---
title: WS 2007 聯合 HTTP 繫結
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: ad56665b5b6648fb93a9f31f18167a964b4cba92
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834661"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="0b0ac-102">WS 2007 聯合 HTTP 繫結</span><span class="sxs-lookup"><span data-stu-id="0b0ac-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="0b0ac-103">這個範例會示範使用 <xref:System.ServiceModel.WS2007FederationHttpBinding>，這是能夠用來建置支援 WS-Trust 規格 1.3 版之聯合案例的標準繫結。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="0b0ac-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0b0ac-105">此範例包含以主控台為基礎的用戶端程式（*setup.exe*）、以主控台為基礎的 Security Token Service 程式（使用 *.exe*），以及以主控台為基礎的服務程式（*setup.exe*）。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="0b0ac-106">服務會實作定義要求/回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="0b0ac-107">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算作業 (`Add`、`Subtract`、`Multiply` 和 `Divide`)。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="0b0ac-108">用戶端自安全性權杖服務 (STS) 取得安全性權杆，並對指定的數學運算提出同步要求。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="0b0ac-109">服務則以結果回覆。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-109">The service then replies with the result.</span></span> <span data-ttu-id="0b0ac-110">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="0b0ac-111">這個範例會使用 `ICalculator` 項目，讓 `ws2007FederationHttpBinding` 合約可供使用。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="0b0ac-112">此系結在用戶端上的設定會顯示在下列程式碼中：</span><span class="sxs-lookup"><span data-stu-id="0b0ac-112">The configuration of this binding on the client is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="0b0ac-113">在[\<security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)上，`security` 值會指定應該使用的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="0b0ac-114">在此範例中，會使用 `message` 安全性，這也是為什麼在[@no__t 4security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)內指定[@no__t 2message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)的原因。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="0b0ac-115">[@No__t 3message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)內的[@no__t 1issuer >](../../configure-apps/file-schema/wcf/issuer.md)元素，會指定發行安全性權杖給用戶端的 STS 位址和系結，讓用戶端可以向 `ICalculator` 服務驗證。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="0b0ac-116">在服務上設定此系結的方式如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0b0ac-116">The configuration of this binding on the service is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="0b0ac-117">在[\<security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)上，`security` 值會指定應該使用的安全性模式。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="0b0ac-118">在此範例中，會使用 `message` 安全性，這也是為什麼在[@no__t 4security >](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)內指定[@no__t 2message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)的原因。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="0b0ac-119">[@No__t 4message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)內 `ws2007FederationHttpBinding` 的[@no__t 1issuerMetadata >](../../configure-apps/file-schema/wcf/issuermetadata.md)元素，會指定可用來抓取 STS 中繼資料的端點位址和識別。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="0b0ac-120">服務的行為如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0b0ac-120">The behavior for the service is shown in the following code:</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
<span data-ttu-id="0b0ac-121">[@No__t 1issuedTokenAuthentication >](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> 可讓服務在驗證期間允許用戶端轉譯的權杖上指定條件約束。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="0b0ac-122">這個組態會指定服務接受主體名稱為 CN=STS 之憑證所簽署的權杖。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="0b0ac-123">STS 會使用標準 <xref:System.ServiceModel.WS2007HttpBinding>，讓單一端點可供使用。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="0b0ac-124">服務會回應用戶端對權杖的要求。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="0b0ac-125">如果用戶端是以 Windows 帳戶進行驗證，服務就會發出包含用戶端之使用者名稱做為宣告的權杖。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="0b0ac-126">在建立權杖期間，STS 會使用與 CN=STS 憑證關聯的私密金鑰來簽署該權杖。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="0b0ac-127">此外，它還會建立對稱金鑰，並使用與 CN=localhost 憑證關聯的公開金鑰進行加密。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="0b0ac-128">在將權杖傳回至用戶端時，STS 也會傳回對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="0b0ac-129">用戶端向 `ICalculator` 服務出示發行的權杖，然後使用對稱金鑰簽署訊息來證明它知道這把金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="0b0ac-130">當您執行範例時，安全性權杖的要求會顯示在 STS 主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="0b0ac-131">作業的要求和回應會顯示在用戶端和服務主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="0b0ac-132">在任何主控台視窗中按下 ENTER 鍵，即可關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="0b0ac-133">此範例中包含的*安裝程式 .bat*檔案可讓您使用相關的憑證來設定伺服器和 STS，以執行自我裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="0b0ac-134">此批次檔會在 LocalMachine/TrustedPeople 憑證存放區中建立兩份憑證。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="0b0ac-135">第一份憑證的主體名稱為 CN=STS，而且會由 STS 用來簽署發給用戶端的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="0b0ac-136">第二份憑證的主體名稱為 CN=localhost，而且會由 STS 用於以服務可解密的方式來加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b0ac-137">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0b0ac-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="0b0ac-138">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0b0ac-139">以系統管理員許可權開啟 Visual Studio 的開發人員命令提示字元，並執行安裝程式 .bat 檔案，以建立所需的憑證。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="0b0ac-140">此批次檔會使用*certmgr.msc*與 Windows SDK 散發的 Makecert。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="0b0ac-141">不過，您必須從 Visual Studio 命令提示字元內執行*安裝程式 .bat* ，讓腳本能夠找到這些工具。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="0b0ac-142">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="0b0ac-143">若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="0b0ac-144">如果您使用 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]，則必須以較高的許可權（以滑鼠右鍵按一下*檔案，然後*按一下 [以**系統管理員身分執行**]）來執行*setup.exe*、setup.exe 和 mstest.exe *。*</span><span class="sxs-lookup"><span data-stu-id="0b0ac-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b0ac-145">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0b0ac-146">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="0b0ac-146">Check for the following (default) directory before continuing:</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> <span data-ttu-id="0b0ac-147">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="0b0ac-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b0ac-148">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="0b0ac-148">This sample is located in the following directory:</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
