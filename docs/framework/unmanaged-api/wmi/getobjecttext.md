---
title: 獲取物件文本功能（非託管 API 引用）
description: GetObjectText 函數在 MOF 語法中返回物件的文本呈現。
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176782"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="fd94f-103">GetObjectText 函式</span><span class="sxs-lookup"><span data-stu-id="fd94f-103">GetObjectText function</span></span>
<span data-ttu-id="fd94f-104">在管理物件格式 （MOF） 語法中返回物件的文本呈現。</span><span class="sxs-lookup"><span data-stu-id="fd94f-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fd94f-105">語法</span><span class="sxs-lookup"><span data-stu-id="fd94f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a><span data-ttu-id="fd94f-106">參數</span><span class="sxs-lookup"><span data-stu-id="fd94f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fd94f-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="fd94f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fd94f-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="fd94f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="fd94f-109">[在]通常為 0。</span><span class="sxs-lookup"><span data-stu-id="fd94f-109">[in] Normally 0.</span></span> <span data-ttu-id="fd94f-110">如果`WBEM_FLAG_NO_FLAVORS`指定 （或 0x1），則包含限定詞而不包含傳播或風味資訊。</span><span class="sxs-lookup"><span data-stu-id="fd94f-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

<span data-ttu-id="fd94f-111">`pstrObjectText`[出]指向上條目的`null`指標。</span><span class="sxs-lookup"><span data-stu-id="fd94f-111">`pstrObjectText` [out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="fd94f-112">返回時，包含物件的`BSTR`MOF 語法呈現的新分配。</span><span class="sxs-lookup"><span data-stu-id="fd94f-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="fd94f-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd94f-113">Return value</span></span>

<span data-ttu-id="fd94f-114">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="fd94f-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fd94f-115">持續性</span><span class="sxs-lookup"><span data-stu-id="fd94f-115">Constant</span></span>  |<span data-ttu-id="fd94f-116">值</span><span class="sxs-lookup"><span data-stu-id="fd94f-116">Value</span></span>  |<span data-ttu-id="fd94f-117">描述</span><span class="sxs-lookup"><span data-stu-id="fd94f-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="fd94f-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="fd94f-118">0x80041001</span></span> | <span data-ttu-id="fd94f-119">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="fd94f-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fd94f-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fd94f-120">0x80041008</span></span> | <span data-ttu-id="fd94f-121">參數無效。</span><span class="sxs-lookup"><span data-stu-id="fd94f-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="fd94f-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="fd94f-122">0x80041006</span></span> | <span data-ttu-id="fd94f-123">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="fd94f-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fd94f-124">0</span><span class="sxs-lookup"><span data-stu-id="fd94f-124">0</span></span> | <span data-ttu-id="fd94f-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fd94f-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fd94f-126">備註</span><span class="sxs-lookup"><span data-stu-id="fd94f-126">Remarks</span></span>

<span data-ttu-id="fd94f-127">此函數將調用包起來到[IWbem ClassObject：：getObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)方法。</span><span class="sxs-lookup"><span data-stu-id="fd94f-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="fd94f-128">返回的 MOF 文本不包含有關物件的所有資訊，但僅包含足夠的資訊，以便 MOF 編譯器能夠重新創建原始物件。</span><span class="sxs-lookup"><span data-stu-id="fd94f-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="fd94f-129">例如，不包含傳播的限定詞或父類屬性。</span><span class="sxs-lookup"><span data-stu-id="fd94f-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="fd94f-130">以下演算法用於重建方法參數的文本：</span><span class="sxs-lookup"><span data-stu-id="fd94f-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="fd94f-131">參數按其識別碼值的順序重新排序。</span><span class="sxs-lookup"><span data-stu-id="fd94f-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="fd94f-132">指定為`[in]`並`[out]`組合到單個參數的參數。</span><span class="sxs-lookup"><span data-stu-id="fd94f-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>

<span data-ttu-id="fd94f-133">`pstrObjectText`調用函數時必須指向`null`的 指標;它不得指向方法調用之前有效的字串，因為指標不會被處理。</span><span class="sxs-lookup"><span data-stu-id="fd94f-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd94f-134">需求</span><span class="sxs-lookup"><span data-stu-id="fd94f-134">Requirements</span></span>  
<span data-ttu-id="fd94f-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd94f-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd94f-136">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fd94f-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fd94f-137">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fd94f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd94f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd94f-138">See also</span></span>

- [<span data-ttu-id="fd94f-139">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="fd94f-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
