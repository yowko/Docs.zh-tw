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
ms.openlocfilehash: d02dab01eca3bd4f8ce3ae7ace7f9d4be8233dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917010"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="360de-102">ICorDebugILFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="360de-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="360de-103">ICorDebugILFrame 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="360de-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="360de-104">方法</span><span class="sxs-lookup"><span data-stu-id="360de-104">Methods</span></span>  
  
|<span data-ttu-id="360de-105">方法</span><span class="sxs-lookup"><span data-stu-id="360de-105">Method</span></span>|<span data-ttu-id="360de-106">說明</span><span class="sxs-lookup"><span data-stu-id="360de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="360de-107">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="360de-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="360de-108">取得 ICorDebugTypeEnum 物件, 其中包含此<xref:System.Type>框架中的參數。</span><span class="sxs-lookup"><span data-stu-id="360de-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="360de-109">RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="360de-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="360de-110">藉由指定新的 MSIL 位移來重新對應已編輯的函式。</span><span class="sxs-lookup"><span data-stu-id="360de-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="360de-111">備註</span><span class="sxs-lookup"><span data-stu-id="360de-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="360de-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="360de-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360de-113">需求</span><span class="sxs-lookup"><span data-stu-id="360de-113">Requirements</span></span>  
 <span data-ttu-id="360de-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="360de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360de-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="360de-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="360de-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="360de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="360de-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="360de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360de-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="360de-118">See also</span></span>

- [<span data-ttu-id="360de-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="360de-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
