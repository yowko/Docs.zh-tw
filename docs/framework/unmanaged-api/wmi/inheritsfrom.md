---
title: 'InheritsFrom 函式 (非受控 API 參考) '
description: InheritsFrom 函式會判斷類別或實例是否衍生自特定的父類別。
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
ms.openlocfilehash: 3cfe3388dc808335e6d3daaf7ec949108e95f52e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726784"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="91295-103">InheritsFrom 函式</span><span class="sxs-lookup"><span data-stu-id="91295-103">InheritsFrom function</span></span>

<span data-ttu-id="91295-104">判斷目前類別或執行個體衍生自指定的父類別。</span><span class="sxs-lookup"><span data-stu-id="91295-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="91295-105">語法</span><span class="sxs-lookup"><span data-stu-id="91295-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="91295-106">參數</span><span class="sxs-lookup"><span data-stu-id="91295-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="91295-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="91295-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="91295-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="91295-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="91295-109">在類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="91295-109">[in] The name of the class.</span></span> <span data-ttu-id="91295-110">`wszAncestor` 必須指向有效的 `LPCWSTR` 。</span><span class="sxs-lookup"><span data-stu-id="91295-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="91295-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="91295-111">Return value</span></span>

<span data-ttu-id="91295-112">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="91295-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="91295-113">常數</span><span class="sxs-lookup"><span data-stu-id="91295-113">Constant</span></span>  |<span data-ttu-id="91295-114">值</span><span class="sxs-lookup"><span data-stu-id="91295-114">Value</span></span>  |<span data-ttu-id="91295-115">描述</span><span class="sxs-lookup"><span data-stu-id="91295-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="91295-116">0</span><span class="sxs-lookup"><span data-stu-id="91295-116">0</span></span> | <span data-ttu-id="91295-117">目前的物件繼承自 `wszAncestor` 。</span><span class="sxs-lookup"><span data-stu-id="91295-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="91295-118">1</span><span class="sxs-lookup"><span data-stu-id="91295-118">1</span></span> | <span data-ttu-id="91295-119">目前的物件不是繼承自 `wszAncestor` 。</span><span class="sxs-lookup"><span data-stu-id="91295-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="91295-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="91295-120">0x80041008</span></span> | <span data-ttu-id="91295-121">`wszAncestor` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="91295-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="91295-122">備註</span><span class="sxs-lookup"><span data-stu-id="91295-122">Remarks</span></span>

<span data-ttu-id="91295-123">此函數會包裝對 [IWbemClassObject：： InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="91295-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="91295-124">需求</span><span class="sxs-lookup"><span data-stu-id="91295-124">Requirements</span></span>  

 <span data-ttu-id="91295-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91295-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91295-126">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="91295-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="91295-127">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91295-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91295-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91295-128">See also</span></span>

- [<span data-ttu-id="91295-129">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="91295-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
