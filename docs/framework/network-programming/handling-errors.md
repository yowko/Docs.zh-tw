---
title: "處理錯誤 | Microsoft Docs"
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
  - "網際網路、WebRequest 和 WebResponse 類別例外狀況"
  - "Status 屬性"
  - "WebExceptions 類別，關於 WebExceptions 類別"
  - "Timeout 列舉成員"
  - "ConnectFailure 列舉成員"
  - "TrustFailure 列舉成員"
  - "WebRequest 類別，例外狀況"
  - "從網際網路要求資料，錯誤處理"
  - "Success 列舉成員"
  - "接收資料，錯誤"
  - "ProtocolError 列舉成員"
  - "下載網際網路資源，錯誤處理"
  - "WebResponse 類別、例外狀況"
  - "SendFailure 列舉成員"
  - "錯誤 [.NET Framework]、WebRequest 和 WebResponse 類別例外狀況"
  - "傳送資料，錯誤"
  - "網際網路要求回應，錯誤處理"
  - "NameResolutionFailure 列舉成員"
  - "KeepAliveFailure 列舉成員"
  - "網路資源，WebRequest 和 WebResponse 類別例外狀況"
  - "RequestCanceled 列舉成員"
  - "ReceiveFailure 列舉成員"
  - "ServerProtocolViolation 列舉成員"
  - "ConnectionClosed 列舉成員"
  - "SecureChannelFailure 列舉成員"
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 處理錯誤
<xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別擲回來 <xref:System.Net.WebRequest.GetResponse%2A> 方法擲回的 [WebExceptions](frlrfsystemnetwebexceptionclasstopic) \) 的系統例外狀況 \(例如 <xref:System.ArgumentException>\) 和 Web 特定例外狀況。  
  
 每個 **WebException** 包含從 <xref:System.Net.WebExceptionStatus> 列舉型別的值。 <xref:System.Net.WebException.Status%2A> 屬性。  您可以檢查 **狀態** 屬性來判斷產生的錯誤並執行適當的步驟來解決錯誤。  
  
 下表說明 **狀態** 屬性的可能值。  
  
|狀態|描述|  
|--------|--------|  
|ConnectFailure|遠端服務無法聯繫在傳輸層級。|  
|ConnectionClosed|連接過早關閉。|  
|KeepAliveFailure|伺服器關閉正在建立連接 Keep\-Alive 標頭集合。|  
|NameResolutionFailure|命名服務無法解析主機名稱。|  
|ProtocolError|從伺服器收到的回應是完整的，但會指示錯誤在通訊協定層。|  
|ReceiveFailure|未從遠端伺服器接收到完整回應。|  
|RequestCanceled|要求取消。|  
|SecureChannelFailure|錯誤在安全通道連結時發生。|  
|SendFailure|完整要求無法送出至遠端伺服器。|  
|ServerProtocolViolation|伺服器回應不是有效 HTTP 回應。|  
|成功|沒有遇到錯誤。|  
|Timeout|無回應在為要求設定的逾時時間內接收。|  
|TrustFailure|伺服器憑證無法驗證。|  
|MessageLengthLimitExceeded|已在傳送要求或從伺服器接收回應時收到超過指定限制的訊息。|  
|暫止|暫止內部非同步要求。|  
|PipelineFailure|這個值會支援 .NET Framework 基礎結構並不適合直接用於您的程式碼。|  
|ProxyNameResolutionFailure|名稱解析程式服務無法解析 Proxy 主機名稱。|  
|UnknownError|未知類型的例外狀況 \(Exception\) 已經發生。|  
  
 當包含來自伺服器的回應的 **狀態** 屬性是 **WebExceptionStatus.ProtocolError**時， **WebResponse** 可用。  您可以檢查回應判斷通訊協定錯誤的實際來源。  
  
 下列範例會示範如何攔截 **WebException**。  
  
```csharp  
try   
{  
    // Create a request instance.  
    WebRequest myRequest =   
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.   
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )   
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)   
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,   
    //   there has been a protocol error and a WebResponse   
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)   
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.   
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer      
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,   
    '   there has been a protocol error and a WebResponse   
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
 使用 <xref:System.Net.Sockets.Socket> 類別會擲回 [SocketExceptions](frlrfsystemnetsocketssocketexceptionclasstopic) 的應用程式，如果錯誤發生在 Windows Sockets 發生。  [TCPClient](frlrfsystemnetsocketstcpclientclasstopic)、 [TCPListener](frlrfsystemnetsocketstcplistenerclasstopic)和 [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) 類別所建立。 **Socket** 類別最上方並擲回 **SocketExceptions** 。  
  
 當 **SocketException** 擲回時， **SocketException** 類別設定 <xref:System.Net.Sockets.SocketException.ErrorCode%2A> 屬性至最後發生的作業系統通訊端錯誤。  如需通訊端錯誤碼的詳細資訊，請參閱 MSDN 上的 Winsock 2.0 API 錯誤碼文件。  
  
## 請參閱  
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)