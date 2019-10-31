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
ms.openlocfilehash: 89af99fab1f1265701e0dbfe74a46000cb3bfaa6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132143"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="a1586-102">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="a1586-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="a1586-103">提供介面來發行應用程式定義域和處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a1586-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1586-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1586-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="a1586-105">介面</span><span class="sxs-lookup"><span data-stu-id="a1586-105">Interfaces</span></span>  
  
|<span data-ttu-id="a1586-106">介面</span><span class="sxs-lookup"><span data-stu-id="a1586-106">Interface</span></span>|<span data-ttu-id="a1586-107">描述</span><span class="sxs-lookup"><span data-stu-id="a1586-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a1586-108">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="a1586-109">提供方法來發行進程的相關資訊，以及這些進程中的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a1586-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="a1586-110">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="a1586-111">表示和提供進程中應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a1586-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="a1586-112">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="a1586-113">提供方法，以跨越進程中目前存在的應用程式域集合。</span><span class="sxs-lookup"><span data-stu-id="a1586-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="a1586-114">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="a1586-115">代表在電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="a1586-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="a1586-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a1586-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="a1586-117">提供方法來流覽電腦上正在執行的進程集合。</span><span class="sxs-lookup"><span data-stu-id="a1586-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1586-118">備註</span><span class="sxs-lookup"><span data-stu-id="a1586-118">Remarks</span></span>  
 <span data-ttu-id="a1586-119">典型的發行案例牽涉到想要在應用程式域內的電腦上，對其執行的 managed 程式碼進行 debug 的開發人員。</span><span class="sxs-lookup"><span data-stu-id="a1586-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="a1586-120">裝載環境可能會在進程內執行一個以上的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a1586-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="a1586-121">開發人員想要使用圖形化使用者介面或其他方法來列出在電腦上執行的所有處理常式，並挑選特定的進程。</span><span class="sxs-lookup"><span data-stu-id="a1586-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="a1586-122">清單應包含執行 managed 程式碼之進程內的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a1586-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="a1586-123">然後，開發人員可以識別特定的應用程式域，並將偵錯工具附加至該網域。</span><span class="sxs-lookup"><span data-stu-id="a1586-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1586-124">需求</span><span class="sxs-lookup"><span data-stu-id="a1586-124">Requirements</span></span>  
 <span data-ttu-id="a1586-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1586-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1586-126">**標頭：** CorPub .idl</span><span class="sxs-lookup"><span data-stu-id="a1586-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="a1586-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1586-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1586-128">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1586-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1586-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1586-129">See also</span></span>

- [<span data-ttu-id="a1586-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="a1586-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
