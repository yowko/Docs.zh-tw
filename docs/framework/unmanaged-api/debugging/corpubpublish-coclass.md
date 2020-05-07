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
ms.openlocfilehash: e33029e8244fdfa180a79aa4a5b05b07f594d928
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860904"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="dc3fa-102">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="dc3fa-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="dc3fa-103">提供介面來發行應用程式定義域和處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc3fa-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="dc3fa-105">介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-105">Interfaces</span></span>  
  
|<span data-ttu-id="dc3fa-106">介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-106">Interface</span></span>|<span data-ttu-id="dc3fa-107">描述</span><span class="sxs-lookup"><span data-stu-id="dc3fa-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="dc3fa-108">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="dc3fa-109">提供方法來發行進程的相關資訊，以及這些進程中的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="dc3fa-110">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="dc3fa-111">表示和提供進程中應用程式域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="dc3fa-112">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="dc3fa-113">提供方法，以跨越進程中目前存在的應用程式域集合。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="dc3fa-114">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="dc3fa-115">代表在電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="dc3fa-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dc3fa-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="dc3fa-117">提供方法來流覽電腦上正在執行的進程集合。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc3fa-118">備註</span><span class="sxs-lookup"><span data-stu-id="dc3fa-118">Remarks</span></span>  
 <span data-ttu-id="dc3fa-119">典型的發行案例牽涉到想要在應用程式域內的電腦上，對其執行的 managed 程式碼進行 debug 的開發人員。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="dc3fa-120">裝載環境可能會在進程內執行一個以上的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="dc3fa-121">開發人員想要使用圖形化使用者介面或其他方法來列出在電腦上執行的所有處理常式，並挑選特定的進程。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="dc3fa-122">清單應包含執行 managed 程式碼之進程內的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="dc3fa-123">然後，開發人員可以識別特定的應用程式域，並將偵錯工具附加至該網域。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc3fa-124">需求</span><span class="sxs-lookup"><span data-stu-id="dc3fa-124">Requirements</span></span>  
 <span data-ttu-id="dc3fa-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3fa-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc3fa-126">**標頭：** CorPub .idl</span><span class="sxs-lookup"><span data-stu-id="dc3fa-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="dc3fa-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc3fa-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc3fa-128">**.NET Framework 版本：**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc3fa-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc3fa-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3fa-129">See also</span></span>

- [<span data-ttu-id="dc3fa-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="dc3fa-130">Debugging</span></span>](index.md)
