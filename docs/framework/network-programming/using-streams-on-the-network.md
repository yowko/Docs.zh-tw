---
title: 在網路上使用資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: aa3fc56dc461d4fe22e2ff391f3561d8834128d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046882"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="3379d-102">在網路上使用資料流</span><span class="sxs-lookup"><span data-stu-id="3379d-102">Using Streams on the Network</span></span>
<span data-ttu-id="3379d-103">網路資源在 .NET Framework 中是以資料流的形式呈現。</span><span class="sxs-lookup"><span data-stu-id="3379d-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="3379d-104">因為對資料流沒有任何特殊待遇，.NET Framework 提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="3379d-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="3379d-105">以一般方式傳送和接收 Web 資料。</span><span class="sxs-lookup"><span data-stu-id="3379d-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="3379d-106">不論實際的檔案內容為何 (HTML、XML 或其他格式)，應用程式都會使用 <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> 來傳送和接收資料。</span><span class="sxs-lookup"><span data-stu-id="3379d-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="3379d-107">與整個 .NET Framework 資料流的相容性。</span><span class="sxs-lookup"><span data-stu-id="3379d-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="3379d-108">.NET Framework 中無處不使用資料流，其處理資料流的基礎結構健全。</span><span class="sxs-lookup"><span data-stu-id="3379d-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="3379d-109">例如，您可將讀取 <xref:System.IO.FileStream> 中 XML 資料的應用程式，修改為讀取 <xref:System.Net.Sockets.NetworkStream> 中的資料，而非僅變更將資料流初始化的幾行程式碼。</span><span class="sxs-lookup"><span data-stu-id="3379d-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="3379d-110">**NetworkStream** 類別與其他資料流最大的不同處，在於 **NetworkStream** 是不可搜尋的，<xref:System.Net.Sockets.NetworkStream.CanSeek%2A> 屬性一律傳回 **false**而 <xref:System.Net.Sockets.NetworkStream.Seek%2A> 和 <xref:System.Net.Sockets.NetworkStream.Position%2A> 方法則擲回 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="3379d-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="3379d-111">資料送達時的處理。</span><span class="sxs-lookup"><span data-stu-id="3379d-111">Processing of data as it arrives.</span></span> <span data-ttu-id="3379d-112">來自網路的資料以資料流方式到達時，應用程式可立即存取該資料，而不必等到整個資料集下載完成後才存取。</span><span class="sxs-lookup"><span data-stu-id="3379d-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="3379d-113"><xref:System.Net.Sockets> 命名空間包含 **NetworkStream** 類別，其可特別實作用於網路資源的 <xref:System.IO.Stream> 類別。</span><span class="sxs-lookup"><span data-stu-id="3379d-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="3379d-114"><xref:System.Net.Sockets> 命名空間中的類別會使用 **NetworkStream** 類別來代表資料流。</span><span class="sxs-lookup"><span data-stu-id="3379d-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="3379d-115">若要使用傳回的資料流將資料傳送到網路上，請在 <xref:System.Net.WebRequest> 上呼叫 <xref:System.Net.WebRequest.GetRequestStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="3379d-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="3379d-116">**WebRequest** 會將要求標題傳送至伺服器；然後您即可在傳回的資料流上呼叫 <xref:System.IO.Stream.BeginWrite%2A>、<xref:System.IO.Stream.EndWrite%2A> 或 <xref:System.IO.Stream.Write%2A> 方法，將資料傳送到網路資源。</span><span class="sxs-lookup"><span data-stu-id="3379d-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="3379d-117">有些通訊協定 (例如 HTTP) 可能會要求您先設定特定通訊協定屬性，再傳送資料。</span><span class="sxs-lookup"><span data-stu-id="3379d-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="3379d-118">下列程式碼範例示範如何設定用於傳送資料的特定 HTTP 屬性。</span><span class="sxs-lookup"><span data-stu-id="3379d-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="3379d-119">它假設變數 `sendData` 包含要傳送的資料，而變數 `sendLength` 則是要傳送資料的位元組數。</span><span class="sxs-lookup"><span data-stu-id="3379d-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="3379d-120">若要從網路接收資料，請在 <xref:System.Net.WebResponse> 上呼叫 <xref:System.Net.WebResponse.GetResponseStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="3379d-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="3379d-121">然後，您即可在傳回的資料流上呼叫 <xref:System.IO.Stream.BeginRead%2A>、<xref:System.IO.Stream.EndRead%2A> 或 <xref:System.IO.Stream.Read%2A> 方法，以讀取網路資源的資料。</span><span class="sxs-lookup"><span data-stu-id="3379d-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="3379d-122">使用網路資源的資料流時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="3379d-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="3379d-123">因為 **NetworkStream** 類別無法在資料流中變更位置，所以 **CanSeek** 屬性一律傳回 **false**。</span><span class="sxs-lookup"><span data-stu-id="3379d-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="3379d-124">**Seek** 和 **Position** 方法會擲回 **NotSupportedException**。</span><span class="sxs-lookup"><span data-stu-id="3379d-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="3379d-125">使用 **WebRequest** 和 **WebResponse** 時，呼叫 **GetResponseStream** 所建立的資料流執行個體為唯讀，而呼叫 **GetRequestStream** 所建立的資料流執行個體則為唯寫。</span><span class="sxs-lookup"><span data-stu-id="3379d-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="3379d-126">使用 <xref:System.IO.StreamReader> 類別可讓編碼工作變得更輕鬆。</span><span class="sxs-lookup"><span data-stu-id="3379d-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="3379d-127">下列程式碼範例會使用 **StreamReader** 從 **WebResponse** 讀取以 ASCII 編碼的資料流 (範例中未示範如何建立要求)。</span><span class="sxs-lookup"><span data-stu-id="3379d-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="3379d-128">如果沒有可用的網路資源，即可能會封鎖對 **GetResponse** 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3379d-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="3379d-129">您應考慮透過 <xref:System.Net.WebRequest.BeginGetResponse%2A> 和 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法使用非同步要求。</span><span class="sxs-lookup"><span data-stu-id="3379d-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="3379d-130">完成建立伺服器連線時，可能會封鎖對 **GetRequestStream** 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3379d-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="3379d-131">您應考慮透過 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 和 <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法，對資料流使用非同步要求。</span><span class="sxs-lookup"><span data-stu-id="3379d-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="3379d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3379d-132">See also</span></span>

- [<span data-ttu-id="3379d-133">如何：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="3379d-133">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="3379d-134">要求資料</span><span class="sxs-lookup"><span data-stu-id="3379d-134">Requesting Data</span></span>](requesting-data.md)
