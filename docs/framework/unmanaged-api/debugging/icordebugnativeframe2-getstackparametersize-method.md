---
title: ICorDebugNativeFrame2::GetStackParameterSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: ca742ba9e89e1d189cfa38dead314df0d8b4e9d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792768"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="54502-102">ICorDebugNativeFrame2::GetStackParameterSize 方法</span><span class="sxs-lookup"><span data-stu-id="54502-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="54502-103">傳回 x86 作業系統上堆疊上的參數累計大小。</span><span class="sxs-lookup"><span data-stu-id="54502-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54502-104">語法</span><span class="sxs-lookup"><span data-stu-id="54502-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="54502-105">參數</span><span class="sxs-lookup"><span data-stu-id="54502-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="54502-106">脫銷堆疊上參數之累計大小的指標。</span><span class="sxs-lookup"><span data-stu-id="54502-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54502-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="54502-107">Return Value</span></span>  
 <span data-ttu-id="54502-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="54502-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="54502-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54502-109">HRESULT</span></span>|<span data-ttu-id="54502-110">描述</span><span class="sxs-lookup"><span data-stu-id="54502-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54502-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="54502-111">S_OK</span></span>|<span data-ttu-id="54502-112">已成功傳回堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="54502-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="54502-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="54502-113">S_FALSE</span></span>|<span data-ttu-id="54502-114">在非 x86 平臺上呼叫 `GetStackParameterSize`。</span><span class="sxs-lookup"><span data-stu-id="54502-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="54502-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54502-115">E_FAIL</span></span>|<span data-ttu-id="54502-116">`The size of the parameters could not be returned`。</span><span class="sxs-lookup"><span data-stu-id="54502-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="54502-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="54502-117">E_INVALIDARG</span></span>|<span data-ttu-id="54502-118">`null``pSize`。</span><span class="sxs-lookup"><span data-stu-id="54502-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="54502-119">例外狀況</span><span class="sxs-lookup"><span data-stu-id="54502-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54502-120">備註</span><span class="sxs-lookup"><span data-stu-id="54502-120">Remarks</span></span>  
 <span data-ttu-id="54502-121">[ICorDebugStackWalk](icordebugstackwalk-interface.md)方法不會調整堆疊上推送之參數的堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="54502-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="54502-122">相反地，您可以使用 `GetStackParameterSize` 所傳回的值來調整堆疊指標以植入原生回溯器，這會針對參數進行調整。</span><span class="sxs-lookup"><span data-stu-id="54502-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54502-123">需求</span><span class="sxs-lookup"><span data-stu-id="54502-123">Requirements</span></span>  
 <span data-ttu-id="54502-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54502-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54502-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54502-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54502-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54502-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54502-127">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54502-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54502-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="54502-128">See also</span></span>

- [<span data-ttu-id="54502-129">ICorDebugNativeFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="54502-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="54502-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="54502-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="54502-131">偵錯</span><span class="sxs-lookup"><span data-stu-id="54502-131">Debugging</span></span>](index.md)
