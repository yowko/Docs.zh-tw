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
ms.openlocfilehash: c04bb3a7584fcb783af929e87713dbec67ad705f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712313"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="18d71-102">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="18d71-102">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="18d71-103">針對具有超過64暫存器的硬體平臺，擴充 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 介面的功能。</span><span class="sxs-lookup"><span data-stu-id="18d71-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18d71-104">方法</span><span class="sxs-lookup"><span data-stu-id="18d71-104">Methods</span></span>  
  
|<span data-ttu-id="18d71-105">方法</span><span class="sxs-lookup"><span data-stu-id="18d71-105">Method</span></span>|<span data-ttu-id="18d71-106">描述</span><span class="sxs-lookup"><span data-stu-id="18d71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18d71-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="18d71-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="18d71-108">取得電腦上每個登錄 (的值，此電腦上目前正在執行位元遮罩所指定的程式碼) 。</span><span class="sxs-lookup"><span data-stu-id="18d71-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="18d71-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="18d71-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="18d71-110">取得位元組陣列，以提供可用暫存器的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="18d71-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="18d71-111">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="18d71-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="18d71-112">未在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="18d71-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18d71-113">備註</span><span class="sxs-lookup"><span data-stu-id="18d71-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18d71-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="18d71-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18d71-115">需求</span><span class="sxs-lookup"><span data-stu-id="18d71-115">Requirements</span></span>  

 <span data-ttu-id="18d71-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18d71-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18d71-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18d71-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18d71-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18d71-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18d71-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18d71-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d71-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18d71-120">See also</span></span>

- [<span data-ttu-id="18d71-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="18d71-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="18d71-122">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="18d71-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
