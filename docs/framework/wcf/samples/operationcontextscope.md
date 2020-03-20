---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: ce21d9d099d893015ea828bdc3b136ab83f6d8e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183424"
---
# <a name="operationcontextscope"></a>OperationContextScope
操作上下文範圍示例演示如何使用標頭髮送 Windows 通信基礎 （WCF） 調用上的額外資訊。 在此範例中，伺服器與用戶端都是主控台應用程式。  
  
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
 這是使用[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成的代理與遠端服務通信的用戶端實現。 它會先建立兩個 `MessageHeaderReaderClient` 的 Proxy 物件。  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 然後，用戶端會建立 OperationContextScope，並將其範圍設定為 `client1`。 它會將 <xref:System.ServiceModel.Channels.MessageHeader> 新增至 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A>，然後在這兩個用戶端上叫用一次呼叫。 它通過檢查`RetrieveHeader`調用的傳回值確保僅打開`client1`而不是打開`client2`標頭。  
  
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
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 要在單機或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
