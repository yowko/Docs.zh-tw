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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05d9eef36885aee05d88f7da994c8b168c3221b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130529"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="91d3f-102">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="91d3f-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="91d3f-103">提供介面來發行應用程式定義域和處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91d3f-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="91d3f-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="91d3f-105">介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-105">Interfaces</span></span>  
  
|<span data-ttu-id="91d3f-106">介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-106">Interface</span></span>|<span data-ttu-id="91d3f-107">描述</span><span class="sxs-lookup"><span data-stu-id="91d3f-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="91d3f-108">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="91d3f-109">提供方法來發行這些處理序中的程序和應用程式定義域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91d3f-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="91d3f-110">ICorPublishAppDomain 介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="91d3f-111">表示，並提供有關應用程式定義域的處理序中的資訊。</span><span class="sxs-lookup"><span data-stu-id="91d3f-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="91d3f-112">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="91d3f-113">提供方法來周遊目前存在於處理程序的應用程式定義域的集合。</span><span class="sxs-lookup"><span data-stu-id="91d3f-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="91d3f-114">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="91d3f-115">表示執行的電腦的處理序。</span><span class="sxs-lookup"><span data-stu-id="91d3f-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="91d3f-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="91d3f-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="91d3f-117">提供方法來周遊的電腦執行的處理序的集合。</span><span class="sxs-lookup"><span data-stu-id="91d3f-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91d3f-118">備註</span><span class="sxs-lookup"><span data-stu-id="91d3f-118">Remarks</span></span>  
 <span data-ttu-id="91d3f-119">典型的發佈案例牽涉到的開發人員想要偵錯應用程式定義域中的電腦執行的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="91d3f-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="91d3f-120">裝載的環境可能正在執行的處理序中的多個應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="91d3f-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="91d3f-121">開發人員想要使用圖形化使用者介面或其他一些方法來列出所有的電腦執行的處理程序，並挑選特定的處理程序。</span><span class="sxs-lookup"><span data-stu-id="91d3f-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="91d3f-122">清單中應該包含的所有應用程式定義域內執行 managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="91d3f-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="91d3f-123">開發人員接著識別特定的應用程式定義域，並將偵錯工具附加至該定義域。</span><span class="sxs-lookup"><span data-stu-id="91d3f-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d3f-124">需求</span><span class="sxs-lookup"><span data-stu-id="91d3f-124">Requirements</span></span>  
 <span data-ttu-id="91d3f-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91d3f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91d3f-126">**標頭：** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="91d3f-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="91d3f-127">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91d3f-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="91d3f-128">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="91d3f-128">.NET Framework Versions:</span></span>**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91d3f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d3f-129">See also</span></span>

- [<span data-ttu-id="91d3f-130">偵錯</span><span class="sxs-lookup"><span data-stu-id="91d3f-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
