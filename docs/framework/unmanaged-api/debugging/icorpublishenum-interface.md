---
title: ICorPublishEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5206b7cd07acd76237ab72268b492782ac6e49ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616715"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="73326-102">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="73326-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="73326-103">可作為抽象的基底介面，可在發佈程序和應用程式定義域的相關資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="73326-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73326-104">方法</span><span class="sxs-lookup"><span data-stu-id="73326-104">Methods</span></span>  
  
|<span data-ttu-id="73326-105">方法</span><span class="sxs-lookup"><span data-stu-id="73326-105">Method</span></span>|<span data-ttu-id="73326-106">描述</span><span class="sxs-lookup"><span data-stu-id="73326-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73326-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="73326-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="73326-108">建立一份這`ICorPublishEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="73326-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="73326-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="73326-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="73326-110">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="73326-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="73326-111">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="73326-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="73326-112">移動資料指標的列舉型別的開頭。</span><span class="sxs-lookup"><span data-stu-id="73326-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="73326-113">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="73326-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="73326-114">將游標移往前列舉中所指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="73326-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73326-115">備註</span><span class="sxs-lookup"><span data-stu-id="73326-115">Remarks</span></span>  
 <span data-ttu-id="73326-116">下列的列舉值衍生自`ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="73326-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="73326-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="73326-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="73326-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="73326-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="73326-119">需求</span><span class="sxs-lookup"><span data-stu-id="73326-119">Requirements</span></span>  
 <span data-ttu-id="73326-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73326-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73326-121">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="73326-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="73326-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73326-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73326-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73326-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73326-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73326-124">See also</span></span>
- [<span data-ttu-id="73326-125">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="73326-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="73326-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="73326-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
