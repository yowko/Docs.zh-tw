---
title: "ICorPublishEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f09d0f80eba86d03d0db7af8fd63d2231c9a88d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="089f9-102">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="089f9-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="089f9-103">做為處理程序和應用程式定義域的相關資訊的發行中所使用的列舉值的抽象基底介面。</span><span class="sxs-lookup"><span data-stu-id="089f9-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="089f9-104">方法</span><span class="sxs-lookup"><span data-stu-id="089f9-104">Methods</span></span>  
  
|<span data-ttu-id="089f9-105">方法</span><span class="sxs-lookup"><span data-stu-id="089f9-105">Method</span></span>|<span data-ttu-id="089f9-106">描述</span><span class="sxs-lookup"><span data-stu-id="089f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="089f9-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="089f9-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="089f9-108">建立一份這`ICorPublishEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="089f9-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="089f9-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="089f9-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="089f9-110">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="089f9-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="089f9-111">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="089f9-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="089f9-112">將游標移至列舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="089f9-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="089f9-113">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="089f9-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="089f9-114">將游標移往前列舉中所指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="089f9-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="089f9-115">備註</span><span class="sxs-lookup"><span data-stu-id="089f9-115">Remarks</span></span>  
 <span data-ttu-id="089f9-116">下列的列舉值衍生自`ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="089f9-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="089f9-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="089f9-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="089f9-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="089f9-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="089f9-119">需求</span><span class="sxs-lookup"><span data-stu-id="089f9-119">Requirements</span></span>  
 <span data-ttu-id="089f9-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="089f9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089f9-121">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="089f9-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="089f9-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="089f9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="089f9-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089f9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089f9-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="089f9-124">See Also</span></span>  
 [<span data-ttu-id="089f9-125">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="089f9-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="089f9-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="089f9-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
