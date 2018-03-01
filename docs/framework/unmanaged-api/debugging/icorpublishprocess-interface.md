---
title: "ICorPublishProcess 介面"
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
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="b6a85-102">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="b6a85-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="b6a85-103">提供存取處理序的相關資訊，以顯示的方法。</span><span class="sxs-lookup"><span data-stu-id="b6a85-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6a85-104">方法</span><span class="sxs-lookup"><span data-stu-id="b6a85-104">Methods</span></span>  
  
|<span data-ttu-id="b6a85-105">方法</span><span class="sxs-lookup"><span data-stu-id="b6a85-105">Method</span></span>|<span data-ttu-id="b6a85-106">描述</span><span class="sxs-lookup"><span data-stu-id="b6a85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6a85-107">EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="b6a85-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="b6a85-108">取得[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)包含應用程式定義域中所參考的程序的執行個體`ICorPublishProcess`。</span><span class="sxs-lookup"><span data-stu-id="b6a85-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b6a85-109">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="b6a85-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="b6a85-110">取得處理序所參考的可執行檔的完整路徑`ICorPublishProcess`。</span><span class="sxs-lookup"><span data-stu-id="b6a85-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b6a85-111">GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="b6a85-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="b6a85-112">取得處理序所參考的作業系統識別項`ICorPublishProcess`。</span><span class="sxs-lookup"><span data-stu-id="b6a85-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b6a85-113">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="b6a85-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="b6a85-114">取得值，指出是否處理程序參考這個`ICorPublishProcess`已知執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6a85-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6a85-115">需求</span><span class="sxs-lookup"><span data-stu-id="b6a85-115">Requirements</span></span>  
 <span data-ttu-id="b6a85-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6a85-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a85-117">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b6a85-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b6a85-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6a85-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6a85-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6a85-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a85-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6a85-120">See Also</span></span>  
 [<span data-ttu-id="b6a85-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b6a85-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b6a85-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="b6a85-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
