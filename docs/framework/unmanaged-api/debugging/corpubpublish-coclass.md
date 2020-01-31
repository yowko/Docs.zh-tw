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
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789210"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="1c964-102">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="1c964-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="1c964-103">提供介面來發行應用程式定義域和處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1c964-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c964-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c964-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="1c964-105">介面</span><span class="sxs-lookup"><span data-stu-id="1c964-105">Interfaces</span></span>  
  
|<span data-ttu-id="1c964-106">介面</span><span class="sxs-lookup"><span data-stu-id="1c964-106">Interface</span></span>|<span data-ttu-id="1c964-107">描述</span><span class="sxs-lookup"><span data-stu-id="1c964-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="1c964-108">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="1c964-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="1c964-109">提供方法來發行進程的相關資訊，以及這些進程中的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="1c964-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="1c964-110">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="1c964-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="1c964-111">表示和提供進程中應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1c964-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="1c964-112">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1c964-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="1c964-113">提供方法，以跨越進程中目前存在的應用程式域集合。</span><span class="sxs-lookup"><span data-stu-id="1c964-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="1c964-114">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="1c964-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="1c964-115">代表在電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1c964-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="1c964-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1c964-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="1c964-117">提供方法來流覽電腦上正在執行的進程集合。</span><span class="sxs-lookup"><span data-stu-id="1c964-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c964-118">備註</span><span class="sxs-lookup"><span data-stu-id="1c964-118">Remarks</span></span>  
 <span data-ttu-id="1c964-119">典型的發行案例牽涉到想要在應用程式域內的電腦上，對其執行的 managed 程式碼進行 debug 的開發人員。</span><span class="sxs-lookup"><span data-stu-id="1c964-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="1c964-120">裝載環境可能會在進程內執行一個以上的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="1c964-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="1c964-121">開發人員想要使用圖形化使用者介面或其他方法來列出在電腦上執行的所有處理常式，並挑選特定的進程。</span><span class="sxs-lookup"><span data-stu-id="1c964-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="1c964-122">清單應包含執行 managed 程式碼之進程內的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="1c964-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="1c964-123">然後，開發人員可以識別特定的應用程式域，並將偵錯工具附加至該網域。</span><span class="sxs-lookup"><span data-stu-id="1c964-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c964-124">需求</span><span class="sxs-lookup"><span data-stu-id="1c964-124">Requirements</span></span>  
 <span data-ttu-id="1c964-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c964-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c964-126">**標頭：** CorPub .idl</span><span class="sxs-lookup"><span data-stu-id="1c964-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="1c964-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c964-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c964-128">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c964-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c964-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c964-129">See also</span></span>

- [<span data-ttu-id="1c964-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="1c964-130">Debugging</span></span>](index.md)
