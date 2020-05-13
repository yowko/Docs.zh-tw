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
ms.openlocfilehash: f989f1c1f29c63af54ff125f4ad1aaa2bcee6757
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378206"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="8f786-102">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="8f786-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="8f786-103">針對具有64以上暫存器的硬體平臺，擴充[ICorDebugRegisterSet](icordebugregisterset-interface.md)介面的功能。</span><span class="sxs-lookup"><span data-stu-id="8f786-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f786-104">方法</span><span class="sxs-lookup"><span data-stu-id="8f786-104">Methods</span></span>  
  
|<span data-ttu-id="8f786-105">方法</span><span class="sxs-lookup"><span data-stu-id="8f786-105">Method</span></span>|<span data-ttu-id="8f786-106">描述</span><span class="sxs-lookup"><span data-stu-id="8f786-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f786-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="8f786-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="8f786-108">取得位元遮罩所指定之每個暫存器（目前執行程式碼的電腦）的值。</span><span class="sxs-lookup"><span data-stu-id="8f786-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="8f786-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="8f786-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="8f786-110">取得提供可用暫存器之點陣圖的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="8f786-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="8f786-111">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="8f786-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="8f786-112">未在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="8f786-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f786-113">備註</span><span class="sxs-lookup"><span data-stu-id="8f786-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f786-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8f786-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f786-115">需求</span><span class="sxs-lookup"><span data-stu-id="8f786-115">Requirements</span></span>  
 <span data-ttu-id="8f786-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f786-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f786-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f786-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f786-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f786-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f786-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f786-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f786-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f786-120">See also</span></span>

- [<span data-ttu-id="8f786-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8f786-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8f786-122">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="8f786-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
