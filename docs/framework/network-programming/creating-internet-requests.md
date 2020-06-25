---
title: 建立網際網路要求
description: 瞭解應用程式如何透過 WebRequest 建立 WebRequest 實例，此方法會根據傳遞給它的 URI 配置來建立衍生類別。
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
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325639"
---
# <a name="create-internet-requests"></a><span data-ttu-id="1f2f3-103">建立網際網路要求</span><span class="sxs-lookup"><span data-stu-id="1f2f3-103">Create internet requests</span></span>

<span data-ttu-id="1f2f3-104">應用程式會透過 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法來建立 <xref:System.Net.WebRequest> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1f2f3-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>是一種靜態方法，會 <xref:System.Net.WebRequest> 根據傳遞給它的 URI 配置，建立衍生自的類別。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> is a static method that creates a class derived from <xref:System.Net.WebRequest> based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="1f2f3-106">Web、檔案和 FTP 要求</span><span class="sxs-lookup"><span data-stu-id="1f2f3-106">Web, file, and FTP requests</span></span>

<span data-ttu-id="1f2f3-107">.NET Framework 提供 <xref:System.Net.HttpWebRequest> 衍生自的類別， `WebRequest` 以處理 HTTP 和 HTTPS 要求。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-107">.NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from `WebRequest`, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="1f2f3-108">在大多數情況下， `WebRequest` 類別會提供提出要求所需的所有屬性; 不過，如有必要，您可以將 `WebRequest` 方法所建立的物件轉換 `WebRequest.Create` 成 `HttpWebRequest` 類型，以存取要求的 HTTP 特定屬性。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-108">In most cases, the `WebRequest` class provides all the properties you need to make a request; however, if necessary, you can cast `WebRequest` objects created by the `WebRequest.Create` method to the `HttpWebRequest` type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="1f2f3-109">同樣地， `HttpWebResponse` 物件會處理來自 HTTP 和 HTTPS 要求的回應。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-109">Similarly, the `HttpWebResponse` object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="1f2f3-110">若要存取物件的 HTTP 特定屬性 `HttpWebResponse` ，您必須將 `WebResponse` 物件轉換成 `HttpWebResponse` 類型。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-110">To access the HTTP-specific properties of the `HttpWebResponse` object, you need to cast `WebResponse` objects to the `HttpWebResponse` type.</span></span>  
  
<span data-ttu-id="1f2f3-111">.NET Framework 也會提供 <xref:System.Net.FileWebRequest> 和 <xref:System.Net.FileWebResponse> 類別，來處理使用 "file：" URI 配置之資源的要求。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-111">.NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="1f2f3-112">同樣地，提供 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別，以處理使用 "ftp:" 配置之資源的要求。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="1f2f3-113">如果您的要求是針對使用任何這些配置的資源，您可以使用 `WebRequest.Create` 方法來取得要用來提出要求的物件。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-113">If your request is for a resource that uses any of these schemes, you can use the `WebRequest.Create` method to obtain an object with which to make your request.</span></span>  
  
<span data-ttu-id="1f2f3-114">若要處理使用其他應用層級通訊協定的要求，請執行衍生自和的通訊協定特定類別 `WebRequest` `WebResponse` 。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-114">To handle requests that use other application-level protocols, implement protocol-specific classes derived from `WebRequest` and `WebResponse`.</span></span> <span data-ttu-id="1f2f3-115">如需詳細資訊，請參閱程式[設計插即用通訊協定](programming-pluggable-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="1f2f3-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2f3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f2f3-116">See also</span></span>

- [<span data-ttu-id="1f2f3-117">如何：使用 WebRequest 類別要求資料</span><span class="sxs-lookup"><span data-stu-id="1f2f3-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="1f2f3-118">要求資料</span><span class="sxs-lookup"><span data-stu-id="1f2f3-118">Requesting Data</span></span>](requesting-data.md)
