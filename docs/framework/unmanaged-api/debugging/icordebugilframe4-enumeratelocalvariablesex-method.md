---
title: "ICorDebugILFrame4::EnumerateLocalVariablesEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="58f1e-102">ICorDebugILFrame4::EnumerateLocalVariablesEx 方法</span><span class="sxs-lookup"><span data-stu-id="58f1e-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="58f1e-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="58f1e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="58f1e-104">在框架中取得區域變數的列舉程式，並選擇性地包含在分析工具 ReJIT 檢測中加入的變數。</span><span class="sxs-lookup"><span data-stu-id="58f1e-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f1e-105">語法</span><span class="sxs-lookup"><span data-stu-id="58f1e-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58f1e-106">參數</span><span class="sxs-lookup"><span data-stu-id="58f1e-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="58f1e-107">[in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)列舉的成員，指定是否包含在分析工具 ReJIT 檢測中加入的變數在框架中。</span><span class="sxs-lookup"><span data-stu-id="58f1e-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="58f1e-108">[out]是這個框架中區域變數的列舉值 」 ICorDebugValueEnum 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="58f1e-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58f1e-109">備註</span><span class="sxs-lookup"><span data-stu-id="58f1e-109">Remarks</span></span>  
 <span data-ttu-id="58f1e-110">這個方法是類似於[EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)方法，但是它會選擇性地存取分析工具 ReJIT 檢測中加入的變數。</span><span class="sxs-lookup"><span data-stu-id="58f1e-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="58f1e-111">設定`flags`至`ILCODE_ORIGINAL_IL`就相當於呼叫[icordebugilframe:: Enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)。</span><span class="sxs-lookup"><span data-stu-id="58f1e-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="58f1e-112">將 `flags` 設為 `ILCODE_REJIT_IL` 可允許偵錯工具存取加入在分析工具 ReJIT 檢測中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="58f1e-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="58f1e-113">如果未檢測中繼語言 (IL)，則列舉空白，且該方法會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="58f1e-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="58f1e-114">列舉程式可能不會包含執行中方法的所有區域變數，因為有些變數可能不在使用中。</span><span class="sxs-lookup"><span data-stu-id="58f1e-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58f1e-115">需求</span><span class="sxs-lookup"><span data-stu-id="58f1e-115">Requirements</span></span>  
 <span data-ttu-id="58f1e-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58f1e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58f1e-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58f1e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58f1e-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58f1e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58f1e-119">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58f1e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f1e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="58f1e-120">See Also</span></span>  
 [<span data-ttu-id="58f1e-121">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="58f1e-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="58f1e-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58f1e-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="58f1e-123">ReJIT： 使用說明指南</span><span class="sxs-lookup"><span data-stu-id="58f1e-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
