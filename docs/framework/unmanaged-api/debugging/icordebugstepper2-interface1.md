---
title: ICorDebugStepper2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256f67d21a22ee4692d88311cc150736e61563a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987411"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="28f7b-102">ICorDebugStepper2 介面</span><span class="sxs-lookup"><span data-stu-id="28f7b-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="28f7b-103">提供支援剛 my code (JMC) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="28f7b-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28f7b-104">方法</span><span class="sxs-lookup"><span data-stu-id="28f7b-104">Methods</span></span>  
  
|<span data-ttu-id="28f7b-105">方法</span><span class="sxs-lookup"><span data-stu-id="28f7b-105">Method</span></span>|<span data-ttu-id="28f7b-106">描述</span><span class="sxs-lookup"><span data-stu-id="28f7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28f7b-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="28f7b-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="28f7b-108">設定值，這個值指出是否此 ICorDebugStepper 步驟只能透過應用程式的開發人員所撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="28f7b-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28f7b-109">備註</span><span class="sxs-lookup"><span data-stu-id="28f7b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28f7b-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="28f7b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28f7b-111">需求</span><span class="sxs-lookup"><span data-stu-id="28f7b-111">Requirements</span></span>  
 <span data-ttu-id="28f7b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28f7b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28f7b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28f7b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28f7b-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28f7b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28f7b-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28f7b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f7b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28f7b-116">See also</span></span>

- [<span data-ttu-id="28f7b-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="28f7b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
