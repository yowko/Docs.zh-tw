---
title: ICorDebugModuleBreakpoint 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3916bf8f7792e82ba905554bb32696f81634f819
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971516"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="7e888-102">ICorDebugModuleBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="7e888-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="7e888-103">提供特定模組的存取。</span><span class="sxs-lookup"><span data-stu-id="7e888-103">Provides access to specific modules.</span></span> <span data-ttu-id="7e888-104">這個介面是 ICorDebugBreakpoint 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="7e888-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e888-105">方法</span><span class="sxs-lookup"><span data-stu-id="7e888-105">Methods</span></span>  
  
|<span data-ttu-id="7e888-106">方法</span><span class="sxs-lookup"><span data-stu-id="7e888-106">Method</span></span>|<span data-ttu-id="7e888-107">描述</span><span class="sxs-lookup"><span data-stu-id="7e888-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e888-108">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="7e888-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="7e888-109">取得參考的模組設定此中斷點的位置 ICorDebugModule 介面指標。</span><span class="sxs-lookup"><span data-stu-id="7e888-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e888-110">備註</span><span class="sxs-lookup"><span data-stu-id="7e888-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e888-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7e888-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e888-112">需求</span><span class="sxs-lookup"><span data-stu-id="7e888-112">Requirements</span></span>  
 <span data-ttu-id="7e888-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e888-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e888-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e888-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e888-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e888-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e888-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e888-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e888-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e888-117">See also</span></span>
- [<span data-ttu-id="7e888-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7e888-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
