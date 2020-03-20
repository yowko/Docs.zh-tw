---
title: ICorDebugProcess6::GetExportStepInfo 方法
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178523"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="f47c5-102">ICorDebugProcess6::GetExportStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f47c5-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="f47c5-103">提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f47c5-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f47c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f47c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f47c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="f47c5-105">Parameters</span></span>  
 <span data-ttu-id="f47c5-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="f47c5-106">pszExportName</span></span>  
 <span data-ttu-id="f47c5-107">[in] 執行階段匯出函式寫入 PE 匯出資料表時所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="f47c5-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="f47c5-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="f47c5-108">invokeKind</span></span>  
 <span data-ttu-id="f47c5-109">[出]指向[CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md)枚舉成員的指標，用於描述匯出的函數將如何調用託管代碼。</span><span class="sxs-lookup"><span data-stu-id="f47c5-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="f47c5-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="f47c5-110">invokePurpose</span></span>  
 <span data-ttu-id="f47c5-111">[出]指向[CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md)枚舉成員的指標，用於描述匯出函數將調用託管代碼的原因。</span><span class="sxs-lookup"><span data-stu-id="f47c5-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f47c5-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f47c5-112">Return Value</span></span>  
 <span data-ttu-id="f47c5-113">這個方法會傳回下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="f47c5-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="f47c5-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="f47c5-114">Return value</span></span>|<span data-ttu-id="f47c5-115">描述</span><span class="sxs-lookup"><span data-stu-id="f47c5-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="f47c5-116">方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f47c5-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="f47c5-117">`pInvokeKind`或`pInvokePurpose`**為 null**。</span><span class="sxs-lookup"><span data-stu-id="f47c5-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="f47c5-118">其他失敗的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="f47c5-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="f47c5-119">視需要。</span><span class="sxs-lookup"><span data-stu-id="f47c5-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f47c5-120">備註</span><span class="sxs-lookup"><span data-stu-id="f47c5-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f47c5-121">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f47c5-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f47c5-122">需求</span><span class="sxs-lookup"><span data-stu-id="f47c5-122">Requirements</span></span>  
 <span data-ttu-id="f47c5-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f47c5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f47c5-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f47c5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f47c5-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f47c5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f47c5-126">**.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f47c5-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47c5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f47c5-127">See also</span></span>

- [<span data-ttu-id="f47c5-128">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="f47c5-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="f47c5-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f47c5-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
