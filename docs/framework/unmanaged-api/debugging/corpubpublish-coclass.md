---
title: CorpubPublish Coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: c73eab14bf6f9f9599bed79f4c5f85ed035c0518
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722345"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="679ee-102">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="679ee-102">CorpubPublish Coclass</span></span>

<span data-ttu-id="679ee-103">提供介面來發行應用程式定義域和處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="679ee-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="679ee-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="679ee-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="679ee-105">介面</span><span class="sxs-lookup"><span data-stu-id="679ee-105">Interfaces</span></span>  
  
|<span data-ttu-id="679ee-106">介面</span><span class="sxs-lookup"><span data-stu-id="679ee-106">Interface</span></span>|<span data-ttu-id="679ee-107">描述</span><span class="sxs-lookup"><span data-stu-id="679ee-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="679ee-108">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="679ee-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="679ee-109">提供在這些進程中發佈進程和應用程式域相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="679ee-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="679ee-110">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="679ee-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="679ee-111">代表和提供進程中應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="679ee-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="679ee-112">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="679ee-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="679ee-113">提供方法，這些方法會遍歷目前存在於進程內的應用程式域集合。</span><span class="sxs-lookup"><span data-stu-id="679ee-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="679ee-114">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="679ee-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="679ee-115">代表在電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="679ee-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="679ee-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="679ee-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="679ee-117">提供可跨越電腦上執行之處理常式集合的方法。</span><span class="sxs-lookup"><span data-stu-id="679ee-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="679ee-118">備註</span><span class="sxs-lookup"><span data-stu-id="679ee-118">Remarks</span></span>  

 <span data-ttu-id="679ee-119">典型的發佈案例牽涉到開發人員，想要在應用程式域內的電腦上執行 managed 程式碼的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="679ee-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="679ee-120">裝載環境可能在進程中執行一個以上的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="679ee-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="679ee-121">開發人員想要使用圖形化使用者介面，或使用其他方法來列出電腦上執行的所有處理常式，然後挑選特定的進程。</span><span class="sxs-lookup"><span data-stu-id="679ee-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="679ee-122">此清單應包含執行 managed 程式碼之進程內的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="679ee-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="679ee-123">然後，開發人員可以識別特定的應用程式域，並將偵錯工具附加至該網域。</span><span class="sxs-lookup"><span data-stu-id="679ee-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="679ee-124">需求</span><span class="sxs-lookup"><span data-stu-id="679ee-124">Requirements</span></span>  

 <span data-ttu-id="679ee-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="679ee-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="679ee-126">**標頭：** CorPub .idl</span><span class="sxs-lookup"><span data-stu-id="679ee-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="679ee-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="679ee-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="679ee-128">**.NET Framework 版本：**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="679ee-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679ee-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="679ee-129">See also</span></span>

- [<span data-ttu-id="679ee-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="679ee-130">Debugging</span></span>](index.md)
