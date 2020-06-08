---
title: 如何：使用 WebRequest 類別要求資料
description: 瞭解如何使用 .NET Framework 中的 WebRequest 類別，從伺服器要求資源（例如網頁或檔案）。
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
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502466"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="43206-103">如何：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="43206-103">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="43206-104">下列程序描述向伺服器要求資源 (例如網頁或檔案) 的步驟。</span><span class="sxs-lookup"><span data-stu-id="43206-104">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="43206-105">資源必須是以 URI 識別。</span><span class="sxs-lookup"><span data-stu-id="43206-105">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="43206-106">向主機伺服器要求資料</span><span class="sxs-lookup"><span data-stu-id="43206-106">To request data from a host server</span></span>

1. <span data-ttu-id="43206-107">使用資源的 URI 來呼叫 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>，以建立 <xref:System.Net.WebRequest> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="43206-107">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="43206-108">例如：</span><span class="sxs-lookup"><span data-stu-id="43206-108">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="43206-109">.NET Framework 針對以 *http:*、*https:*、*ftp:* 和 *file:* 開頭的 URI，提供了衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別的通訊協定專用類別。</span><span class="sxs-lookup"><span data-stu-id="43206-109">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="43206-110">如果您需要設定或讀取通訊協定專用屬性，必須將 <xref:System.Net.WebRequest> 或 <xref:System.Net.WebResponse> 物件轉換為通訊協定專用物件類型。</span><span class="sxs-lookup"><span data-stu-id="43206-110">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="43206-111">如需詳細資訊，請參閱[可插式通訊協定程式設計](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="43206-111">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="43206-112">在 `WebRequest` 物件中設定任何需要的屬性值。</span><span class="sxs-lookup"><span data-stu-id="43206-112">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="43206-113">例如，若要啟用驗證，請將 <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Net.NetworkCredential> 類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="43206-113">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="43206-114">藉由呼叫 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>，將要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="43206-114">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="43206-115">這個方法會傳回包含伺服器回應的物件。</span><span class="sxs-lookup"><span data-stu-id="43206-115">This method returns an object containing the server's response.</span></span> <span data-ttu-id="43206-116">傳回的 <xref:System.Net.WebResponse> 物件類型取決於要求 URI 的配置。</span><span class="sxs-lookup"><span data-stu-id="43206-116">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="43206-117">例如：</span><span class="sxs-lookup"><span data-stu-id="43206-117">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="43206-118">您可以存取 `WebResponse` 物件的屬性，或將其轉換為通訊協定專用執行個體，以讀取通訊協定專用屬性。</span><span class="sxs-lookup"><span data-stu-id="43206-118">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="43206-119">例如，若要存取 <xref:System.Net.HttpWebResponse> 的 HTTP 專用屬性，請將 `WebResponse` 物件轉換為 `HttpWebResponse` 參考。</span><span class="sxs-lookup"><span data-stu-id="43206-119">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="43206-120">下列程式碼範例示範如何顯示與回應一起傳送的 HTTP 專用 <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> 屬性：</span><span class="sxs-lookup"><span data-stu-id="43206-120">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="43206-121">若要取得含有伺服器所傳送之回應資料的資料流，請呼叫 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="43206-121">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="43206-122">例如：</span><span class="sxs-lookup"><span data-stu-id="43206-122">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="43206-123">從回應物件讀取資料之後，請使用 <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> 方法關閉它，或使用 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法關閉回應資料流。</span><span class="sxs-lookup"><span data-stu-id="43206-123">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="43206-124">如果不關閉回應物件或資料流，應用程式可能會耗盡伺服器連線，而變得無法處理其他要求。</span><span class="sxs-lookup"><span data-stu-id="43206-124">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="43206-125">`WebResponse.Close` 方法在關閉回應時會呼叫 `Stream.Close`，因此不需要對回應和資料流物件呼叫 `Close`，但是這麼做也不會造成損害。</span><span class="sxs-lookup"><span data-stu-id="43206-125">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="43206-126">例如：</span><span class="sxs-lookup"><span data-stu-id="43206-126">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="43206-127">範例</span><span class="sxs-lookup"><span data-stu-id="43206-127">Example</span></span>

<span data-ttu-id="43206-128">下列程式碼範例示範如何對網頁伺服器建立要求，並讀取其回應中的資料：</span><span class="sxs-lookup"><span data-stu-id="43206-128">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="43206-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43206-129">See also</span></span>

- [<span data-ttu-id="43206-130">建立網際網路要求</span><span class="sxs-lookup"><span data-stu-id="43206-130">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="43206-131">在網路上使用資料流程</span><span class="sxs-lookup"><span data-stu-id="43206-131">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="43206-132">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="43206-132">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="43206-133">要求資料</span><span class="sxs-lookup"><span data-stu-id="43206-133">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="43206-134">如何：使用 WebRequest 類別傳送資料</span><span class="sxs-lookup"><span data-stu-id="43206-134">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
