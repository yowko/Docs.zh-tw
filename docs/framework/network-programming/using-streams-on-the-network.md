---
title: "在網路上使用資料流 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "從網際網路要求資料，資料流"
  - "網路"
  - "回應網際網路要求，資料流"
  - "網路資源，資料流功能"
  - "接收資料，資料流功能"
  - "網路資源"
  - "傳送資料，資料流功能"
  - "下載網際網路資源，資料流"
  - "資料流，功能"
  - "網際網路，資料流"
  - "資料流"
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 在網路上使用資料流
網路資源在 .NET Framework 中表示為資料流。  藉由將資料流泛型， .NET Framework 提供下列功能:  
  
-   一種常見方式傳送和接收網路資料。  哪些檔案 \(HTML， XML 或其他的實際內容—應用程式將使用 <xref:System.IO.Stream.Write%2A?displayProperty=fullName> 和 <xref:System.IO.Stream.Read%2A?displayProperty=fullName> 傳送和接收資料。  
  
-   使用資料流的相容性跨 .NET Framework。  資料流使用在 .NET Framework 中，會處理它們的豐富的基礎結構。  例如，您可以修改 <xref:System.IO.FileStream> 讀取的 XML 資料是以變更只有少數程式碼讀取 <xref:System.Net.Sockets.NetworkStream> 的資料初始化資料流的應用程式。  **NetworkStream** 類別和其他資料流之間的主要差異在於 **NetworkStream** 不可搜尋， <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> 屬性永遠會傳回， **false**，並 <xref:System.Net.Sockets.NetworkStream.Seek%2A> 和 <xref:System.Net.Sockets.NetworkStream.Position%2A> 方法擲回 <xref:System.NotSupportedException>。  
  
-   處理資料，則到達。  資料流提供對資料，當從網路到達，而不是強制應用程式等候設定的整個資料下載。  
  
 <xref:System.Net.Sockets> 命名空間包含明確地實作 <xref:System.IO.Stream> 類別可以搭配網路資源使用的 **NetworkStream** 類別。  在 <xref:System.Net.Sockets> 命名空間中的類別會使用 **NetworkStream** 類別代表資料流。  
  
 使用傳回的資料流，要將資料傳送至網路，請在您的 <xref:System.Net.WebRequest>的 <xref:System.Net.WebRequest.GetRequestStream%2A> 。  **WebRequest** 會傳送要求標頭傳送至伺服器，然後您可以將資料傳送至網路資源是透過呼叫 <xref:System.IO.Stream.BeginWrite%2A>、 <xref:System.IO.Stream.EndWrite%2A>或 <xref:System.IO.Stream.Write%2A> 方法所傳回的資料流。  某些通訊協定，例如 HTTP，可能會要求您在傳送資料之前設定通訊協定的特定屬性。  下列程式碼範例會示範如何設定正在傳送之資料的 HTTP 特定屬性。  這個範例假設，變數 `sendData` 包含資料傳送，而變數 `sendLength` 是位元組數傳送的資料。  
  
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
  
 若要從網路接收的資料，請在您的 <xref:System.Net.WebResponse>的 <xref:System.Net.WebResponse.GetResponseStream%2A> 。  您可以藉由呼叫 <xref:System.IO.Stream.BeginRead%2A>、 <xref:System.IO.Stream.EndRead%2A>或 <xref:System.IO.Stream.Read%2A> 方法然後讀取網路資源的資料會儲存在傳回的資料流。  
  
 當使用從網路資源的資料流時，請注意下列幾點:  
  
-   因為 **NetworkStream** 類別無法變更資料流的位置， **CanSeek** 屬性一定會傳回 **false** 。  **Seek** 和 **位置** 方法擲回 **NotSupportedException**。  
  
-   當您使用 **WebRequest** 和 **WebResponse**時，呼叫方法所建立的資料流執行個體 **GetResponseStream** 是唯讀的，而且呼叫方法所建立的資料流執行個體 **GetRequestStream** 唯寫。  
  
-   使用 <xref:System.IO.StreamReader> 類別讓輸入更容易。  下列程式碼範例會使用 **StreamReader** 讀取 **WebResponse** 的 ASCII 編碼資料流 \(本範例未顯示建立要求\)。  
  
-   如果網路資源無法使用， **GetResponse** 對的呼叫會封鎖。  您應該考慮使用 <xref:System.Net.WebRequest.BeginGetResponse%2A> 和 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法的非同步要求。  
  
-   在與伺服器的連接時， **GetRequestStream** 對的呼叫會封鎖。  您應該考慮使用非同步要求來與 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 和 <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法的資料流。  
  
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
  
## 請參閱  
 [如何：使用 WebRequest 類別要求資料](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)   
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)