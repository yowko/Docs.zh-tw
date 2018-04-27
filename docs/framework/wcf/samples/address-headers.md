---
title: 位址標頭
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1392e06b0148ee24c9591839b58baf45da5109d4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="address-headers"></a>位址標頭
位址標頭範例會示範用戶端如何將參考參數傳遞至使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 WS-Addressing 規格會將端點參考的概念定義成針對特定 Web 服務端點的定址方式。 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，端點參考會使用 `EndpointAddress` 類別模型化，而 `EndpointAddress` 是 `ServiceEndpoint` 類別之 [位址] 欄位的類型。  
  
 端點參考模型的一部分，是每個參考可以包含一些會新增額外識別資訊的參考參數。 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，這些參考參數會模型化為 `AddressHeader` 類別的執行個體。  
  
 在這個範例中，用戶端會新增用戶端端點之 `EndpointAddress` 的參考參數。 服務會尋找這個參考參數，然後在其 "Hello" 服務作業的邏輯中使用這個參數的值。  
  
## <a name="client"></a>用戶端  
 對於要傳送參考參數的用戶端，它必須將 `AddressHeader` 新增至 `EndpointAddress` 的 `ServiceEndpoint`。 因為 `EndpointAddress` 類別是不變的，所以必須使用 `EndpointAddressBuilder` 類別才能修改端點位址。 下列程式碼會初始化用戶端，以便將參考參數當做其訊息部分來傳送。  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 這段程式碼會建立以原始 `EndpointAddressBuilder` 做為初始值的 `EndpointAddress`。 接下來，它會加入新建的位址標頭，呼叫具有特定名稱、命名空間與值的 `CreateAddressHeadercreates` 標頭。 此時的值為 "John"。 一旦標頭新增至產生器後，`ToEndpointAddress()` 方法便會將產生器 (可變的) 轉換回端點位址 (不變的)，此位址已指派回該用戶端端點的 [位址] 欄位。  
  
 現在，當用戶端呼叫 `Console.WriteLine(client.Hello());` 時，服務就能夠取得這個位址參數的值，即顯示於用戶端結果輸出中的值。  
  
 `Hello, John`  
  
## <a name="server"></a>伺服器  
 服務作業 `Hello()` 的實作會使用目前 `OperationContext`，檢查傳入訊息上的標頭值。  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 這段程式碼會逐一查看傳入訊息上的所有標頭，以便尋找屬於含有特定名稱之參考參數的標頭。 如果有找到該參數，它會讀取參數的值，然後將該值儲存在 "id" 變數中。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>另請參閱
