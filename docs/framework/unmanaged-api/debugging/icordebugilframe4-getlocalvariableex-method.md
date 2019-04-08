---
title: ICorDebugILFrame4::GetLocalVariableEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6594bb72ce9cd2fbfa9cdafebc152a90618b810
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193079"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="1ad2b-102">ICorDebugILFrame4::GetLocalVariableEx 方法</span><span class="sxs-lookup"><span data-stu-id="1ad2b-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="1ad2b-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="1ad2b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1ad2b-104">從此中繼語言 (IL) 堆疊框架中取得指定區域變數的值，並選擇是否要存取加入分析工具 ReJIT 測試設備中的變數。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad2b-105">語法</span><span class="sxs-lookup"><span data-stu-id="1ad2b-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ad2b-106">參數</span><span class="sxs-lookup"><span data-stu-id="1ad2b-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="1ad2b-107">[in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)列舉的成員，指定是否要將分析工具 ReJIT 檢測中加入的變數包含在框架中。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="1ad2b-108">[in] IL 堆疊框架中之區域變數的索引。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1ad2b-109">[out]表示擷取的值的"ICorDebugValue 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ad2b-110">備註</span><span class="sxs-lookup"><span data-stu-id="1ad2b-110">Remarks</span></span>  
 <span data-ttu-id="1ad2b-111">這個方法很類似[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)方法，但是它會選擇性地存取加入分析工具 ReJIT 檢測中的變數。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="1ad2b-112">呼叫此方法時`flags`的值`ILCODE_ORIGINAL_IL`相當於呼叫[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); 如果使用額外的本機變數，已檢測的方法無法存取這些變數。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> `ILCODE_REJIT_IL` <span data-ttu-id="1ad2b-113">可讓偵錯工具存取加入分析工具 ReJIT 檢測中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-113">allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="1ad2b-114">若測試設備不是 IL，此方法會傳回 `E_INVALIDARG`。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ad2b-115">需求</span><span class="sxs-lookup"><span data-stu-id="1ad2b-115">Requirements</span></span>  
 <span data-ttu-id="1ad2b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ad2b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ad2b-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ad2b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ad2b-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ad2b-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1ad2b-119">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="1ad2b-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ad2b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad2b-120">See also</span></span>

- [<span data-ttu-id="1ad2b-121">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="1ad2b-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="1ad2b-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1ad2b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1ad2b-123">ReJIT:操作說明指南</span><span class="sxs-lookup"><span data-stu-id="1ad2b-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
