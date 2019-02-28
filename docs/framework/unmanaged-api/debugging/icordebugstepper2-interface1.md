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
ms.openlocfilehash: 69adabbe5bb607e00d383c8bd80d9e150608890e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970404"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="7b184-102">ICorDebugStepper2 介面</span><span class="sxs-lookup"><span data-stu-id="7b184-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="7b184-103">提供支援剛 my code (JMC) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="7b184-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b184-104">方法</span><span class="sxs-lookup"><span data-stu-id="7b184-104">Methods</span></span>  
  
|<span data-ttu-id="7b184-105">方法</span><span class="sxs-lookup"><span data-stu-id="7b184-105">Method</span></span>|<span data-ttu-id="7b184-106">描述</span><span class="sxs-lookup"><span data-stu-id="7b184-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b184-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="7b184-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="7b184-108">設定值，這個值指出是否此 ICorDebugStepper 步驟只能透過應用程式的開發人員所撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b184-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b184-109">備註</span><span class="sxs-lookup"><span data-stu-id="7b184-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b184-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7b184-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b184-111">需求</span><span class="sxs-lookup"><span data-stu-id="7b184-111">Requirements</span></span>  
 <span data-ttu-id="7b184-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b184-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b184-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b184-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b184-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b184-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b184-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b184-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b184-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b184-116">See also</span></span>
- [<span data-ttu-id="7b184-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7b184-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
