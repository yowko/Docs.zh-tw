---
title: 存取應用程式 Web 服務 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: a321776692366c64acf4ad3a01c31bc91947e2cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521058"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="73b89-102">存取應用程式 Web 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73b89-102">Accessing Application Web Services (Visual Basic)</span></span>
<span data-ttu-id="73b89-103">`My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="73b89-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="73b89-104">每個執行個體都是依需要具現化。</span><span class="sxs-lookup"><span data-stu-id="73b89-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="73b89-105">您可以透過 `My.WebServices` 物件的屬性來存取這些 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="73b89-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="73b89-106">屬性名稱和屬性存取的 Web 服務名稱相同。</span><span class="sxs-lookup"><span data-stu-id="73b89-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="73b89-107">任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別都是 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="73b89-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="73b89-108">工作</span><span class="sxs-lookup"><span data-stu-id="73b89-108">Tasks</span></span>  
 <span data-ttu-id="73b89-109">下表列出存取應用程式所參考之 Web 服務的可能方式。</span><span class="sxs-lookup"><span data-stu-id="73b89-109">The following table lists possible ways to access Web services referenced by an application.</span></span>  
  
|<span data-ttu-id="73b89-110">以</span><span class="sxs-lookup"><span data-stu-id="73b89-110">To</span></span>|<span data-ttu-id="73b89-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="73b89-111">See</span></span>|  
|---|---|   
|<span data-ttu-id="73b89-112">呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="73b89-112">Call a Web service</span></span>|[<span data-ttu-id="73b89-113">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="73b89-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|<span data-ttu-id="73b89-114">以非同步方式呼叫 Web 服務並於完成時處理事件</span><span class="sxs-lookup"><span data-stu-id="73b89-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="73b89-115">如何：非同步地呼叫 Web 服務</span><span class="sxs-lookup"><span data-stu-id="73b89-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="73b89-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73b89-116">See also</span></span>
- [<span data-ttu-id="73b89-117">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="73b89-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
