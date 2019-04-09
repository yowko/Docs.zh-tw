---
title: ICorDebugILFrame4 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17c7630160af78fe3163e6962b8fe085af1edc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206612"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="33101-102">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="33101-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="33101-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="33101-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="33101-104">提供的方法可讓您在中繼語言 (IL) 程式碼的框架中，存取區域變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="33101-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="33101-105">參數可指定偵錯工具是否能夠存取在分析工具 ReJIT 檢測中加入的變數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="33101-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33101-106">方法</span><span class="sxs-lookup"><span data-stu-id="33101-106">Methods</span></span>  
  
|<span data-ttu-id="33101-107">方法</span><span class="sxs-lookup"><span data-stu-id="33101-107">Method</span></span>|<span data-ttu-id="33101-108">描述</span><span class="sxs-lookup"><span data-stu-id="33101-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33101-109">EnumerateLocalVariablesEx 方法</span><span class="sxs-lookup"><span data-stu-id="33101-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="33101-110">傳回目前框架中可用的區域變數清單。</span><span class="sxs-lookup"><span data-stu-id="33101-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="33101-111">GetCodeEx 方法</span><span class="sxs-lookup"><span data-stu-id="33101-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="33101-112">傳回此堆疊框架正在執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="33101-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="33101-113">GetLocalVariableEx 方法</span><span class="sxs-lookup"><span data-stu-id="33101-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="33101-114">傳回 IL 框架中的區域變數值。</span><span class="sxs-lookup"><span data-stu-id="33101-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33101-115">備註</span><span class="sxs-lookup"><span data-stu-id="33101-115">Remarks</span></span>  
 <span data-ttu-id="33101-116">這些方法會提供除了所提供的功能[EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)， [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)，並[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="33101-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="33101-117">每個方法都包含 `flags` 參數，可指定是否顯示分析工具 ReJIT 要求所定義的區域變數或程式碼。</span><span class="sxs-lookup"><span data-stu-id="33101-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33101-118">需求</span><span class="sxs-lookup"><span data-stu-id="33101-118">Requirements</span></span>  
 <span data-ttu-id="33101-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33101-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33101-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33101-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33101-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33101-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="33101-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="33101-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33101-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33101-123">See also</span></span>

- [<span data-ttu-id="33101-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="33101-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="33101-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="33101-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
