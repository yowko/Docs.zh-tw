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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e831f3c305716afe11df6c0b1e21db1ed5a4f01e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="6df21-102">如何：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="6df21-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="6df21-103">下列程序描述用來向伺服器要求資源的步驟 ，例如網頁或檔案。</span><span class="sxs-lookup"><span data-stu-id="6df21-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="6df21-104">資源必須是以 URI 識別。</span><span class="sxs-lookup"><span data-stu-id="6df21-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="6df21-105">向主機伺服器要求資料</span><span class="sxs-lookup"><span data-stu-id="6df21-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="6df21-106">藉由使用資源的 URI 來呼叫 <xref:System.Net.WebRequest.Create%2A>，以建立 <xref:System.Net.WebRequest> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6df21-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6df21-107">.NET Framework 針對以 "http:"、"https:''、"ftp:" 和 "file:" 開頭的 URI，提供了衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="6df21-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="6df21-108">若要使用其他通訊協定存取資源，您必須實作衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="6df21-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="6df21-109">如需詳細資訊，請參閱[可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="6df21-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="6df21-110">在 **WebRequest** 中設定任何需要的屬性值。</span><span class="sxs-lookup"><span data-stu-id="6df21-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="6df21-111">例如，若要啟用驗證，請將 **Credentials** 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6df21-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="6df21-112">在大部分情況下，**WebRequest** 類別即足以接收資料。</span><span class="sxs-lookup"><span data-stu-id="6df21-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="6df21-113">不過，如果您需要設定通訊協定特定屬性，就必須將 **WebRequest** 轉換為通訊協定特定類型。</span><span class="sxs-lookup"><span data-stu-id="6df21-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="6df21-114">例如，若要存取 <xref:System.Net.HttpWebRequest> 的 HTTP 特定屬性，請將 **WebRequest** 轉換為 **HttpWebRequest** 參考。</span><span class="sxs-lookup"><span data-stu-id="6df21-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="6df21-115">下列程式碼範例示範如何設定 HTTP 特定的 <xref:System.Net.HttpWebRequest.UserAgent%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6df21-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="6df21-116">若要將要求傳送到伺服器，請呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A>。</span><span class="sxs-lookup"><span data-stu-id="6df21-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="6df21-117">**WebResponse** 物件傳回的實際類型取決於所要求 URI 的配置。</span><span class="sxs-lookup"><span data-stu-id="6df21-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6df21-118">完成使用 <xref:System.Net.WebResponse> 物件之後，您必須呼叫 <xref:System.Net.WebResponse.Close%2A> 方法來關閉它。</span><span class="sxs-lookup"><span data-stu-id="6df21-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="6df21-119">或者，如果您已自回應物件取得回應資料流，則可呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法來關閉該資料流。</span><span class="sxs-lookup"><span data-stu-id="6df21-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6df21-120">如果不關閉回應或資料流，應用程式就會耗盡所有與該伺服器的連線，而無法處理其他要求。</span><span class="sxs-lookup"><span data-stu-id="6df21-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="6df21-121">您可以存取 **WebResponse** 的屬性或將 **WebResponse** 轉換為通訊協定特定執行個體，以讀取通訊協定特定屬性。</span><span class="sxs-lookup"><span data-stu-id="6df21-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="6df21-122">例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 特定屬性，請將 **WebResponse** 轉換為 **HttpWebResponse** 參考。</span><span class="sxs-lookup"><span data-stu-id="6df21-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="6df21-123">下列程式碼範例示範如何顯示與回應一起傳送的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="6df21-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="6df21-124">若要取得含有伺服器所傳送之回應資料的資料流，請使用 **WebResponse** 的 <xref:System.Net.HttpWebResponse.GetResponseStream%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6df21-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="6df21-125">讀取回應中的資料之後，您必須使用 **Stream.Close** 方法關閉回應資料流，或使用 **WebResponse.Close** 方法關閉回應。</span><span class="sxs-lookup"><span data-stu-id="6df21-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="6df21-126">您不需要同時針對回應資料流和 **WebResponse** 呼叫 **Close** 方法；不過，這麼做亦無害。</span><span class="sxs-lookup"><span data-stu-id="6df21-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="6df21-127">**WebResponse.Close** 在關閉回應時會呼叫 **Stream.Close**。</span><span class="sxs-lookup"><span data-stu-id="6df21-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="6df21-128">範例</span><span class="sxs-lookup"><span data-stu-id="6df21-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6df21-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6df21-129">See Also</span></span>  
 [<span data-ttu-id="6df21-130">建立網際網路要求</span><span class="sxs-lookup"><span data-stu-id="6df21-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="6df21-131">在網路上使用資料流</span><span class="sxs-lookup"><span data-stu-id="6df21-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="6df21-132">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="6df21-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="6df21-133">要求資料</span><span class="sxs-lookup"><span data-stu-id="6df21-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="6df21-134">如何：使用 WebRequest 類別傳送資料</span><span class="sxs-lookup"><span data-stu-id="6df21-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
