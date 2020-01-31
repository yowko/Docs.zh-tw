---
title: ICorPublishProcessEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790501"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="243ea-102">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="243ea-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="243ea-103">[ICorPublishEnum](icorpublishenum-interface.md)介面的子類別，提供方法來流覽[ICorPublishProcess](icorpublishprocess-interface.md)物件的集合。</span><span class="sxs-lookup"><span data-stu-id="243ea-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="243ea-104">方法</span><span class="sxs-lookup"><span data-stu-id="243ea-104">Methods</span></span>  
  
|<span data-ttu-id="243ea-105">方法</span><span class="sxs-lookup"><span data-stu-id="243ea-105">Method</span></span>|<span data-ttu-id="243ea-106">描述</span><span class="sxs-lookup"><span data-stu-id="243ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="243ea-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="243ea-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="243ea-108">從目前位置開始，取得集合中指定數目的 `ICorPublishProcess` 實例。</span><span class="sxs-lookup"><span data-stu-id="243ea-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="243ea-109">備註</span><span class="sxs-lookup"><span data-stu-id="243ea-109">Remarks</span></span>  
 <span data-ttu-id="243ea-110">`ICorPublishProcessEnum` 介面會實[ICorPublishEnum](icorpublishenum-interface.md)抽象介面的方法。</span><span class="sxs-lookup"><span data-stu-id="243ea-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="243ea-111">`ICorPublishProcessEnum` 實例是由[ICorPublish：： EnumProcesses](icorpublish-enumprocesses-method.md)方法所建立。</span><span class="sxs-lookup"><span data-stu-id="243ea-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="243ea-112">`ICorPublishProcess` 物件集合的遍歷是以建立 `ICorPublishProcessEnum` 實例時所指定的篩選準則為基礎。</span><span class="sxs-lookup"><span data-stu-id="243ea-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="243ea-113">需求</span><span class="sxs-lookup"><span data-stu-id="243ea-113">Requirements</span></span>  
 <span data-ttu-id="243ea-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="243ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243ea-115">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="243ea-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="243ea-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="243ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="243ea-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243ea-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="243ea-118">See also</span></span>

- [<span data-ttu-id="243ea-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="243ea-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="243ea-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="243ea-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
