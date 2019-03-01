---
title: ICorDebugCode2 介面
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
ms.openlocfilehash: dce3e3e4baeaa351c5ed1d9e5ca2c03631c3fce4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964263"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="c4dd2-102">ICorDebugCode2 介面</span><span class="sxs-lookup"><span data-stu-id="c4dd2-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="c4dd2-103">提供擴充功能的 「 ICorDebugCode"的方法。</span><span class="sxs-lookup"><span data-stu-id="c4dd2-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4dd2-104">方法</span><span class="sxs-lookup"><span data-stu-id="c4dd2-104">Methods</span></span>  
  
|<span data-ttu-id="c4dd2-105">方法</span><span class="sxs-lookup"><span data-stu-id="c4dd2-105">Method</span></span>|<span data-ttu-id="c4dd2-106">描述</span><span class="sxs-lookup"><span data-stu-id="c4dd2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4dd2-107">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="c4dd2-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="c4dd2-108">取得這個程式碼物件組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c4dd2-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="c4dd2-109">GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="c4dd2-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="c4dd2-110">取得指定所在這個程式碼物件是其中一個在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 所產生之條件的旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dd2-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4dd2-111">備註</span><span class="sxs-lookup"><span data-stu-id="c4dd2-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4dd2-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4dd2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4dd2-113">需求</span><span class="sxs-lookup"><span data-stu-id="c4dd2-113">Requirements</span></span>  
 <span data-ttu-id="c4dd2-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4dd2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4dd2-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4dd2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4dd2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4dd2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4dd2-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4dd2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4dd2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4dd2-118">See also</span></span>

- [<span data-ttu-id="c4dd2-119">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="c4dd2-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="c4dd2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c4dd2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
