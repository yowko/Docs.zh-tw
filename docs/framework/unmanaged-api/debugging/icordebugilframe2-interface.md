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
ms.openlocfilehash: 08c2946a9bd6251f377ea594c0c3ca5d1bd98c67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095096"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="01296-102">ICorDebugILFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="01296-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="01296-103">ICorDebugILFrame 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="01296-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01296-104">方法</span><span class="sxs-lookup"><span data-stu-id="01296-104">Methods</span></span>  
  
|<span data-ttu-id="01296-105">方法</span><span class="sxs-lookup"><span data-stu-id="01296-105">Method</span></span>|<span data-ttu-id="01296-106">描述</span><span class="sxs-lookup"><span data-stu-id="01296-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01296-107">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="01296-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="01296-108">取得 ICorDebugTypeEnum 物件，其中包含此框架中的 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="01296-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="01296-109">RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="01296-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="01296-110">藉由指定新的 MSIL 位移來重新對應已編輯的函式。</span><span class="sxs-lookup"><span data-stu-id="01296-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01296-111">備註</span><span class="sxs-lookup"><span data-stu-id="01296-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01296-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="01296-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01296-113">需求</span><span class="sxs-lookup"><span data-stu-id="01296-113">Requirements</span></span>  
 <span data-ttu-id="01296-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01296-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01296-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01296-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01296-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01296-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01296-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01296-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01296-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="01296-118">See also</span></span>

- [<span data-ttu-id="01296-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="01296-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
