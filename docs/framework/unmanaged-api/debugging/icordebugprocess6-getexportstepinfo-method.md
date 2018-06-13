---
title: ICorDebugProcess6::GetExportStepInfo 方法
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d0758a8603b7c31844b39c9f3beefea04e0a029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422955"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="ff9c8-102">ICorDebugProcess6::GetExportStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="ff9c8-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="ff9c8-103">提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff9c8-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff9c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff9c8-105">Parameters</span></span>  
 <span data-ttu-id="ff9c8-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="ff9c8-106">pszExportName</span></span>  
 <span data-ttu-id="ff9c8-107">[in] 執行階段匯出函式寫入 PE 匯出資料表時所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="ff9c8-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="ff9c8-108">invokeKind</span></span>  
 <span data-ttu-id="ff9c8-109">[out]成員指標[CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)列舉，描述匯出函式如何叫用 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="ff9c8-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="ff9c8-110">invokePurpose</span></span>  
 <span data-ttu-id="ff9c8-111">[out]成員指標[CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)列舉，描述匯出函式呼叫 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff9c8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="ff9c8-112">Return Value</span></span>  
 <span data-ttu-id="ff9c8-113">這個方法會傳回下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="ff9c8-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="ff9c8-114">Return value</span></span>|<span data-ttu-id="ff9c8-115">描述</span><span class="sxs-lookup"><span data-stu-id="ff9c8-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="ff9c8-116">方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="ff9c8-117">`pInvokeKind` 或`pInvokePurpose`是**null**。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="ff9c8-118">其他失敗的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="ff9c8-119">視需要。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff9c8-120">備註</span><span class="sxs-lookup"><span data-stu-id="ff9c8-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff9c8-121">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff9c8-122">需求</span><span class="sxs-lookup"><span data-stu-id="ff9c8-122">Requirements</span></span>  
 <span data-ttu-id="ff9c8-123">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff9c8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff9c8-124">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff9c8-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff9c8-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff9c8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff9c8-126">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff9c8-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9c8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff9c8-127">See Also</span></span>  
 [<span data-ttu-id="ff9c8-128">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="ff9c8-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="ff9c8-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ff9c8-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
