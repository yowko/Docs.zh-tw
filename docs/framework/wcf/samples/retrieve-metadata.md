---
title: 擷取中繼資料
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: a7a30fee36b14d0414f2f5bed513c21a694f3484
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255399"
---
# <a name="retrieve-metadata"></a>擷取中繼資料

這個範例會示範如何實作會動態擷取服務的中繼資料，以選擇要進行通訊之端點的用戶端。 這個範例是以 [消費者入門](getting-started-sample.md)為基礎。 服務已修改成公開兩個端點：使用系結之基底位址上的端點 `basicHttpBinding` ，以及在 {*baseaddress*}/secure 使用系結的安全端點 `wsHttpBinding` 。 此時用戶端並不是以端點位址與繫結設定，而是使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 類別動態擷取服務的中繼資料，然後使用 <xref:System.ServiceModel.Description.ServiceEndpointCollection> 類別將中繼資料當做 <xref:System.ServiceModel.Description.WsdlImporter> 匯入。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 用戶端應用程式會使用匯入的 <xref:System.ServiceModel.Description.ServiceEndpointCollection> 以建立與服務通訊的用戶端。 用戶端應用程式會逐一查看每個擷取的端點，並與每個會實作 `ICalculator` 合約的端點進行通訊。 適當的位址與繫結會隨同所擷取的端點提供，以便讓該用戶端設定成與每個端點通訊，如下列範例程式碼所示。  
  
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
  
 用戶端主控台視窗會顯示傳送至每個端點的作業，並顯示位址路徑與繫結程序名稱。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建立解決方案的 c #、c + + 或 Visual Basic .NET 版本，請遵循 [建立 Windows Communication Foundation 範例](building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
