---
title: ICorDebugILFrame4::GetCodeEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: e77344a99189ec8e234129262d45698c794dc249
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788519"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="968d4-102">ICorDebugILFrame4::GetCodeEx 方法</span><span class="sxs-lookup"><span data-stu-id="968d4-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="968d4-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="968d4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="968d4-104">取得此堆疊框架執行之程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="968d4-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="968d4-105">語法</span><span class="sxs-lookup"><span data-stu-id="968d4-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="968d4-106">參數</span><span class="sxs-lookup"><span data-stu-id="968d4-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="968d4-107">在[ILCodeKind](ilcodekind-enumeration.md)列舉成員，指定由 Profiler 的 ReJIT 要求所定義的中繼語言（IL）是否包含在框架中。</span><span class="sxs-lookup"><span data-stu-id="968d4-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="968d4-108">脫銷代表此堆疊框架正在執行之程式碼的 "ICorDebugCode" 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="968d4-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="968d4-109">備註</span><span class="sxs-lookup"><span data-stu-id="968d4-109">Remarks</span></span>  
 <span data-ttu-id="968d4-110">這個方法類似于[ICorDebugFrame：： GetCode](icordebugframe-getcode-method.md)方法，不同之處在于它會選擇性地存取分析工具的 ReJIT 要求所定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="968d4-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="968d4-111">使用 `ILCODE_ORIGINAL_IL` 的 `flags` 值呼叫此方法相當於呼叫[GetCode](icordebugframe-getcode-method.md);如果已檢測此方法，則無法存取其 IL。</span><span class="sxs-lookup"><span data-stu-id="968d4-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="968d4-112">`ILCODE_REJIT_IL` 可讓偵錯工具存取分析工具的 ReJIT 要求所定義的 IL。</span><span class="sxs-lookup"><span data-stu-id="968d4-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="968d4-113">如果未檢測 IL，`ppCode` 為**null**，且方法會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="968d4-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="968d4-114">需求</span><span class="sxs-lookup"><span data-stu-id="968d4-114">Requirements</span></span>  
 <span data-ttu-id="968d4-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="968d4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968d4-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="968d4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="968d4-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="968d4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="968d4-118">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968d4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968d4-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="968d4-119">See also</span></span>

- [<span data-ttu-id="968d4-120">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="968d4-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="968d4-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="968d4-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="968d4-122">ReJIT：使用說明指南</span><span class="sxs-lookup"><span data-stu-id="968d4-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
