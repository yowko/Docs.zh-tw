---
title: CorpubPublish Coclass
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="3ed10-102">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="3ed10-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="3ed10-103">提供介面來發行應用程式定義域和處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3ed10-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed10-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ed10-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="3ed10-105">介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-105">Interfaces</span></span>  
  
|<span data-ttu-id="3ed10-106">介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-106">Interface</span></span>|<span data-ttu-id="3ed10-107">描述</span><span class="sxs-lookup"><span data-stu-id="3ed10-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="3ed10-108">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="3ed10-109">提供方法讓這些處理序在發佈程序和應用程式定義域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3ed10-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="3ed10-110">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="3ed10-111">代表，並提供有關應用程式定義域的程序中的資訊。</span><span class="sxs-lookup"><span data-stu-id="3ed10-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="3ed10-112">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="3ed10-113">提供方法來周遊目前存在於處理程序的應用程式網域的集合。</span><span class="sxs-lookup"><span data-stu-id="3ed10-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="3ed10-114">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="3ed10-115">表示執行的電腦的處理序。</span><span class="sxs-lookup"><span data-stu-id="3ed10-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="3ed10-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="3ed10-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="3ed10-117">提供方法來周遊的電腦上執行的處理序的集合。</span><span class="sxs-lookup"><span data-stu-id="3ed10-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ed10-118">備註</span><span class="sxs-lookup"><span data-stu-id="3ed10-118">Remarks</span></span>  
 <span data-ttu-id="3ed10-119">典型的發佈案例牽涉到的開發人員想要偵錯應用程式定義域中的電腦執行的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ed10-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="3ed10-120">裝載環境可能執行之處理序中的多個應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="3ed10-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="3ed10-121">開發人員想要使用圖形化使用者介面或其他方式來列出所有電腦執行的處理程序，並選取特定的處理程序。</span><span class="sxs-lookup"><span data-stu-id="3ed10-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="3ed10-122">清單中應該包含的所有應用程式網域內執行 managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="3ed10-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="3ed10-123">開發人員可以識別該特定應用程式定義域，並將偵錯工具附加至該定義域。</span><span class="sxs-lookup"><span data-stu-id="3ed10-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ed10-124">需求</span><span class="sxs-lookup"><span data-stu-id="3ed10-124">Requirements</span></span>  
 <span data-ttu-id="3ed10-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ed10-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ed10-126">**標頭：** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="3ed10-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="3ed10-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ed10-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ed10-128">**.NET framework 版本：**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ed10-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed10-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ed10-129">See Also</span></span>  
 [<span data-ttu-id="3ed10-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="3ed10-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
