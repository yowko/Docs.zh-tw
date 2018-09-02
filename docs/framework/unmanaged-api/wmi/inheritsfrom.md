---
title: InheritsFrom 函式 （Unmanaged API 參考）
description: InheritsFrom 函式會判斷類別或執行個體是否衍生自特定的父類別。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4784e22d5a3eec031fbee00441958a62d66b52df
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452909"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="efd5b-103">InheritsFrom 函式</span><span class="sxs-lookup"><span data-stu-id="efd5b-103">InheritsFrom function</span></span>
<span data-ttu-id="efd5b-104">判斷目前的類別或執行個體是否衍生自指定的父類別。</span><span class="sxs-lookup"><span data-stu-id="efd5b-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="efd5b-105">語法</span><span class="sxs-lookup"><span data-stu-id="efd5b-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="efd5b-106">參數</span><span class="sxs-lookup"><span data-stu-id="efd5b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="efd5b-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="efd5b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="efd5b-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="efd5b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="efd5b-109">[in]類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="efd5b-109">[in] The name of the class.</span></span> <span data-ttu-id="efd5b-110">`wszAncestor` 必須指向有效`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="efd5b-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="efd5b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="efd5b-111">Return value</span></span>

<span data-ttu-id="efd5b-112">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="efd5b-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="efd5b-113">常數</span><span class="sxs-lookup"><span data-stu-id="efd5b-113">Constant</span></span>  |<span data-ttu-id="efd5b-114">值</span><span class="sxs-lookup"><span data-stu-id="efd5b-114">Value</span></span>  |<span data-ttu-id="efd5b-115">描述</span><span class="sxs-lookup"><span data-stu-id="efd5b-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="efd5b-116">0</span><span class="sxs-lookup"><span data-stu-id="efd5b-116">0</span></span> | <span data-ttu-id="efd5b-117">目前的物件繼承自`wszAncestor`。</span><span class="sxs-lookup"><span data-stu-id="efd5b-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="efd5b-118">1</span><span class="sxs-lookup"><span data-stu-id="efd5b-118">1</span></span> | <span data-ttu-id="efd5b-119">目前的物件不是繼承自`wszAncestor`。</span><span class="sxs-lookup"><span data-stu-id="efd5b-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="efd5b-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="efd5b-120">0x80041008</span></span> | <span data-ttu-id="efd5b-121">`wszAncestor` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="efd5b-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="efd5b-122">備註</span><span class="sxs-lookup"><span data-stu-id="efd5b-122">Remarks</span></span>

<span data-ttu-id="efd5b-123">此函式會包裝在呼叫[IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)方法。</span><span class="sxs-lookup"><span data-stu-id="efd5b-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="efd5b-124">需求</span><span class="sxs-lookup"><span data-stu-id="efd5b-124">Requirements</span></span>  
 <span data-ttu-id="efd5b-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efd5b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd5b-126">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="efd5b-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="efd5b-127">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="efd5b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd5b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efd5b-128">See also</span></span>  
[<span data-ttu-id="efd5b-129">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="efd5b-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
