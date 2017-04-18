---
title: "如何：使用 WebRequest 類別傳送資料 | Microsoft Docs"
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
  - "WebRequest 類別，將資料傳送至主機"
  - "將資料傳送至主機，使用 WebRequest 類別"
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 如何：使用 WebRequest 類別傳送資料
下列程序所說明的步驟將資料傳送至伺服器。  這個程序通常用來傳送資料至 Web 網頁。  
  
### 將資料傳送至裝載伺服器  
  
1.  可藉由呼叫接受資料，例如，指令碼或 ASP.NET 網頁資源的 URI。 <xref:System.Net.WebRequest.Create%2A><xref:System.Net.WebRequest> 建立執行個體。  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
  
    ```  
  
    > [!NOTE]
    >  .NET Framework 提供 URI 從「http 開始從 **WebRequest** 和 **WebResponse** 衍生通訊協定特定類別: 」， 「https:'' 「， ftp: 」和「檔案: 」。  使用其他通訊協定，才能存取資源，您必須從實作 **WebRequest** 和 **WebResponse**衍生的通訊協定的特定類別。  如需詳細資訊，請參閱[可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)。  
  
2.  設定您在 **WebRequest**需要的任何屬性值。  例如，啟用驗證，請將屬性設定為 **Credentials**<xref:System.Net.NetworkCredential> 類別的執行個體。  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
  
    ```  
  
     在許多情況下，執行個體 **WebRequest** 足以傳送資料。  不過，在中，如果您需要設定通訊協定的特定屬性，您必須將項目轉換 **WebRequest** 至通訊協定的特定型別。  例如，存取 <xref:System.Net.HttpWebRequest>HTTP 特定屬性，請先將轉型為 **WebRequest** **HttpWebRequest** 參考。  下列程式碼範例會示範如何設定 HTTP 特定 <xref:System.Net.HttpWebRequest.UserAgent%2A> 屬性。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  指定允許要求所傳送之資料的通訊協定方法，例如 HTTP **POST** 方法。  
  
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
  
5.  設定 **ContentType** 屬性設為適當的值。  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  藉由呼叫所取得 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法保留要求資料的資料流。  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  將這個方法傳回的物件 <xref:System.IO.Stream> 寫入資料。  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  藉由呼叫方法 **Stream.Close** 關閉要求資料流。  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. 將要求傳送至伺服器藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A>。  這個方法會傳回包含伺服器之回應的物件。  傳回的 <xref:System.Net.WebResponse> 目標型別視所要求 URI 的配置。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
  
    ```  
  
    > [!NOTE]
    >  在您完成 <xref:System.Net.WebResponse> 物件之後，您必須呼叫方法 <xref:System.Net.WebResponse.Close%2A> 關閉它。  或者，在 中，如果您從回應物件取得回應資料流，您可以藉由呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=fullName> 方法關閉資料流。  如果您不要關閉回應資料流，您的應用程式可能會用盡與伺服器的連接變得無法處理其他要求。  
  
10. 您可以存取 **WebResponse** 的屬性或轉型 **WebResponse** 至通訊協定的特定執行個體讀取通訊協定的特定屬性。  例如，存取 <xref:System.Net.HttpWebResponse>HTTP 特定屬性，請先將轉型為 **WebResponse** **HttpWebResponse** 參考。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. 若要取得包含回應資料的資料流由伺服器傳送， **WebResponse**<xref:System.Net.WebResponse.GetResponseStream%2A> 呼叫的方法。  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. 使用方法，在 **WebResponse.Close** 讀取回應的資料之後，您必須關閉回應資料流使用 **Stream.Close** 方法或結束回應。  在這兩種方法的 **關閉** 回應資料流和 **WebResponse**是不必要的，不過，這樣做並没有害。  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
  
    ```  
  
## 範例  
  
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
  
## 請參閱  
 [建立網際網路要求](../../../docs/framework/network-programming/creating-internet-requests.md)   
 [在網路上使用資料流](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)   
 [如何：使用 WebRequest 類別要求資料](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)