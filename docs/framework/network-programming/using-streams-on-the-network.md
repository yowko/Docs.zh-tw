---
title: 在網路上使用資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: a593ea324d39d8161ad87c4df6d6010970f3e1c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109053"
---
# <a name="using-streams-on-the-network"></a>在網路上使用資料流
網路資源在 .NET Framework 中是以資料流的形式呈現。 因為對資料流沒有任何特殊待遇，.NET Framework 提供下列功能：  
  
-   以一般方式傳送和接收 Web 資料。 不論實際的檔案內容為何 (HTML、XML 或其他格式)，應用程式都會使用 <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> 來傳送和接收資料。  
  
-   與整個 .NET Framework 資料流的相容性。 .NET Framework 中無處不使用資料流，其處理資料流的基礎結構健全。 例如，您可將讀取 <xref:System.IO.FileStream> 中 XML 資料的應用程式，修改為讀取 <xref:System.Net.Sockets.NetworkStream> 中的資料，而非僅變更將資料流初始化的幾行程式碼。 **NetworkStream** 類別與其他資料流最大的不同處，在於 **NetworkStream** 是不可搜尋的，<xref:System.Net.Sockets.NetworkStream.CanSeek%2A> 屬性一律傳回 **false**而 <xref:System.Net.Sockets.NetworkStream.Seek%2A> 和 <xref:System.Net.Sockets.NetworkStream.Position%2A> 方法則擲回 <xref:System.NotSupportedException>。  
  
-   資料送達時的處理。 來自網路的資料以資料流方式到達時，應用程式可立即存取該資料，而不必等到整個資料集下載完成後才存取。  
  
 <xref:System.Net.Sockets> 命名空間包含 **NetworkStream** 類別，其可特別實作用於網路資源的 <xref:System.IO.Stream> 類別。 <xref:System.Net.Sockets> 命名空間中的類別會使用 **NetworkStream** 類別來代表資料流。  
  
 若要使用傳回的資料流將資料傳送到網路上，請在 <xref:System.Net.WebRequest> 上呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A>。 **WebRequest** 會將要求標題傳送至伺服器；然後您即可在傳回的資料流上呼叫 <xref:System.IO.Stream.BeginWrite%2A>、<xref:System.IO.Stream.EndWrite%2A> 或 <xref:System.IO.Stream.Write%2A> 方法，將資料傳送到網路資源。 有些通訊協定 (例如 HTTP) 可能會要求您先設定特定通訊協定屬性，再傳送資料。 下列程式碼範例示範如何設定用於傳送資料的特定 HTTP 屬性。 它假設變數 `sendData` 包含要傳送的資料，而變數 `sendLength` 則是要傳送資料的位元組數。  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 若要從網路接收資料，請在 <xref:System.Net.WebResponse> 上呼叫 <xref:System.Net.WebResponse.GetResponseStream%2A>。 然後，您即可在傳回的資料流上呼叫 <xref:System.IO.Stream.BeginRead%2A>、<xref:System.IO.Stream.EndRead%2A> 或 <xref:System.IO.Stream.Read%2A> 方法，以讀取網路資源的資料。  
  
 使用網路資源的資料流時，請牢記下列要點：  
  
-   因為 **NetworkStream** 類別無法在資料流中變更位置，所以 **CanSeek** 屬性一律傳回 **false**。 **Seek** 和 **Position** 方法會擲回 **NotSupportedException**。  
  
-   使用 **WebRequest** 和 **WebResponse** 時，呼叫 **GetResponseStream** 所建立的資料流執行個體為唯讀，而呼叫 **GetRequestStream** 所建立的資料流執行個體則為唯寫。  
  
-   使用 <xref:System.IO.StreamReader> 類別可讓編碼工作變得更輕鬆。 下列程式碼範例會使用 **StreamReader** 從 **WebResponse** 讀取以 ASCII 編碼的資料流 (範例中未示範如何建立要求)。  
  
-   如果沒有可用的網路資源，即可能會封鎖對 **GetResponse** 的呼叫。 您應考慮透過 <xref:System.Net.WebRequest.BeginGetResponse%2A> 和 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法使用非同步要求。  
  
-   完成建立伺服器連線時，可能會封鎖對 **GetRequestStream** 的呼叫。 您應考慮透過 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 和 <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法，對資料流使用非同步要求。  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a>另請參閱

- [作法：使用 WebRequest 類別要求資料](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [要求資料](../../../docs/framework/network-programming/requesting-data.md)
