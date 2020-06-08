---
title: 建立網際網路要求
description: 瞭解應用程式如何透過 WebRequest 建立 WebRequest 實例。 Create，這是一種靜態方法，會根據傳遞給它的 URI 配置來建立衍生類別。
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502622"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="4d0e9-103">建立網際網路要求</span><span class="sxs-lookup"><span data-stu-id="4d0e9-103">Creating Internet Requests</span></span>
<span data-ttu-id="4d0e9-104">應用程式會透過 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法來建立 <xref:System.Net.WebRequest> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4d0e9-105">這是建立衍生自 **WebRequest** 之類別的靜態方法 (視傳遞給它的 URI 配置而定)。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-105">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="4d0e9-106">Web、檔案和 FTP 要求</span><span class="sxs-lookup"><span data-stu-id="4d0e9-106">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="4d0e9-107">.NET Framework 提供衍生自 **WebRequest** 的 <xref:System.Net.HttpWebRequest> 類別，來處理 HTTP 和 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-107">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="4d0e9-108">在大部分情況下，**WebRequest** 類別會提供您提出要求所需的所有屬性；不過，必要時，您可以將 **WebRequest.Create** 方法所建立的 **WebRequest** 物件轉換為 **HttpWebRequest** 類型，以存取要求的 HTTP 特定屬性。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-108">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="4d0e9-109">同樣地，**HttpWebResponse** 物件會處理來自 HTTP 和 HTTPS 要求的回應。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-109">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="4d0e9-110">若要存取 **HttpWebResponse** 物件的 HTTP 特定屬性，您需要將 **WebResponse** 物件轉換為 **HttpWebResponse** 類型。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-110">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="4d0e9-111">.NET Framework 也會提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 類別，來處理使用 "file:" URI 配置之資源的要求。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-111">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="4d0e9-112">同樣地，提供 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別，以處理使用 "ftp:" 配置之資源的要求。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="4d0e9-113">如果您的要求適用於使用所有這些配置的資源，則可以使用 **WebRequest.Create** 方法，來取得用來提出要求的物件。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-113">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="4d0e9-114">若要處理使用其他應用程式層級通訊協定的要求，您需要實作衍生自 **WebRequest** 和 **WebResponse** 的通訊協定特定類別。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-114">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="4d0e9-115">如需詳細資訊，請參閱程式[設計插即用通訊協定](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="4d0e9-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0e9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d0e9-116">See also</span></span>

- [<span data-ttu-id="4d0e9-117">如何：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="4d0e9-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="4d0e9-118">要求資料</span><span class="sxs-lookup"><span data-stu-id="4d0e9-118">Requesting Data</span></span>](requesting-data.md)
