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
ms.openlocfilehash: 161358fab9a4601e7b718321273d493bd84a3228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792017"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="cfad0-102">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="cfad0-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="cfad0-103">針對具有64以上暫存器的硬體平臺，擴充[ICorDebugRegisterSet](icordebugregisterset-interface.md)介面的功能。</span><span class="sxs-lookup"><span data-stu-id="cfad0-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfad0-104">方法</span><span class="sxs-lookup"><span data-stu-id="cfad0-104">Methods</span></span>  
  
|<span data-ttu-id="cfad0-105">方法</span><span class="sxs-lookup"><span data-stu-id="cfad0-105">Method</span></span>|<span data-ttu-id="cfad0-106">描述</span><span class="sxs-lookup"><span data-stu-id="cfad0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfad0-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="cfad0-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="cfad0-108">取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。</span><span class="sxs-lookup"><span data-stu-id="cfad0-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="cfad0-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="cfad0-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="cfad0-110">取得提供可用暫存器之點陣圖的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="cfad0-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="cfad0-111">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="cfad0-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="cfad0-112">未在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="cfad0-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfad0-113">備註</span><span class="sxs-lookup"><span data-stu-id="cfad0-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfad0-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cfad0-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfad0-115">需求</span><span class="sxs-lookup"><span data-stu-id="cfad0-115">Requirements</span></span>  
 <span data-ttu-id="cfad0-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cfad0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfad0-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfad0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfad0-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfad0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfad0-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfad0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfad0-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfad0-120">See also</span></span>

- [<span data-ttu-id="cfad0-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cfad0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cfad0-122">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="cfad0-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
