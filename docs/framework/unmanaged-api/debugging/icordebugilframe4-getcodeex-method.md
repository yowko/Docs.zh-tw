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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d61981d26d21ec1e5e24093817586ebf45b129e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162328"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="d9863-102">ICorDebugILFrame4::GetCodeEx 方法</span><span class="sxs-lookup"><span data-stu-id="d9863-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="d9863-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="d9863-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d9863-104">取得此堆疊框架執行之程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="d9863-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9863-105">語法</span><span class="sxs-lookup"><span data-stu-id="d9863-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9863-106">參數</span><span class="sxs-lookup"><span data-stu-id="d9863-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="d9863-107">[in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)列舉的成員，指定是否要將分析工具的 ReJIT 要求所定義的中繼語言 (IL) 包含在框架中。</span><span class="sxs-lookup"><span data-stu-id="d9863-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="d9863-108">[out]「 ICorDebugCode 」 物件，代表這個堆疊框架正在執行的程式碼的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d9863-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9863-109">備註</span><span class="sxs-lookup"><span data-stu-id="d9863-109">Remarks</span></span>  
 <span data-ttu-id="d9863-110">這個方法很類似[icordebugframe:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)方法，但是它會選擇性地存取分析工具的 ReJIT 要求所定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d9863-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="d9863-111">呼叫此方法時`flags`的值`ILCODE_ORIGINAL_IL`相當於呼叫[GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); 如果已檢測的方法，將無法存取其 IL。</span><span class="sxs-lookup"><span data-stu-id="d9863-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> `ILCODE_REJIT_IL` <span data-ttu-id="d9863-112">可讓偵錯工具存取分析工具的 ReJIT 要求所定義的 IL。</span><span class="sxs-lookup"><span data-stu-id="d9863-112">allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="d9863-113">如果未檢測 IL，`ppCode`已**null**，且此方法傳回`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="d9863-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9863-114">需求</span><span class="sxs-lookup"><span data-stu-id="d9863-114">Requirements</span></span>  
 <span data-ttu-id="d9863-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9863-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9863-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9863-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9863-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9863-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d9863-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d9863-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9863-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9863-119">See also</span></span>

- [<span data-ttu-id="d9863-120">ICorDebugILFrame4 介面</span><span class="sxs-lookup"><span data-stu-id="d9863-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="d9863-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d9863-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d9863-122">ReJIT:操作說明指南</span><span class="sxs-lookup"><span data-stu-id="d9863-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
