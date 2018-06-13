---
title: ICorDebugStepper2 Interface1
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
ms.openlocfilehash: 4652bcb00d3437350b5fd3e1071b3c538403cfe3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418685"
---
# <a name="icordebugstepper2-interface1"></a><span data-ttu-id="4c656-102">ICorDebugStepper2 Interface1</span><span class="sxs-lookup"><span data-stu-id="4c656-102">ICorDebugStepper2 Interface1</span></span>
<span data-ttu-id="4c656-103">提供 just my code (JMC) 偵錯的支援。</span><span class="sxs-lookup"><span data-stu-id="4c656-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c656-104">方法</span><span class="sxs-lookup"><span data-stu-id="4c656-104">Methods</span></span>  
  
|<span data-ttu-id="4c656-105">方法</span><span class="sxs-lookup"><span data-stu-id="4c656-105">Method</span></span>|<span data-ttu-id="4c656-106">描述</span><span class="sxs-lookup"><span data-stu-id="4c656-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c656-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="4c656-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="4c656-108">設定值，指定這個 ICorDebugStepper 是否只能透過應用程式的開發人員所撰寫的程式碼的步驟。</span><span class="sxs-lookup"><span data-stu-id="4c656-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c656-109">備註</span><span class="sxs-lookup"><span data-stu-id="4c656-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c656-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4c656-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c656-111">需求</span><span class="sxs-lookup"><span data-stu-id="4c656-111">Requirements</span></span>  
 <span data-ttu-id="4c656-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c656-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c656-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c656-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c656-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c656-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c656-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c656-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c656-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c656-116">See Also</span></span>  
 [<span data-ttu-id="4c656-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4c656-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
