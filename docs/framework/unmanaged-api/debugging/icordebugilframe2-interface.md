---
title: ICorDebugILFrame2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4f57f27ec92e7977b46ebfa5967b0590674d2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946467"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="f843c-102">ICorDebugILFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="f843c-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="f843c-103">ICorDebugILFrame 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="f843c-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f843c-104">方法</span><span class="sxs-lookup"><span data-stu-id="f843c-104">Methods</span></span>  
  
|<span data-ttu-id="f843c-105">方法</span><span class="sxs-lookup"><span data-stu-id="f843c-105">Method</span></span>|<span data-ttu-id="f843c-106">描述</span><span class="sxs-lookup"><span data-stu-id="f843c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f843c-107">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="f843c-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="f843c-108">取得包含 ICorDebugTypeEnum 物件<xref:System.Type>這個框架中的參數。</span><span class="sxs-lookup"><span data-stu-id="f843c-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="f843c-109">RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="f843c-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="f843c-110">將編輯過的函式中指定新的 MSIL 位移重新對應。</span><span class="sxs-lookup"><span data-stu-id="f843c-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f843c-111">備註</span><span class="sxs-lookup"><span data-stu-id="f843c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f843c-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f843c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f843c-113">需求</span><span class="sxs-lookup"><span data-stu-id="f843c-113">Requirements</span></span>  
 <span data-ttu-id="f843c-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f843c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f843c-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f843c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f843c-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f843c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f843c-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f843c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f843c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f843c-118">See also</span></span>

- [<span data-ttu-id="f843c-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f843c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
