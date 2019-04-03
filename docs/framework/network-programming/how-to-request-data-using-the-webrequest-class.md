---
title: 作法：使用 WebRequest 類別要求資料
ms.date: 03/21/2019
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
ms.openlocfilehash: 1b71327d007e66cc217f6d69e11122c481e5118f
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634033"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="cb253-102">作法：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="cb253-102">How to: Request data by using the WebRequest class</span></span>
<span data-ttu-id="cb253-103">下列程序描述向伺服器要求資源 (例如網頁或檔案) 的步驟。</span><span class="sxs-lookup"><span data-stu-id="cb253-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="cb253-104">資源必須是以 URI 識別。</span><span class="sxs-lookup"><span data-stu-id="cb253-104">The resource must be identified by a URI.</span></span>  
  
## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="cb253-105">向主機伺服器要求資料</span><span class="sxs-lookup"><span data-stu-id="cb253-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="cb253-106">使用資源的 URI 來呼叫 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>，以建立 <xref:System.Net.WebRequest> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb253-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="cb253-107">例如：</span><span class="sxs-lookup"><span data-stu-id="cb253-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="cb253-108">.NET Framework 針對以 *http:*、*https:*、*ftp:* 和 *file:* 開頭的 URI，提供了衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別的通訊協定專用類別。</span><span class="sxs-lookup"><span data-stu-id="cb253-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="cb253-109">如果您需要設定或讀取通訊協定專用屬性，必須將 <xref:System.Net.WebRequest> 或 <xref:System.Net.WebResponse> 物件轉換為通訊協定專用物件類型。</span><span class="sxs-lookup"><span data-stu-id="cb253-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="cb253-110">如需詳細資訊，請參閱[可插式通訊協定程式設計](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="cb253-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2.  <span data-ttu-id="cb253-111">在 `WebRequest` 物件中設定任何需要的屬性值。</span><span class="sxs-lookup"><span data-stu-id="cb253-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="cb253-112">例如，若要啟用驗證，請將 <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="cb253-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  <span data-ttu-id="cb253-113">藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>，將要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="cb253-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cb253-114">這個方法會傳回包含伺服器回應的物件。</span><span class="sxs-lookup"><span data-stu-id="cb253-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="cb253-115">傳回的 <xref:System.Net.WebResponse> 物件類型取決於要求 URI 的配置。</span><span class="sxs-lookup"><span data-stu-id="cb253-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="cb253-116">例如：</span><span class="sxs-lookup"><span data-stu-id="cb253-116">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  <span data-ttu-id="cb253-117">您可以存取 `WebResponse` 物件的屬性，或將其轉換為通訊協定專用執行個體，以讀取通訊協定專用屬性。</span><span class="sxs-lookup"><span data-stu-id="cb253-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="cb253-118">例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 專用屬性，請將 `WebResponse` 物件轉換為 `HttpWebResponse` 參考。</span><span class="sxs-lookup"><span data-stu-id="cb253-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="cb253-119">下列程式碼範例示範如何顯示與回應一起傳送的 HTTP 專用 <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> 屬性：</span><span class="sxs-lookup"><span data-stu-id="cb253-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="cb253-120">若要取得含有伺服器所傳送之回應資料的資料流，請呼叫 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cb253-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cb253-121">例如：</span><span class="sxs-lookup"><span data-stu-id="cb253-121">For example:</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="cb253-122">從回應物件讀取資料之後，請使用 <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> 方法關閉它，或使用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法關閉回應資料流。</span><span class="sxs-lookup"><span data-stu-id="cb253-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cb253-123">如果不關閉回應物件或資料流，應用程式可能會耗盡伺服器連線，而變得無法處理其他要求。</span><span class="sxs-lookup"><span data-stu-id="cb253-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="cb253-124">`WebResponse.Close` 方法在關閉回應時會呼叫 `Stream.Close`，因此不需要對回應和資料流物件呼叫 `Close`，但是這麼做也不會造成損害。</span><span class="sxs-lookup"><span data-stu-id="cb253-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="cb253-125">例如：</span><span class="sxs-lookup"><span data-stu-id="cb253-125">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="cb253-126">範例</span><span class="sxs-lookup"><span data-stu-id="cb253-126">Example</span></span>  

<span data-ttu-id="cb253-127">下列程式碼範例示範如何對網頁伺服器建立要求，並讀取其回應中的資料：</span><span class="sxs-lookup"><span data-stu-id="cb253-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>  
  
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
            // Open the stream by using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  

            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  

            // Clean up the response.  
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
            ' Open the stream by using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  

            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  

            ' Clean up the response.  
            reader.Close()  
            response.Close() 

        End Sub   

    End Class  
 
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb253-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb253-128">See also</span></span>
- [<span data-ttu-id="cb253-129">建立網際網路要求</span><span class="sxs-lookup"><span data-stu-id="cb253-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="cb253-130">在網路上使用資料流</span><span class="sxs-lookup"><span data-stu-id="cb253-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="cb253-131">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="cb253-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="cb253-132">要求資料</span><span class="sxs-lookup"><span data-stu-id="cb253-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="cb253-133">如何：使用 WebRequest 類別傳送資料</span><span class="sxs-lookup"><span data-stu-id="cb253-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
