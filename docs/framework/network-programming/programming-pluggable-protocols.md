---
title: 可插式通訊協定程式設計
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047393"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="4bbc9-102">可插式通訊協定程式設計</span><span class="sxs-lookup"><span data-stu-id="4bbc9-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="4bbc9-103">抽象 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別提供可插式通訊協定的基底。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="4bbc9-104">透過從 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 衍生通訊協定特定類別，應用程式可以要求來自網際網路資源的資料，並讀取回應，而不需要指定所要使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="4bbc9-105">建立通訊協定特定 <xref:System.Net.WebRequest> 之前，您必須先註冊 Create 方法。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="4bbc9-106">使用 <xref:System.Net.WebRequest> 的靜態 <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> 方法來註冊 <xref:System.Net.WebRequest> 子系，以處理對特定網際網路配置、配置和伺服器或者配置、伺服器和路徑的一組要求。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="4bbc9-107">在大部分情況下，您將可以使用 <xref:System.Net.WebRequest> 類別的方法和屬性來傳送和接收資料。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="4bbc9-108">不過，如果您需要存取通訊協定特定屬性，則可以將 <xref:System.Net.WebRequest> 類型轉換為特定衍生類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="4bbc9-109">若要善用可插式通訊協定，<xref:System.Net.WebRequest> 子系必須提供不需要設定通訊協定特定屬性的預設要求和回應交易。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="4bbc9-110">例如，實作 <xref:System.Net.WebRequest> 類別以進行 HTTP 的 <xref:System.Net.HttpWebRequest> 類別預設會提供 `GET` 要求，並傳回包含從網頁伺服器傳回之資料流的 <xref:System.Net.HttpWebResponse>。</span><span class="sxs-lookup"><span data-stu-id="4bbc9-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bbc9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bbc9-111">See also</span></span>

- [<span data-ttu-id="4bbc9-112">衍生自 WebRequest</span><span class="sxs-lookup"><span data-stu-id="4bbc9-112">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="4bbc9-113">衍生自 WebResponse</span><span class="sxs-lookup"><span data-stu-id="4bbc9-113">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="4bbc9-114">以 .NET Framework 進行網路程式設計</span><span class="sxs-lookup"><span data-stu-id="4bbc9-114">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="4bbc9-115">如何：轉換 WebRequest 類型以存取通訊協定特定屬性</span><span class="sxs-lookup"><span data-stu-id="4bbc9-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
