---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: 89c0fc9cabc544a6a71333b7c6c78e2657cc6610
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965571"
---
# <a name="operationcontextscope"></a>OperationContextScope
OperationCoNtextScope 範例會示範如何使用標頭, 在 Windows Communication Foundation (WCF) 呼叫上傳送額外的資訊。 在此範例中，伺服器與用戶端都是主控台應用程式。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例會示範用戶端如何使用 <xref:System.ServiceModel.Channels.MessageHeader> 將額外的資訊當做 <xref:System.ServiceModel.OperationContextScope> 傳送。 將物件範圍設定至通道以建立 <xref:System.ServiceModel.OperationContextScope> 物件。 必須轉譯至遠端服務的標頭可以新增至 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> 集合。 藉由存取 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>，可以在服務上擷取新增至此集合的標頭。 它會對多個通道進行呼叫，接著，新增至用戶端的標頭只會套用到建立 <xref:System.ServiceModel.OperationContextScope> 時所使用的通道。  
  
## <a name="messageheaderreader"></a>MessageHeaderReader  
 這個範例服務會接收來自用戶端的訊息，並嘗試查閱 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> 集合中的標頭。 用戶端會傳遞標頭中所傳送的 GUID，而服務會擷取自訂標頭，並在有出現自訂標頭時，比較此標頭和用戶端當做引數傳遞的 GUID。  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =   
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,   
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+   
         "Does it match with GUID sent as parameter: {1}",   
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a>MessageHeaderClient  
 這是使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)所產生之 proxy 來與遠端服務通訊的用戶端執行。 它會先建立兩個 `MessageHeaderReaderClient` 的 Proxy 物件。  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 然後，用戶端會建立 OperationContextScope，並將其範圍設定為 `client1`。 它會將 <xref:System.ServiceModel.Channels.MessageHeader> 新增至 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A>，然後在這兩個用戶端上叫用一次呼叫。 它會藉由檢查`client1` `RetrieveHeader`呼叫的傳回值, 確保只`client2`會在上傳送標頭, 而不是在其上。  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to   
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 這個範例會自我裝載。 執行此範例時的範例輸出提供如下：  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
