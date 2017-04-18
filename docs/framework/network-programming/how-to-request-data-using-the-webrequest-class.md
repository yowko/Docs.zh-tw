---
title: "如何：使用 WebRequest 類別要求資料 | Microsoft Docs"
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
  - "下載網際網路資源，步驟"
  - "從網際網路要求資料，步驟"
  - "WebRequest 類別，接收資料"
  - "接收資料，使用 WebRequest 類別"
  - "網際網路，要求資料"
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 如何：使用 WebRequest 類別要求資料
下列程序所說明的步驟要求資源時從伺服器，例如，網頁或檔案。  必須由 URI 識別的資源。  
  
### 要求主機伺服器上的資料  
  
1.  您可以使用資源的 URI。 <xref:System.Net.WebRequest.Create%2A><xref:System.Net.WebRequest> 建立執行個體。  
  
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
  
     在許多情況下， **WebRequest** 類別足以接收資料。  不過，在中，如果您需要設定通訊協定的特定屬性，您必須將項目轉換 **WebRequest** 至通訊協定的特定型別。  例如，存取 <xref:System.Net.HttpWebRequest>HTTP 特定屬性，請先將轉型為 **WebRequest** **HttpWebRequest** 參考。  下列程式碼範例會示範如何設定 HTTP 特定 <xref:System.Net.HttpWebRequest.UserAgent%2A> 屬性。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
  
    ```  
  
3.  若要將要求傳送至伺服器，請呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A>。  傳回的 **WebResponse** 物件的實際型別視所要求 URI 的配置。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
  
    ```  
  
    > [!NOTE]
    >  在您完成 <xref:System.Net.WebResponse> 物件之後，您必須呼叫方法 <xref:System.Net.WebResponse.Close%2A> 關閉它。  或者，在 中，如果您從回應物件取得回應資料流，您可以藉由呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=fullName> 方法關閉資料流。  如果您不要關閉回應資料流，您的應用程式可能會用盡與伺服器的連接變得無法處理其他要求。  
  
4.  您可以存取 **WebResponse** 的屬性或轉型 **WebResponse** 至通訊協定的特定執行個體讀取通訊協定的特定屬性。  例如，存取 <xref:System.Net.HttpWebResponse>HTTP 特定屬性，請先將轉型為 **WebResponse** **HttpWebResponse** 參考。  下列程式碼範例將示範如何顯示狀態資訊傳送回應。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  若要取得包含回應資料的資料流由伺服器傳送，使用 **WebResponse**的 <xref:System.Net.HttpWebResponse.GetResponseStream%2A> 方法。  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
  
    ```  
  
6.  使用方法，在 **WebResponse.Close** 讀取回應的資料之後，您必須關閉回應資料流使用 **Stream.Close** 方法或結束回應。  在這兩種方法的 **關閉** 回應資料流和 **WebResponse**是不必要的，不過，這樣做並没有害。  **WebResponse.Close** 呼叫 **Stream.Close** ，當關閉回應時。  
  
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
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create (  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close ();  
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
  
## 請參閱  
 [建立網際網路要求](../../../docs/framework/network-programming/creating-internet-requests.md)   
 [在網路上使用資料流](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [要求資料](../../../docs/framework/network-programming/requesting-data.md)   
 [如何：使用 WebRequest 類別傳送資料](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)