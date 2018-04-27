---
title: 擷取中繼資料
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3a85c43cf812ccb8e099149646d63cda6b80b71
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="retrieve-metadata"></a><span data-ttu-id="5a1ba-102">擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="5a1ba-102">Retrieve Metadata</span></span>
<span data-ttu-id="5a1ba-103">這個範例會示範如何實作會動態擷取服務的中繼資料，以選擇要進行通訊之端點的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="5a1ba-104">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="5a1ba-105">服務已修改成公開兩個端點，在基底位址使用端點`basicHttpBinding`繫結和安全的端點，在 {*baseaddress*} /secure 使用`wsHttpBinding`繫結。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="5a1ba-106">此時用戶端並不是以端點位址與繫結設定，而是使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 類別動態擷取服務的中繼資料，然後使用 <xref:System.ServiceModel.Description.ServiceEndpointCollection> 類別將中繼資料當做 <xref:System.ServiceModel.Description.WsdlImporter> 匯入。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a1ba-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5a1ba-108">用戶端應用程式會使用匯入的 <xref:System.ServiceModel.Description.ServiceEndpointCollection> 以建立與服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="5a1ba-109">用戶端應用程式會逐一查看每個擷取的端點，並與每個會實作 `ICalculator` 合約的端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="5a1ba-110">適當的位址與繫結會隨同所擷取的端點提供，以便讓該用戶端設定成與每個端點通訊，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
```csharp   
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 <span data-ttu-id="5a1ba-111">用戶端主控台視窗會顯示傳送至每個端點的作業，並顯示位址路徑與繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a1ba-112">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5a1ba-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5a1ba-113">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5a1ba-114">若要建置方案的 C#、 c + + 或 Visual BASIC.NET 版本，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5a1ba-115">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a1ba-116">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a1ba-117">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5a1ba-118">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a1ba-119">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5a1ba-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="5a1ba-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a1ba-120">See Also</span></span>
