---
title: ICorDebugInternalFrame2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd867db8886c1c74d209e080b6b810ed4adc3654
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589330"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="d984b-102">ICorDebugInternalFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="d984b-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="d984b-103">提供內部框架，包括堆疊位址，以及相對於 ICorDebugFrame 物件位置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d984b-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d984b-104">方法</span><span class="sxs-lookup"><span data-stu-id="d984b-104">Methods</span></span>  
  
|<span data-ttu-id="d984b-105">方法</span><span class="sxs-lookup"><span data-stu-id="d984b-105">Method</span></span>|<span data-ttu-id="d984b-106">描述</span><span class="sxs-lookup"><span data-stu-id="d984b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d984b-107">GetFrameAddress 方法</span><span class="sxs-lookup"><span data-stu-id="d984b-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="d984b-108">傳回內部框架的堆疊位址。</span><span class="sxs-lookup"><span data-stu-id="d984b-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="d984b-109">IsCloserToLeaf 方法</span><span class="sxs-lookup"><span data-stu-id="d984b-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="d984b-110">檢查是否`this`內部框架是接近 ICorDebugFrame 物件和指定的分葉。</span><span class="sxs-lookup"><span data-stu-id="d984b-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d984b-111">備註</span><span class="sxs-lookup"><span data-stu-id="d984b-111">Remarks</span></span>  
 <span data-ttu-id="d984b-112">這個介面會擴充 ICorDebugInternalFrame 介面。</span><span class="sxs-lookup"><span data-stu-id="d984b-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d984b-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d984b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d984b-114">需求</span><span class="sxs-lookup"><span data-stu-id="d984b-114">Requirements</span></span>  
 <span data-ttu-id="d984b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d984b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d984b-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d984b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d984b-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d984b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d984b-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d984b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d984b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d984b-119">See also</span></span>
- [<span data-ttu-id="d984b-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d984b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d984b-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="d984b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
