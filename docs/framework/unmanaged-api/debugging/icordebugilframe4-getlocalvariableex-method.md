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
ms.openlocfilehash: eb4eaaa23a810a23852dc5ef88d61c6a5d0f0ccd
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926812"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="25d23-102">ICorDebugILFrame4::GetLocalVariableEx 方法</span><span class="sxs-lookup"><span data-stu-id="25d23-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="25d23-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="25d23-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="25d23-104">從此中繼語言 (IL) 堆疊框架中取得指定區域變數的值，並選擇是否要存取加入分析工具 ReJIT 測試設備中的變數。</span><span class="sxs-lookup"><span data-stu-id="25d23-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d23-105">語法</span><span class="sxs-lookup"><span data-stu-id="25d23-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25d23-106">參數</span><span class="sxs-lookup"><span data-stu-id="25d23-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="25d23-107">在[ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)列舉成員，指定在 profiler ReJIT 檢測中加入的變數是否包含在框架中。</span><span class="sxs-lookup"><span data-stu-id="25d23-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="25d23-108">[in] IL 堆疊框架中之區域變數的索引。</span><span class="sxs-lookup"><span data-stu-id="25d23-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="25d23-109">脫銷代表所抓取值之 "ICorDebugValue" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="25d23-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25d23-110">備註</span><span class="sxs-lookup"><span data-stu-id="25d23-110">Remarks</span></span>  
 <span data-ttu-id="25d23-111">這個方法類似于[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)方法，不同之處在于它會選擇性地存取在 profiler ReJIT 檢測中加入的變數。</span><span class="sxs-lookup"><span data-stu-id="25d23-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="25d23-112">使用`flags`的`ILCODE_ORIGINAL_IL`值呼叫此方法相當於呼叫[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); 如果方法是以其他區域變數檢測，則無法存取這些變數。</span><span class="sxs-lookup"><span data-stu-id="25d23-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="25d23-113">`ILCODE_REJIT_IL` 允許偵錯程式存取加入分析工具 ReJIT 測試設備中的區域變數。</span><span class="sxs-lookup"><span data-stu-id="25d23-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="25d23-114">若測試設備不是 IL，此方法會傳回 `E_INVALIDARG`。</span><span class="sxs-lookup"><span data-stu-id="25d23-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25d23-115">需求</span><span class="sxs-lookup"><span data-stu-id="25d23-115">Requirements</span></span>  
 <span data-ttu-id="25d23-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25d23-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25d23-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25d23-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25d23-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25d23-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25d23-119">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25d23-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d23-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25d23-120">See also</span></span>

- [<span data-ttu-id="25d23-121">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="25d23-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="25d23-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="25d23-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="25d23-123">ReJIT使用說明指南</span><span class="sxs-lookup"><span data-stu-id="25d23-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
