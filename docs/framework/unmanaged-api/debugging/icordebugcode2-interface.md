---
title: ICorDebugCode2 介面 1
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a5c28ec6c447f3fc3305e0faf51aa868d5a4c17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499969"
---
# <a name="icordebugcode2-interface1"></a><span data-ttu-id="5b5b6-102">ICorDebugCode2 介面 1</span><span class="sxs-lookup"><span data-stu-id="5b5b6-102">ICorDebugCode2 Interface1</span></span>
<span data-ttu-id="5b5b6-103">提供擴充功能的 「 ICorDebugCode"的方法。</span><span class="sxs-lookup"><span data-stu-id="5b5b6-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b5b6-104">方法</span><span class="sxs-lookup"><span data-stu-id="5b5b6-104">Methods</span></span>  
  
|<span data-ttu-id="5b5b6-105">方法</span><span class="sxs-lookup"><span data-stu-id="5b5b6-105">Method</span></span>|<span data-ttu-id="5b5b6-106">描述</span><span class="sxs-lookup"><span data-stu-id="5b5b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b5b6-107">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="5b5b6-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="5b5b6-108">取得這個程式碼物件組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="5b5b6-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="5b5b6-109">GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="5b5b6-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="5b5b6-110">取得指定所在這個程式碼物件是其中一個在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 所產生之條件的旗標。</span><span class="sxs-lookup"><span data-stu-id="5b5b6-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b5b6-111">備註</span><span class="sxs-lookup"><span data-stu-id="5b5b6-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b5b6-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5b5b6-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b5b6-113">需求</span><span class="sxs-lookup"><span data-stu-id="5b5b6-113">Requirements</span></span>  
 <span data-ttu-id="5b5b6-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b5b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b5b6-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b5b6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b5b6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b5b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b5b6-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b5b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5b6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b5b6-118">See also</span></span>

- [<span data-ttu-id="5b5b6-119">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="5b5b6-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="5b5b6-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5b5b6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
