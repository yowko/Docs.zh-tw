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
ms.openlocfilehash: 1f10c5e0c6c266b7b31d658ec561bd8d6d85697b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129463"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a><span data-ttu-id="e950f-102">如何：使用 WebRequest 類別傳送資料</span><span class="sxs-lookup"><span data-stu-id="e950f-102">How to: Send Data Using the WebRequest Class</span></span>
<span data-ttu-id="e950f-103">下列程序描述用來將資料傳送到伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="e950f-103">The following procedure describes the steps used to send data to a server.</span></span> <span data-ttu-id="e950f-104">本程序通常用於在網頁上張貼資料。</span><span class="sxs-lookup"><span data-stu-id="e950f-104">This procedure is commonly used to post data to a Web page.</span></span>  
  
### <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="e950f-105">將資料傳送到主機伺服器</span><span class="sxs-lookup"><span data-stu-id="e950f-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="e950f-106">使用接受資料之資源 (例如，指令碼或 ASP.NET 網頁) 的 URI 呼叫 <xref:System.Net.WebRequest.Create%2A>，以建立 <xref:System.Net.WebRequest> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e950f-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource that accepts data, for example, a script or ASP.NET page.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e950f-107">.NET Framework 針對以 "http:"、"https:''、"ftp:" 和 "file:" 開頭的 URI，提供了衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="e950f-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="e950f-108">若要使用其他通訊協定存取資源，您必須實作衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="e950f-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="e950f-109">如需詳細資訊，請參閱[可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="e950f-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="e950f-110">在 **WebRequest** 中設定任何需要的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e950f-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="e950f-111">例如，若要啟用驗證，請將 **Credentials** 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e950f-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="e950f-112">在大部分情況下，**WebRequest** 執行個體本身即足以傳送資料。</span><span class="sxs-lookup"><span data-stu-id="e950f-112">In most cases, the **WebRequest** instance itself is sufficient to send data.</span></span> <span data-ttu-id="e950f-113">不過，如果您需要設定通訊協定特定屬性，就必須將 **WebRequest** 轉換為通訊協定特定類型。</span><span class="sxs-lookup"><span data-stu-id="e950f-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="e950f-114">例如，若要存取 <xref:System.Net.HttpWebRequest> 的 HTTP 特定屬性，請將 **WebRequest** 轉換為 **HttpWebRequest** 參考。</span><span class="sxs-lookup"><span data-stu-id="e950f-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="e950f-115">下列程式碼範例示範如何設定 HTTP 特定的 <xref:System.Net.HttpWebRequest.UserAgent%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e950f-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="e950f-116">指定允許資料與要求一起傳送的通訊協定方法，例如 HTTP **POST** 方法。</span><span class="sxs-lookup"><span data-stu-id="e950f-116">Specify a protocol method that permits data to be sent with a request, such as the HTTP **POST** method.</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="e950f-117">設定 **ContentLength** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e950f-117">Set the **ContentLength** property.</span></span>  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="e950f-118">將 **ContentType** 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="e950f-118">Set the **ContentType** property to an appropriate value.</span></span>  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="e950f-119">藉由呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法，取得保留要求資料的資料流。</span><span class="sxs-lookup"><span data-stu-id="e950f-119">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span>  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  <span data-ttu-id="e950f-120">將資料寫入這個方法所傳回的 <xref:System.IO.Stream> 物件。</span><span class="sxs-lookup"><span data-stu-id="e950f-120">Write the data to the <xref:System.IO.Stream> object returned by this method.</span></span>  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="e950f-121">藉由呼叫 **Stream.Close** 方法來關閉要求資料流。</span><span class="sxs-lookup"><span data-stu-id="e950f-121">Close the request stream by calling the **Stream.Close** method.</span></span>  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <span data-ttu-id="e950f-122">藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A>，將要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="e950f-122">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="e950f-123">這個方法會傳回包含伺服器回應的物件。</span><span class="sxs-lookup"><span data-stu-id="e950f-123">This method returns an object containing the server's response.</span></span> <span data-ttu-id="e950f-124">傳回的 <xref:System.Net.WebResponse> 物件類型取決於要求 URI 的配置。</span><span class="sxs-lookup"><span data-stu-id="e950f-124">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e950f-125">完成使用 <xref:System.Net.WebResponse> 物件之後，您必須呼叫 <xref:System.Net.WebResponse.Close%2A> 方法來關閉它。</span><span class="sxs-lookup"><span data-stu-id="e950f-125">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="e950f-126">或者，如果您已自回應物件取得回應資料流，則可呼叫 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法來關閉該資料流。</span><span class="sxs-lookup"><span data-stu-id="e950f-126">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e950f-127">如果不關閉回應或資料流，應用程式就會耗盡所有與該伺服器的連線，而無法處理其他要求。</span><span class="sxs-lookup"><span data-stu-id="e950f-127">If you do not close the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
10. <span data-ttu-id="e950f-128">您可以存取 **WebResponse** 的屬性或將 **WebResponse** 轉換為通訊協定特定執行個體，以讀取通訊協定特定屬性。</span><span class="sxs-lookup"><span data-stu-id="e950f-128">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="e950f-129">例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 特定屬性，請將 **WebResponse** 轉換為 **HttpWebResponse** 參考。</span><span class="sxs-lookup"><span data-stu-id="e950f-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to an **HttpWebResponse** reference.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="e950f-130">若要取得含有伺服器所傳送之回應資料的資料流，請呼叫 **WebResponse** 的 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e950f-130">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. <span data-ttu-id="e950f-131">讀取回應中的資料之後，您必須使用 **Stream.Close** 方法關閉回應資料流，或使用 **WebResponse.Close** 方法關閉回應。</span><span class="sxs-lookup"><span data-stu-id="e950f-131">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="e950f-132">您不需要同時針對回應資料流和 **WebResponse** 呼叫 **Close** 方法；不過，這麼做亦無害。</span><span class="sxs-lookup"><span data-stu-id="e950f-132">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="e950f-133">範例</span><span class="sxs-lookup"><span data-stu-id="e950f-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e950f-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="e950f-134">See Also</span></span>  
 [<span data-ttu-id="e950f-135">建立網際網路要求</span><span class="sxs-lookup"><span data-stu-id="e950f-135">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="e950f-136">在網路上使用資料流</span><span class="sxs-lookup"><span data-stu-id="e950f-136">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="e950f-137">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="e950f-137">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="e950f-138">要求資料</span><span class="sxs-lookup"><span data-stu-id="e950f-138">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="e950f-139">如何：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="e950f-139">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
