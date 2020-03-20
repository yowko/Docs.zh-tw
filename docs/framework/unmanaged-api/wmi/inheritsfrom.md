---
title: 繼承來自函數（非託管 API 引用）
description: 繼承 From 函數確定類或實例是否派生自特定的父類。
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174936"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="3a187-103">InheritsFrom 函式</span><span class="sxs-lookup"><span data-stu-id="3a187-103">InheritsFrom function</span></span>
<span data-ttu-id="3a187-104">判斷目前類別或執行個體衍生自指定的父類別。</span><span class="sxs-lookup"><span data-stu-id="3a187-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3a187-105">語法</span><span class="sxs-lookup"><span data-stu-id="3a187-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="3a187-106">參數</span><span class="sxs-lookup"><span data-stu-id="3a187-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3a187-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="3a187-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3a187-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="3a187-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="3a187-109">[在]類的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a187-109">[in] The name of the class.</span></span> <span data-ttu-id="3a187-110">`wszAncestor`必須指向有效的`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="3a187-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="3a187-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a187-111">Return value</span></span>

<span data-ttu-id="3a187-112">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="3a187-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3a187-113">持續性</span><span class="sxs-lookup"><span data-stu-id="3a187-113">Constant</span></span>  |<span data-ttu-id="3a187-114">值</span><span class="sxs-lookup"><span data-stu-id="3a187-114">Value</span></span>  |<span data-ttu-id="3a187-115">描述</span><span class="sxs-lookup"><span data-stu-id="3a187-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="3a187-116">0</span><span class="sxs-lookup"><span data-stu-id="3a187-116">0</span></span> | <span data-ttu-id="3a187-117">當前物件從`wszAncestor`繼承。</span><span class="sxs-lookup"><span data-stu-id="3a187-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="3a187-118">1</span><span class="sxs-lookup"><span data-stu-id="3a187-118">1</span></span> | <span data-ttu-id="3a187-119">當前物件不從`wszAncestor`繼承。</span><span class="sxs-lookup"><span data-stu-id="3a187-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3a187-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3a187-120">0x80041008</span></span> | <span data-ttu-id="3a187-121">`wszAncestor` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="3a187-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="3a187-122">備註</span><span class="sxs-lookup"><span data-stu-id="3a187-122">Remarks</span></span>

<span data-ttu-id="3a187-123">此函數包裝對[IWbem ClassObject 的調用：：繼承方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)。</span><span class="sxs-lookup"><span data-stu-id="3a187-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a187-124">需求</span><span class="sxs-lookup"><span data-stu-id="3a187-124">Requirements</span></span>  
 <span data-ttu-id="3a187-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a187-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a187-126">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3a187-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3a187-127">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3a187-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a187-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a187-128">See also</span></span>

- [<span data-ttu-id="3a187-129">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="3a187-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
