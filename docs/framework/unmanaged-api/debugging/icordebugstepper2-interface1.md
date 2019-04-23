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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073047"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="f3a2e-102">ICorDebugStepper2 介面</span><span class="sxs-lookup"><span data-stu-id="f3a2e-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="f3a2e-103">提供支援剛 my code (JMC) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="f3a2e-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3a2e-104">方法</span><span class="sxs-lookup"><span data-stu-id="f3a2e-104">Methods</span></span>  
  
|<span data-ttu-id="f3a2e-105">方法</span><span class="sxs-lookup"><span data-stu-id="f3a2e-105">Method</span></span>|<span data-ttu-id="f3a2e-106">描述</span><span class="sxs-lookup"><span data-stu-id="f3a2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3a2e-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="f3a2e-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="f3a2e-108">設定值，這個值指出是否此 ICorDebugStepper 步驟只能透過應用程式的開發人員所撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3a2e-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a2e-109">備註</span><span class="sxs-lookup"><span data-stu-id="f3a2e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a2e-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f3a2e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a2e-111">需求</span><span class="sxs-lookup"><span data-stu-id="f3a2e-111">Requirements</span></span>  
 <span data-ttu-id="f3a2e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3a2e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a2e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3a2e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3a2e-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3a2e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3a2e-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a2e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3a2e-116">See also</span></span>

- [<span data-ttu-id="f3a2e-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f3a2e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
