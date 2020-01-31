---
title: ICorProfilerFunctionControl 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 1286ce953c96eb3e3164ba5b209031dd1ec5c453
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864696"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="51429-102">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="51429-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="51429-103">提供的方法可讓程式碼分析工具與通用語言執行平台 (CLR) 進行通訊，以控制在重新編譯特定方法時，JIT 編譯器應如何產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="51429-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51429-104">方法</span><span class="sxs-lookup"><span data-stu-id="51429-104">Methods</span></span>  
  
|<span data-ttu-id="51429-105">方法</span><span class="sxs-lookup"><span data-stu-id="51429-105">Method</span></span>|<span data-ttu-id="51429-106">描述</span><span class="sxs-lookup"><span data-stu-id="51429-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51429-107">SetCodegenFlags 方法</span><span class="sxs-lookup"><span data-stu-id="51429-107">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="51429-108">設定[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列舉中的一或多個旗標，以控制即時（JIT）重新編譯函式的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="51429-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="51429-109">SetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="51429-109">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="51429-110">取代方法的 Common Intermediate Language (CIL) 主體。</span><span class="sxs-lookup"><span data-stu-id="51429-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="51429-111">SetILInstrumentedCodeMap 方法</span><span class="sxs-lookup"><span data-stu-id="51429-111">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="51429-112">使用指定的通用中間語言 (CIL) 對應項目，為所指定的函式設定程式碼對應。</span><span class="sxs-lookup"><span data-stu-id="51429-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51429-113">備註</span><span class="sxs-lookup"><span data-stu-id="51429-113">Remarks</span></span>  
 <span data-ttu-id="51429-114">`ICorProfilerFunctionControl` 介面可提供方法來控制單一重新編譯函式的程式碼產生方式。</span><span class="sxs-lookup"><span data-stu-id="51429-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="51429-115">分析工具會透過[ICorProfilerCallback4：： GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md)回呼來取得此介面的實例。</span><span class="sxs-lookup"><span data-stu-id="51429-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="51429-116">`ICorProfilerFunctionControl` 的每個執行個體各控制一個函式的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="51429-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51429-117">需求</span><span class="sxs-lookup"><span data-stu-id="51429-117">Requirements</span></span>  
 <span data-ttu-id="51429-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51429-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51429-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51429-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51429-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51429-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51429-121">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51429-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51429-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="51429-122">See also</span></span>

- [<span data-ttu-id="51429-123">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="51429-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="51429-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="51429-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="51429-125">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="51429-125">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
