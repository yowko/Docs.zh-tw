---
title: "要求資料"
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
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bb5c79980246a9afa5a7e5024049c26815cab49d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="requesting-data"></a><span data-ttu-id="65620-102">要求資料</span><span class="sxs-lookup"><span data-stu-id="65620-102">Requesting Data</span></span>
<span data-ttu-id="65620-103">開發在現今網際網路分散式作業環境中執行的應用程式，需要從所有類型的資源中擷取資料的有效且易用的方法。</span><span class="sxs-lookup"><span data-stu-id="65620-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="65620-104">可插式通訊協定可讓您開發應用程式，而應用程式使用單一介面來擷取多個網際網路通訊協定中的資料。</span><span class="sxs-lookup"><span data-stu-id="65620-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="65620-105">從網際網路伺服器上傳和下載資料</span><span class="sxs-lookup"><span data-stu-id="65620-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="65620-106">針對簡單要求和回應交易，<xref:System.Net.WebClient> 類別提供最簡單的模型，將資料上傳至網際網路伺服器，或從中下載資料。</span><span class="sxs-lookup"><span data-stu-id="65620-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="65620-107">**WebClient** 提供方法來上傳和下載檔案、傳送和接收資料流，並將資料緩衝區傳送至伺服器以及接收回應。</span><span class="sxs-lookup"><span data-stu-id="65620-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="65620-108">**WebClient** 會使用 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別進行實際網際網路資源連線，讓任何註冊的插入式通訊協定可供使用。</span><span class="sxs-lookup"><span data-stu-id="65620-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="65620-109">需要使用 **WebRequest** 類別和其子系，從伺服器製作更複雜交易要求資料的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="65620-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="65620-110">**WebRequest** 會封裝連線至伺服器、傳送要求以及接收回應的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="65620-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="65620-111">**WebRequest** 是定義一組屬性和方法的抽象類別，而屬性和方法可供使用可插式通訊協定的所有應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="65620-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="65620-112">**WebRequest** 子系 (例如 <xref:System.Net.HttpWebRequest>) 會使用與基礎通訊協定一致的方式，來實作 **WebRequest** 所定義的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="65620-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="65620-113">**WebRequest** 類別會使用傳遞至其 <xref:System.Net.WebRequest.Create%2A> 方法的 URI 值來建立 **WebRequest** 子系的通訊協定特定執行個體，以判斷要建立的特定衍生類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="65620-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="65620-114">應用程式指出應該使用哪個 **WebRequest** 子系來處理要求，方法是使用 <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> 方法來註冊子系的建構函式。</span><span class="sxs-lookup"><span data-stu-id="65620-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="65620-115">要求網際網路資源的方式是在 **WebRequest** 上呼叫 <xref:System.Net.WebRequest.GetResponse%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="65620-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="65620-116">**GetResponse** 方法會從 **WebRequest** 的屬性建構通訊協定特定要求，並建立與伺服器的 TCP 或 UDP 通訊端連線，然後傳送要求。</span><span class="sxs-lookup"><span data-stu-id="65620-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="65620-117">針對將資料傳送至伺服器的要求 (例如 HTTP **Post** 或 FTP **Put** 要求)，<xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> 方法提供在其中傳送資料的網路資料流。</span><span class="sxs-lookup"><span data-stu-id="65620-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="65620-118">**GetResponse** 方法會傳回符合 **WebRequest** 的通訊協定特定 **WebResponse**。</span><span class="sxs-lookup"><span data-stu-id="65620-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="65620-119">**WebResponse** 類別也是定義屬性和方法的抽象類別，而屬性和方法可供使用可插式通訊協定的所有應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="65620-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="65620-120">**WebResponse** 子系會針對基礎通訊協定實作這些屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="65620-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="65620-121">例如，<xref:System.Net.HttpWebResponse> 類別實作 **WebResponse** 類別來進行 HTTP。</span><span class="sxs-lookup"><span data-stu-id="65620-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="65620-122">向 <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> 方法所傳回資料流中的應用程式呈現伺服器所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="65620-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="65620-123">您可以像使用任何其他資料流的方式一樣來使用此資料流，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="65620-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="65620-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65620-124">See Also</span></span>  
 [<span data-ttu-id="65620-125">以 .NET Framework 進行網路程式設計</span><span class="sxs-lookup"><span data-stu-id="65620-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="65620-126">如何：要求網頁並擷取結果當作資料流</span><span class="sxs-lookup"><span data-stu-id="65620-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [<span data-ttu-id="65620-127">如何：擷取符合 WebRequest 的通訊協定特定 WebResponse</span><span class="sxs-lookup"><span data-stu-id="65620-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
