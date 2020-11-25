---
title: 'GetObjectText 函式 (非受控 API 參考) '
description: GetObjectText 函式會以 MOF 語法傳回物件的文字呈現。
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
ms.openlocfilehash: 6ad2b29202222d594cc7976a13929002164314a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718367"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="0f7c9-103">GetObjectText 函式</span><span class="sxs-lookup"><span data-stu-id="0f7c9-103">GetObjectText function</span></span>

<span data-ttu-id="0f7c9-104">以受控物件格式 (MOF) 語法傳回物件的文字呈現。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0f7c9-105">語法</span><span class="sxs-lookup"><span data-stu-id="0f7c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a><span data-ttu-id="0f7c9-106">參數</span><span class="sxs-lookup"><span data-stu-id="0f7c9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0f7c9-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0f7c9-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="0f7c9-109">在通常是0。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-109">[in] Normally 0.</span></span> <span data-ttu-id="0f7c9-110">如果 `WBEM_FLAG_NO_FLAVORS` 指定了 (或 0x1) ，則不會包含任何傳播或類別資訊的限定詞。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

<span data-ttu-id="0f7c9-111">`pstrObjectText` 擴展On 專案的指標 `null` 。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-111">`pstrObjectText` [out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="0f7c9-112">傳回時，為新配置 `BSTR` 的，包含物件的 MOF 語法轉譯。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="0f7c9-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="0f7c9-113">Return value</span></span>

<span data-ttu-id="0f7c9-114">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="0f7c9-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0f7c9-115">常數</span><span class="sxs-lookup"><span data-stu-id="0f7c9-115">Constant</span></span>  |<span data-ttu-id="0f7c9-116">值</span><span class="sxs-lookup"><span data-stu-id="0f7c9-116">Value</span></span>  |<span data-ttu-id="0f7c9-117">描述</span><span class="sxs-lookup"><span data-stu-id="0f7c9-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="0f7c9-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0f7c9-118">0x80041001</span></span> | <span data-ttu-id="0f7c9-119">一般失敗。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0f7c9-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0f7c9-120">0x80041008</span></span> | <span data-ttu-id="0f7c9-121">參數無效。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0f7c9-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0f7c9-122">0x80041006</span></span> | <span data-ttu-id="0f7c9-123">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0f7c9-124">0</span><span class="sxs-lookup"><span data-stu-id="0f7c9-124">0</span></span> | <span data-ttu-id="0f7c9-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0f7c9-126">備註</span><span class="sxs-lookup"><span data-stu-id="0f7c9-126">Remarks</span></span>

<span data-ttu-id="0f7c9-127">此函數會包裝對 [IWbemClassObject：： GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="0f7c9-128">傳回的 MOF 文字未包含物件的所有相關資訊，但只有足夠的資訊可讓 MOF 編譯器能夠重新建立原始物件。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="0f7c9-129">例如，不包含任何傳播的限定詞或父類別屬性。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="0f7c9-130">下列演算法用來重建方法參數的文字：</span><span class="sxs-lookup"><span data-stu-id="0f7c9-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="0f7c9-131">參數的 resequenced 順序為其識別碼值。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="0f7c9-132">以和指定的參數 `[in]` `[out]` 會結合為單一參數。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>

<span data-ttu-id="0f7c9-133">`pstrObjectText` 當呼叫函式時，必須是指向的指標 `null` ; 因為指標不會解除配置，所以它不能指向方法呼叫之前的有效字串。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f7c9-134">需求</span><span class="sxs-lookup"><span data-stu-id="0f7c9-134">Requirements</span></span>  

<span data-ttu-id="0f7c9-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f7c9-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f7c9-136">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="0f7c9-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0f7c9-137">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0f7c9-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f7c9-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f7c9-138">See also</span></span>

- [<span data-ttu-id="0f7c9-139">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="0f7c9-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
