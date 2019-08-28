---
title: 資料流
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 3f52ba01dfd3290e4b0f728e5832a11f2f9c3eeb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045463"
---
# <a name="stream"></a>資料流
這個資料流範例將示範資料流傳輸模式通訊的使用。 服務會公開數個傳送和接收資料流的作業。 這個範例會自我裝載。 用戶端和服務都是主控台程式。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 Windows Communication Foundation (WCF) 可以用兩種傳輸模式 (已緩衝處理或串流) 進行通訊。 在預設的緩衝傳輸模式中，必須完整傳遞訊息，接收者才能讀取。 在資料流傳輸模式中，接收者不需等到訊息完全送達，就可以開始處理訊息。 當資訊的傳遞很漫長，但是可依序列處理時，使用資料流模式將十分有幫助。 當訊息太龐大而無法完整加以緩衝時，資料流模式也很有用處。  
  
## <a name="streaming-and-service-contracts"></a>資料流和服務合約  
 設計服務合約時，資料流是一項需要考慮的重點。 如果作業會接收或傳回大量的資料，您應該考慮透過資料流處理這筆資料，以避免因為要緩衝輸入或輸出訊息而佔用太多記憶體。 若要以資料流方式處理資料，存放該資料的參數必須是訊息中的唯一參數。 例如，如果輸入訊息是要處理成資料流的訊息，這項處理作業就必須剛好只有一個輸入參數。 同樣地，如果要將輸出訊息處理成資料流，這項作業也必須剛好只有一個輸出參數或傳回值。 不論是何種情況，參數或傳回值型別都必須是 `Stream`、`Message` 或 `IXmlSerializable`。 下列是這個資料流範例中使用的服務合約。  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 `GetStream` 作業會接收經過緩衝處理做為字串的一些輸入資料，然後傳回經過資料流處理的 `Stream`。 相反地，`UploadStream` 會接受 `Stream` (經過資料流處理) 並傳回 `bool` (經過緩衝處理)。 `EchoStream` 會接受並傳回 `Stream`，而這項作業也是對輸入和輸出兩種訊息都進行資料流處理的範例。 最後，`GetReversedStream` 不接受任何輸入，而只是傳回 `Stream` (經過資料流處理)。  
  
## <a name="enabling-streamed-transfers"></a>啟用資料流處理的傳輸  
 如先前所述，定義作業合約就可以在程式設計模型層級上提供資料流。 如果您在此停止作業，則傳輸仍然會緩衝整個訊息內容。 若要啟用傳輸資料流，請在傳輸的繫結項目上選取傳輸模式。 繫結項目包含可設為 `TransferMode`、`Buffered`、`Streamed` 或 `StreamedRequest` 的 `StreamedResponse` 屬性。 將傳輸模式設為 `Streamed` 可啟用雙向資料流通訊。 將傳輸模式設為 `StreamedRequest` 或 `StreamedResponse` 可以分別啟用只有要求或回應方向的資料流通訊。  
  
 `basicHttpBinding` 也會公開繫結上的 `TransferMode` 屬性，就像 `NetTcpBinding` 和 `NetNamedPipeBinding` 一樣。 如果是其他傳輸模式，您必須建立自訂繫結程序才能設定傳輸模式。  
  
 範例中的下列組態程式碼示範將 `TransferMode` 屬性設定為會在 `basicHttpBinding` 和自訂 HTTP 繫結上進行資料流處理：  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 除了將 `transferMode` 設定為 `Streamed` 之外，上述組態程式碼還會將 `maxReceivedMessageSize` 設定為 64MB。 `maxReceivedMessageSize` 會限制允許接收的最大訊息大小，以形成保護機制。 預設的 `maxReceivedMessageSize` 是 64 KB，但這對資料流案例來說，通常是過低的。  
  
## <a name="processing-data-as-it-is-streamed"></a>在資料流處理時處理資料  
 `GetStream`、`UploadStream` 和 `EchoStream` 作業都會處理直接從檔案傳送資料或直接將接收資料儲存至檔案的作業。 但是在某些情況下，還是需要傳送或接收大量的資料，並在資料送達或收到時對其資料區塊 (Chunk) 進行某種處理。 處理此類案例的其中一種方式是，撰寫自訂資料流 (衍生自 <xref:System.IO.Stream> 的類別)，以便在讀取或寫入資料時加以處理。 例如，`GetReversedStream` 作業和 `ReverseStream` 類別即是這種方式的範例。  
  
 `GetReversedStream` 會建立並傳回 `ReverseStream` 的新執行個體。 實際的處理會在系統從這個 `ReverseStream` 物件讀取時進行。 `ReverseStream.Read` 的實作會從基礎檔案讀取位元組區塊，然後將其反向，再傳回此反向的位元組。 這並不會反向整個檔案內容；一次只反向一個位元組區塊。 下列是示範如何在對資料流讀取或寫入內容時執行資料流處理的範例。  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a>執行範例  
 若要執行此範例，請先依照本文件結尾的指示建置服務與用戶端。 接下來，分別在兩個不同的主控台視窗中啟動服務和用戶端。 當用戶端啟動時，會等候您在服務就緒時按下 ENTER。 然後，用戶端先透過 HTTP 呼叫 `GetStream()`、`UploadStream()` 和 `GetReversedStream()` 方法，再透過 TCP 呼叫這些方法。 下面是服務的範例輸出，接著是用戶端的範例輸出：  
  
 服務輸出：  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 用戶端輸出：  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------   
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!NOTE]
> 如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
