---
title: ICorDebugRegisterSet2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30cecaa1832ba9d45782b164ee65a2f39f28a8f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605402"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="33877-102">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="33877-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="33877-103">擴充功能[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)具有 64 個以上的暫存器的硬體平台的介面。</span><span class="sxs-lookup"><span data-stu-id="33877-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33877-104">方法</span><span class="sxs-lookup"><span data-stu-id="33877-104">Methods</span></span>  
  
|<span data-ttu-id="33877-105">方法</span><span class="sxs-lookup"><span data-stu-id="33877-105">Method</span></span>|<span data-ttu-id="33877-106">描述</span><span class="sxs-lookup"><span data-stu-id="33877-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33877-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="33877-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="33877-108">取得每個暫存器值 （在電腦上目前正在執行的程式碼） 所指定的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="33877-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="33877-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="33877-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="33877-110">取得位元組陣列，提供可用的暫存器的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="33877-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="33877-111">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="33877-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="33877-112">.NET Framework 2.0 版中尚未實作。</span><span class="sxs-lookup"><span data-stu-id="33877-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33877-113">備註</span><span class="sxs-lookup"><span data-stu-id="33877-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33877-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="33877-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33877-115">需求</span><span class="sxs-lookup"><span data-stu-id="33877-115">Requirements</span></span>  
 <span data-ttu-id="33877-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33877-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33877-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33877-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33877-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33877-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33877-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33877-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33877-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33877-120">See also</span></span>
- [<span data-ttu-id="33877-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="33877-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="33877-122">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="33877-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
