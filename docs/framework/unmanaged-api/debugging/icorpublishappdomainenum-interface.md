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
ms.openlocfilehash: a48e20413f466e25a9145e9dbf1ba93d90155770
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397036"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="dfc14-102">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dfc14-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="dfc14-103">[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽目前存在於進程中的[ICorPublishAppDomain](icorpublishappdomain-interface.md)物件集合。</span><span class="sxs-lookup"><span data-stu-id="dfc14-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfc14-104">方法</span><span class="sxs-lookup"><span data-stu-id="dfc14-104">Methods</span></span>  
  
|<span data-ttu-id="dfc14-105">方法</span><span class="sxs-lookup"><span data-stu-id="dfc14-105">Method</span></span>|<span data-ttu-id="dfc14-106">描述</span><span class="sxs-lookup"><span data-stu-id="dfc14-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfc14-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="dfc14-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="dfc14-108">`ICorPublishAppDomain`從目前位置開始，取得集合中指定數目的實例。</span><span class="sxs-lookup"><span data-stu-id="dfc14-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc14-109">備註</span><span class="sxs-lookup"><span data-stu-id="dfc14-109">Remarks</span></span>  
 <span data-ttu-id="dfc14-110">介面會實 `ICorPublishAppDomainEnum` [ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="dfc14-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc14-111">需求</span><span class="sxs-lookup"><span data-stu-id="dfc14-111">Requirements</span></span>  
 <span data-ttu-id="dfc14-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfc14-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc14-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="dfc14-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="dfc14-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfc14-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfc14-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc14-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc14-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc14-116">See also</span></span>

- [<span data-ttu-id="dfc14-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="dfc14-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dfc14-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="dfc14-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
