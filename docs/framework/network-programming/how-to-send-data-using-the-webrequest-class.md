---
title: 如何：使用 WebRequest 類別傳送資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f62775a41f70e4dd96c749acd99bf8b850d96407
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47193027"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>如何：使用 WebRequest 類別傳送資料
下列程序描述用來將資料傳送到伺服器的步驟。 本程序通常用於在網頁上張貼資料。  
  
### <a name="to-send-data-to-a-host-server"></a>將資料傳送到主機伺服器  
  
1.  使用接受資料之資源 (例如，指令碼或 ASP.NET 網頁) 的 URI 呼叫 <xref:System.Net.WebRequest.Create%2A>，以建立 <xref:System.Net.WebRequest> 執行個體。  
  
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
  
     在大部分情況下，**WebRequest** 執行個體本身即足以傳送資料。 不過，如果您需要設定通訊協定特定屬性，就必須將 **WebRequest** 轉換為通訊協定特定類型。 例如，若要存取 <xref:System.Net.HttpWebRequest> 的 HTTP 特定屬性，請將 **WebRequest** 轉換為 **HttpWebRequest** 參考。 下列程式碼範例示範如何設定 HTTP 特定的 <xref:System.Net.HttpWebRequest.UserAgent%2A> 屬性。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  指定允許資料與要求一起傳送的通訊協定方法，例如 HTTP **POST** 方法。  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  設定 **ContentLength** 屬性。  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  將 **ContentType** 屬性設定為適當值。  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  藉由呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法，取得保留要求資料的資料流。  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  將資料寫入這個方法所傳回的 <xref:System.IO.Stream> 物件。  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  藉由呼叫 **Stream.Close** 方法來關閉要求資料流。  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. 藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A>，將要求傳送到伺服器。 這個方法會傳回包含伺服器回應的物件。 傳回的 <xref:System.Net.WebResponse> 物件類型取決於要求 URI 的配置。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  完成使用 <xref:System.Net.WebResponse> 物件之後，您必須呼叫 <xref:System.Net.WebResponse.Close%2A> 方法來關閉它。 或者，如果您已自回應物件取得回應資料流，則可呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法來關閉該資料流。 如果不關閉回應或資料流，應用程式就會耗盡所有與該伺服器的連線，而無法處理其他要求。  
  
10. 您可以存取 **WebResponse** 的屬性或將 **WebResponse** 轉換為通訊協定特定執行個體，以讀取通訊協定特定屬性。 例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 特定屬性，請將 **WebResponse** 轉換為 **HttpWebResponse** 參考。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. 若要取得含有伺服器所傳送之回應資料的資料流，請呼叫 **WebResponse** 的 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法。  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. 讀取回應中的資料之後，您必須使用 **Stream.Close** 方法關閉回應資料流，或使用 **WebResponse.Close** 方法關閉回應。 您不需要同時針對回應資料流和 **WebResponse** 呼叫 **Close** 方法；不過，這麼做亦無害。  
  
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
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
            response.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>請參閱  
 [建立網際網路要求](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [在網路上使用資料流](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)  
 [如何：使用 WebRequest 類別要求資料](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
