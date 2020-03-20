---
title: 擷取中繼資料
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 9b1adf4ed2a09625ca19016f531936002fff757d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183386"
---
# <a name="retrieve-metadata"></a>擷取中繼資料
這個範例會示範如何實作會動態擷取服務的中繼資料，以選擇要進行通訊之端點的用戶端。 此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 已修改服務以公開兩個終結點：使用`basicHttpBinding`綁定在基底位址的終結點，以及使用`wsHttpBinding`綁定在 [*基底位址*]/安全處的安全終結點。 此時用戶端並不是以端點位址與繫結設定，而是使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 類別動態擷取服務的中繼資料，然後使用 <xref:System.ServiceModel.Description.ServiceEndpointCollection> 類別將中繼資料當做 <xref:System.ServiceModel.Description.WsdlImporter> 匯入。  
  
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
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 要生成解決方案的 C#、C++ 或 Visual Basic .NET 版本，請按照[生成 Windows 通信基礎示例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的說明操作。  
  
3. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
