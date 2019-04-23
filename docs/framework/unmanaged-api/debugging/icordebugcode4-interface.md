---
title: ICorDebugCode4 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23f588b46eb452b7670085249938f7d10cea1ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108160"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="2cd46-102">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="2cd46-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="2cd46-103">提供方法，以允許列舉的本機變數和引數的函式中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="2cd46-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cd46-104">方法</span><span class="sxs-lookup"><span data-stu-id="2cd46-104">Methods</span></span>  
  
|<span data-ttu-id="2cd46-105">方法</span><span class="sxs-lookup"><span data-stu-id="2cd46-105">Method</span></span>|<span data-ttu-id="2cd46-106">描述</span><span class="sxs-lookup"><span data-stu-id="2cd46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cd46-107">EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="2cd46-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="2cd46-108">取得列舉值的本機變數和引數的函式中。</span><span class="sxs-lookup"><span data-stu-id="2cd46-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd46-109">備註</span><span class="sxs-lookup"><span data-stu-id="2cd46-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cd46-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2cd46-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd46-111">需求</span><span class="sxs-lookup"><span data-stu-id="2cd46-111">Requirements</span></span>  
 <span data-ttu-id="2cd46-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cd46-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd46-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cd46-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cd46-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cd46-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cd46-115">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd46-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd46-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cd46-116">See also</span></span>

- [<span data-ttu-id="2cd46-117">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="2cd46-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="2cd46-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2cd46-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
