---
title: "處理錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c7d9c08e38c2d82381c94e8813ef0312806bd010
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="handling-errors"></a>處理錯誤
<xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別會擲回兩個系統例外狀況 (例如 <xref:System.ArgumentException>) 和 Web 特定例外狀況 (這些是 <xref:System.Net.WebRequest.GetResponse%2A> 方法所擲回的 <xref:System.Net.WebException>)。  
  
 每個 **WebException** 包含一個 <xref:System.Net.WebException.Status%2A> 屬性，其中包含來自 <xref:System.Net.WebExceptionStatus> 列舉的值。 您可以檢查 **Status** 屬性來判斷發生的錯誤，並採取適當的步驟來解決這個錯誤。  
  
 下表描述 **Status** 屬性的可能值。  
  
|狀態|描述|  
|------------|-----------------|  
|ConnectFailure|無法在傳輸層級連絡遠端服務。|  
|ConnectionClosed|連線過早關閉。|  
|KeepAliveFailure|伺服器已關閉使用保持連線標頭集合建立的連線。|  
|NameResolutionFailure|名稱服務無法解析主機名稱。|  
|ProtocolError|從伺服器收到的回應已完成，但是指出通訊協定層級發生錯誤。|  
|ReceiveFailure|未從遠端伺服器收到完整的回應。|  
|RequestCanceled|已取消要求。|  
|SecureChannelFailure|安全通道連結發生錯誤。|  
|SendFailure|無法將完整的要求傳送到遠端伺服器。|  
|ServerProtocolViolation|伺服器回應不是有效的 HTTP 回應。|  
|成功|沒有遇到任何錯誤。|  
|等候逾時|在針對要求所設定的逾時內未收到任何回應。|  
|TrustFailure|無法驗證伺服器憑證。|  
|MessageLengthLimitExceeded|從伺服器傳送要求或接收回應時，收到超過指定限制的訊息。|  
|暫止|內部非同步要求正在擱置中。|  
|PipelineFailure|此值支援 .NET Framework 基礎結構，但不能直接用於您的程式碼中。|  
|ProxyNameResolutionFailure|名稱解析服務無法解析 Proxy 主機名稱。|  
|UnknownError|發生未知類型的例外狀況。|  
  
 當 **Status** 屬性是 **WebExceptionStatus.ProtocolError** 時，即可使用包含伺服器回應的 **WebResponse**。 您可以檢查這個回應，以判斷實際的通訊協定錯誤來源。  
  
 下列範例示範如何快取 **WebException**。  
  
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
  
 當 Windows 通訊端發生錯誤時，使用 <xref:System.Net.Sockets.Socket> 類別的應用程式會擲回 <xref:System.Net.Sockets.SocketException>。 <xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener> 和 <xref:System.Net.Sockets.UdpClient> 類別都建置在 **Socket** 類別之上，因此也會擲回 **SocketExceptions**。  
  
 擲回 **SocketException** 時，**SocketException** 類別會將 <xref:System.Net.Sockets.SocketException.ErrorCode%2A> 屬性設定為最後發生的作業系統通訊端錯誤。 如需通訊端錯誤碼的詳細資訊，請參閱 MSDN 中的 Winsock 2.0 API 錯誤碼文件。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理基本概念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)
