---
title: ICorPublishAppDomainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: cbe2aa48a8b67b0b6e88f7b5267bc70848fe3cec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140322"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="8a057-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8a057-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="8a057-103">[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)介面的子類別，提供方法來流覽目前存在於進程中的[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)物件集合。</span><span class="sxs-lookup"><span data-stu-id="8a057-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a057-104">方法</span><span class="sxs-lookup"><span data-stu-id="8a057-104">Methods</span></span>  
  
|<span data-ttu-id="8a057-105">方法</span><span class="sxs-lookup"><span data-stu-id="8a057-105">Method</span></span>|<span data-ttu-id="8a057-106">描述</span><span class="sxs-lookup"><span data-stu-id="8a057-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a057-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="8a057-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="8a057-108">從目前位置開始，取得集合中指定數目的 `ICorPublishAppDomain` 實例。</span><span class="sxs-lookup"><span data-stu-id="8a057-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a057-109">備註</span><span class="sxs-lookup"><span data-stu-id="8a057-109">Remarks</span></span>  
 <span data-ttu-id="8a057-110">`ICorPublishAppDomainEnum` 介面會實[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="8a057-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a057-111">需求</span><span class="sxs-lookup"><span data-stu-id="8a057-111">Requirements</span></span>  
 <span data-ttu-id="8a057-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a057-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a057-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="8a057-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8a057-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a057-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a057-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a057-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a057-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a057-116">See also</span></span>

- [<span data-ttu-id="8a057-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8a057-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a057-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="8a057-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
