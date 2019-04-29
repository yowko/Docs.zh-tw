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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752252"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="1eb8d-102">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="1eb8d-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="1eb8d-103">提供方法，以允許列舉的本機變數和引數的函式中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1eb8d-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1eb8d-104">方法</span><span class="sxs-lookup"><span data-stu-id="1eb8d-104">Methods</span></span>  
  
|<span data-ttu-id="1eb8d-105">方法</span><span class="sxs-lookup"><span data-stu-id="1eb8d-105">Method</span></span>|<span data-ttu-id="1eb8d-106">描述</span><span class="sxs-lookup"><span data-stu-id="1eb8d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1eb8d-107">EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="1eb8d-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="1eb8d-108">取得列舉值的本機變數和引數的函式中。</span><span class="sxs-lookup"><span data-stu-id="1eb8d-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eb8d-109">備註</span><span class="sxs-lookup"><span data-stu-id="1eb8d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1eb8d-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1eb8d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb8d-111">需求</span><span class="sxs-lookup"><span data-stu-id="1eb8d-111">Requirements</span></span>  
 <span data-ttu-id="1eb8d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1eb8d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb8d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eb8d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eb8d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eb8d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eb8d-115">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb8d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb8d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1eb8d-116">See also</span></span>

- [<span data-ttu-id="1eb8d-117">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="1eb8d-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="1eb8d-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1eb8d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
