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
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790669"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="c01e2-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="c01e2-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="c01e2-103">[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽目前存在於進程中的[ICorPublishAppDomain](icorpublishappdomain-interface.md)物件集合。</span><span class="sxs-lookup"><span data-stu-id="c01e2-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c01e2-104">方法</span><span class="sxs-lookup"><span data-stu-id="c01e2-104">Methods</span></span>  
  
|<span data-ttu-id="c01e2-105">方法</span><span class="sxs-lookup"><span data-stu-id="c01e2-105">Method</span></span>|<span data-ttu-id="c01e2-106">描述</span><span class="sxs-lookup"><span data-stu-id="c01e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c01e2-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="c01e2-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="c01e2-108">從目前位置開始，取得集合中指定數目的 `ICorPublishAppDomain` 實例。</span><span class="sxs-lookup"><span data-stu-id="c01e2-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c01e2-109">備註</span><span class="sxs-lookup"><span data-stu-id="c01e2-109">Remarks</span></span>  
 <span data-ttu-id="c01e2-110">`ICorPublishAppDomainEnum` 介面會實[ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="c01e2-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c01e2-111">需求</span><span class="sxs-lookup"><span data-stu-id="c01e2-111">Requirements</span></span>  
 <span data-ttu-id="c01e2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c01e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c01e2-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="c01e2-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c01e2-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c01e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c01e2-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c01e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01e2-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c01e2-116">See also</span></span>

- [<span data-ttu-id="c01e2-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c01e2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c01e2-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="c01e2-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
