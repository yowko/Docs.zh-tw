---
title: ICorDebugCode2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2
helpviewer_keywords: ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7de0bdddd20dd073adfd38565bb1e94e8f2806e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode2-interface1"></a><span data-ttu-id="ca124-102">ICorDebugCode2 Interface1</span><span class="sxs-lookup"><span data-stu-id="ca124-102">ICorDebugCode2 Interface1</span></span>
<span data-ttu-id="ca124-103">提供擴充功能的 「 ICorDebugCode"的方法。</span><span class="sxs-lookup"><span data-stu-id="ca124-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca124-104">方法</span><span class="sxs-lookup"><span data-stu-id="ca124-104">Methods</span></span>  
  
|<span data-ttu-id="ca124-105">方法</span><span class="sxs-lookup"><span data-stu-id="ca124-105">Method</span></span>|<span data-ttu-id="ca124-106">說明</span><span class="sxs-lookup"><span data-stu-id="ca124-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca124-107">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="ca124-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="ca124-108">取得這個程式碼物件組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="ca124-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="ca124-109">GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="ca124-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="ca124-110">取得指定的程式碼已此物件可能是在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 產生之條件的旗標。</span><span class="sxs-lookup"><span data-stu-id="ca124-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca124-111">備註</span><span class="sxs-lookup"><span data-stu-id="ca124-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca124-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ca124-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca124-113">需求</span><span class="sxs-lookup"><span data-stu-id="ca124-113">Requirements</span></span>  
 <span data-ttu-id="ca124-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca124-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca124-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca124-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca124-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca124-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca124-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca124-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca124-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca124-118">See Also</span></span>  
    
 [<span data-ttu-id="ca124-119">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="ca124-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="ca124-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ca124-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
