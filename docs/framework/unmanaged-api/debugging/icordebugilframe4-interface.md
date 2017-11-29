---
title: "ICorDebugILFrame4 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame4
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b42a2ed4e93fd5e4c662bab34b111fe0757890
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="4a8d2-102">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="4a8d2-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="4a8d2-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="4a8d2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4a8d2-104">提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="4a8d2-105">參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a8d2-106">方法</span><span class="sxs-lookup"><span data-stu-id="4a8d2-106">Methods</span></span>  
  
|<span data-ttu-id="4a8d2-107">方法</span><span class="sxs-lookup"><span data-stu-id="4a8d2-107">Method</span></span>|<span data-ttu-id="4a8d2-108">說明</span><span class="sxs-lookup"><span data-stu-id="4a8d2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a8d2-109">EnumerateLocalVariablesEx 方法</span><span class="sxs-lookup"><span data-stu-id="4a8d2-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="4a8d2-110">傳回目前框架中可用的區域變數清單。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="4a8d2-111">GetCodeEx 方法</span><span class="sxs-lookup"><span data-stu-id="4a8d2-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="4a8d2-112">傳回此堆疊框架正在執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="4a8d2-113">GetLocalVariableEx 方法</span><span class="sxs-lookup"><span data-stu-id="4a8d2-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="4a8d2-114">傳回 IL 框架中的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a8d2-115">備註</span><span class="sxs-lookup"><span data-stu-id="4a8d2-115">Remarks</span></span>  
 <span data-ttu-id="4a8d2-116">這些方法會提供所提供的功能[EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)， [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)，和[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="4a8d2-117">每個方法都包含 `flags` 參數，可指定是否顯示分析工具 ReJIT 要求所定義的區域變數或程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a8d2-118">需求</span><span class="sxs-lookup"><span data-stu-id="4a8d2-118">Requirements</span></span>  
 <span data-ttu-id="4a8d2-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a8d2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a8d2-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a8d2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a8d2-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a8d2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a8d2-122">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a8d2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8d2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a8d2-123">See Also</span></span>  
 [<span data-ttu-id="4a8d2-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4a8d2-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4a8d2-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="4a8d2-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
