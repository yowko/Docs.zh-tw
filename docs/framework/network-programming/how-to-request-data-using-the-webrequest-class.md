---
title: "如何：使用 WebRequest 類別要求資料"
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
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 463a59444d3f93e5560e149033fd845ac8cbe62d
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>如何：使用 WebRequest 類別要求資料
下列程序描述用來向伺服器要求資源的步驟 ，例如網頁或檔案。 資源必須是以 URI 識別。  
  
### <a name="to-request-data-from-a-host-server"></a>向主機伺服器要求資料  
  
1.  藉由使用資源的 URI 來呼叫 <xref:System.Net.WebRequest.Create%2A>，以建立 <xref:System.Net.WebRequest> 執行個體。  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  .NET Framework 針對以 "http:"、"https:''、"ftp:" 和 "file:" 開頭的 URI，提供了衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。 若要使用其他通訊協定存取資源，您必須實作衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。 如需詳細資訊，請參閱[可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)。  
  
2.  在 **WebRequest** 中設定任何需要的屬性值。 例如，若要啟用驗證，請將 **Credentials** 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體。  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     在大部分情況下，**WebRequest** 類別即足以接收資料。 不過，如果您需要設定通訊協定特定屬性，就必須將 **WebRequest** 轉換為通訊協定特定類型。 例如，若要存取 <xref:System.Net.HttpWebRequest> 的 HTTP 特定屬性，請將 **WebRequest** 轉換為 **HttpWebRequest** 參考。 下列程式碼範例示範如何設定 HTTP 特定的 <xref:System.Net.HttpWebRequest.UserAgent%2A> 屬性。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  若要將要求傳送到伺服器，請呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A>。 **WebResponse** 物件傳回的實際類型取決於所要求 URI 的配置。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  完成使用 <xref:System.Net.WebResponse> 物件之後，您必須呼叫 <xref:System.Net.WebResponse.Close%2A> 方法來關閉它。 或者，如果您已自回應物件取得回應資料流，則可呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法來關閉該資料流。 如果不關閉回應或資料流，應用程式就會耗盡所有與該伺服器的連線，而無法處理其他要求。  
  
4.  您可以存取 **WebResponse** 的屬性或將 **WebResponse** 轉換為通訊協定特定執行個體，以讀取通訊協定特定屬性。 例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 特定屬性，請將 **WebResponse** 轉換為 **HttpWebResponse** 參考。 下列程式碼範例示範如何顯示與回應一起傳送的狀態資訊。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  若要取得含有伺服器所傳送之回應資料的資料流，請使用 **WebResponse** 的 <xref:System.Net.HttpWebResponse.GetResponseStream%2A> 方法。  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  讀取回應中的資料之後，您必須使用 **Stream.Close** 方法關閉回應資料流，或使用 **WebResponse.Close** 方法關閉回應。 您不需要同時針對回應資料流和 **WebResponse** 呼叫 **Close** 方法；不過，這麼做亦無害。 **WebResponse.Close** 在關閉回應時會呼叫 **Stream.Close**。  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>範例  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立網際網路要求](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [在網路上使用資料流](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)  
 [如何：使用 WebRequest 類別傳送資料](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
