---
title: "用戶端驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f0be40b84b11268319daff343598aa949977c52d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="client-validation"></a><span data-ttu-id="d9b2d-102">用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="d9b2d-102">Client Validation</span></span>
<span data-ttu-id="d9b2d-103">服務經常會發行中繼資料，以便自動產生和設定用戶端 Proxy 型別。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-103">Services frequently publish metadata to enable automatic generation and configuration of client proxy types.</span></span> <span data-ttu-id="d9b2d-104">當服務不受信任時，用戶端應用程式應該根據安全性、交易和服務合約類型等條件，驗證中繼資料是否符合用戶端應用程式的原則。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-104">When the service is not trusted, client applications should validate that the metadata conforms to the client application's policy regarding security, transactions, the type of service contract and so on.</span></span> <span data-ttu-id="d9b2d-105">下列範例會示範如何撰寫用戶端端點行為，此行為會驗證服務端點以確定能夠安全地使用服務端點。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-105">The following sample demonstrates how to write a client endpoint behavior that validates the service endpoint to ensure that service endpoint is safe to use.</span></span>  
  
 <span data-ttu-id="d9b2d-106">服務會公開 (Expose) 四個服務端點。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-106">The service exposes four service endpoints.</span></span> <span data-ttu-id="d9b2d-107">第一個端點使用 WSDualHttpBinding，第二個端點會使用 NTLM 驗證，第三個端點會啟用交易流程，而第四個端點會使用憑證架構的驗證。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-107">The first endpoint uses the WSDualHttpBinding, the second endpoint uses NTLM authentication, the third endpoint enables transaction flow, and the fourth endpoint uses certificate-based authentication.</span></span>  
  
 <span data-ttu-id="d9b2d-108">用戶端會使用 <xref:System.ServiceModel.Description.MetadataResolver> 類別來擷取服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-108">The client uses the <xref:System.ServiceModel.Description.MetadataResolver> class to retrieve the metadata for the service.</span></span> <span data-ttu-id="d9b2d-109">用戶端會使用驗證行為，強制禁止雙工繫結、NTLM 驗證與交易流程的原則。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-109">The client enforces a policy of prohibiting duplex bindings, NTLM authentication, and transaction flow using a validating behavior.</span></span> <span data-ttu-id="d9b2d-110">對於從服務中繼資料匯入的每個 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體，用戶端應用程式會在嘗試使用 `InternetClientValidatorBehavior` 用戶端連接至端點之前，將 <xref:System.ServiceModel.Description.ServiceEndpoint> 端點行為的執行個體新增至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-110">For each <xref:System.ServiceModel.Description.ServiceEndpoint> instance imported from the service's metadata, the client application adds an instance of the `InternetClientValidatorBehavior` endpoint behavior to the <xref:System.ServiceModel.Description.ServiceEndpoint> before attempting to use a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to connect to the endpoint.</span></span> <span data-ttu-id="d9b2d-111">此行為的 `Validate` 方法會在呼叫服務的任何作業之前執行，並且擲回 `InvalidOperationExceptions` 以強制執行該用戶端的原則。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-111">The behavior's `Validate` method runs before any operations on the service are called and enforces the client's policy by throwing `InvalidOperationExceptions`.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="d9b2d-112">若要建置範例</span><span class="sxs-lookup"><span data-stu-id="d9b2d-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="d9b2d-113">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-113">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d9b2d-114">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="d9b2d-114">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="d9b2d-115">使用系統管理員權限來開啟 Visual Studio 命令提示字元，然後執行範例安裝資料夾中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-115">Open a Visual Studio command prompt with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d9b2d-116">這會安裝執行範例所需的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-116">This installs all the certificates required for running the sample.</span></span>  
  
2.  <span data-ttu-id="d9b2d-117">從 \service\bin\Debug 執行服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-117">Run the service application from \service\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="d9b2d-118">從 \client\bin\Debug 執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-118">Run the client application from \client\bin\Debug.</span></span> <span data-ttu-id="d9b2d-119">用戶端活動會顯示在用戶端主控台應用程式上。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-119">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="d9b2d-120">如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-120">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
5.  <span data-ttu-id="d9b2d-121">當您完成範例時，請執行 Cleanup.bat 以移除憑證。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-121">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="d9b2d-122">其他安全性範例使用相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-122">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d9b2d-123">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="d9b2d-123">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="d9b2d-124">在伺服器上，以系統管理員的權限執行 Visual Studio 命令提示字元中輸入`setup.bat service`。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-124">On the server, in a Visual Studio command prompt run with administrator privileges, type `setup.bat service`.</span></span> <span data-ttu-id="d9b2d-125">執行`setup.bat`與`service`引數具有電腦完整網域名稱建立服務憑證，並將服務憑證匯出為名為 Service.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-125">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
2.  <span data-ttu-id="d9b2d-126">在伺服器上，編輯 App.config 以反映新的憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-126">On the server, edit App.config to reflect the new certificate name.</span></span> <span data-ttu-id="d9b2d-127">亦即，變更`findValue`屬性[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)電腦的完整網域名稱的項目。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-127">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the computer.</span></span>  
  
3.  <span data-ttu-id="d9b2d-128">從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-128">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
4.  <span data-ttu-id="d9b2d-129">在用戶端，請開啟 Visual Studio 命令提示字元使用系統管理員權限和型別`setup.bat client`。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-129">On the client, open a Visual Studio command prompt with administrator privileges, and type `setup.bat client`.</span></span> <span data-ttu-id="d9b2d-130">執行`setup.bat`與`client`引數會建立名為 Client.com 的用戶端憑證，並將用戶端憑證匯出為名為 Client.cer 的檔案。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-130">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5.  <span data-ttu-id="d9b2d-131">在 client.cs 檔中變更 MEX 端點的位址值和 `findValue`，以便將預設伺服器憑證設定成符合您服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-131">In the client.cs file change the address value of the MEX endpoint and the `findValue` for setting the default server certificate to match the new address of your service.</span></span> <span data-ttu-id="d9b2d-132">您可以藉由使用伺服器的完整網域名稱取代 localhost，完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-132">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="d9b2d-133">接著重新建置。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-133">Rebuild.</span></span>  
  
6.  <span data-ttu-id="d9b2d-134">從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-134">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7.  <span data-ttu-id="d9b2d-135">在用戶端上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportServiceCert.bat。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-135">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="d9b2d-136">這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-136">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8.  <span data-ttu-id="d9b2d-137">在伺服器上，於使用系統管理員權限開啟的 Visual Studio 命令提示字元中，執行 ImportClientCert.bat。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-137">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="d9b2d-138">這樣便會從 Client.cer 檔將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-138">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="d9b2d-139">在服務電腦上，使用 Visual Studio 來建置此服務專案並執行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-139">On the service computer, build the service project in Visual Studio and run service.exe.</span></span>  
  
10. <span data-ttu-id="d9b2d-140">在用戶端電腦上執行 client.exe。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-140">On the client computer, run client.exe.</span></span>  
  
    1.  <span data-ttu-id="d9b2d-141">如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-141">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d9b2d-142">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="d9b2d-142">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="d9b2d-143">當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-143">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9b2d-144">跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-144">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="d9b2d-145">如果您已執行跨電腦使用憑證的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例，請確定清除安裝在 CurrentUser - TrustedPeople 存放區中的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-145">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d9b2d-146">若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="d9b2d-146">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b2d-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9b2d-147">See Also</span></span>  
 [<span data-ttu-id="d9b2d-148">使用中繼資料</span><span class="sxs-lookup"><span data-stu-id="d9b2d-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
