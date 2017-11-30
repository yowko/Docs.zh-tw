---
title: "GetObjectText 函式 （Unmanaged API 參考）"
description: "GetObjectText 函式會傳回物件的文字呈現以 MOF 語法。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 27e25a7ab7131f5b1c995c9367de6fe5a6fae592
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="getobjecttext-function"></a><span data-ttu-id="ae4ca-103">GetObjectText 函式</span><span class="sxs-lookup"><span data-stu-id="ae4ca-103">GetObjectText function</span></span>
<span data-ttu-id="ae4ca-104">傳回物件的文字呈現在受管理物件格式 (MOF) 語法。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ae4ca-105">語法</span><span class="sxs-lookup"><span data-stu-id="ae4ca-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="ae4ca-106">參數</span><span class="sxs-lookup"><span data-stu-id="ae4ca-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ae4ca-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ae4ca-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="ae4ca-109">[in]通常是 0。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-109">[in] Normally 0.</span></span> <span data-ttu-id="ae4ca-110">如果`WBEM_FLAG_NO_FLAVORS`（或 0x1） 指定，限定詞會包含不含傳播或類別資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="ae4ca-111">[out]指標`null`項目。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="ae4ca-112">傳回時，新配置`BSTR`，其中包含物件的 MOF 語法呈現。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="ae4ca-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae4ca-113">Return value</span></span>

<span data-ttu-id="ae4ca-114">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="ae4ca-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ae4ca-115">常數</span><span class="sxs-lookup"><span data-stu-id="ae4ca-115">Constant</span></span>  |<span data-ttu-id="ae4ca-116">值</span><span class="sxs-lookup"><span data-stu-id="ae4ca-116">Value</span></span>  |<span data-ttu-id="ae4ca-117">說明</span><span class="sxs-lookup"><span data-stu-id="ae4ca-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ae4ca-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ae4ca-118">0x80041001</span></span> | <span data-ttu-id="ae4ca-119">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ae4ca-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ae4ca-120">0x80041008</span></span> | <span data-ttu-id="ae4ca-121">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ae4ca-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ae4ca-122">0x80041006</span></span> | <span data-ttu-id="ae4ca-123">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ae4ca-124">0</span><span class="sxs-lookup"><span data-stu-id="ae4ca-124">0</span></span> | <span data-ttu-id="ae4ca-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ae4ca-126">備註</span><span class="sxs-lookup"><span data-stu-id="ae4ca-126">Remarks</span></span>

<span data-ttu-id="ae4ca-127">此函式會包裝呼叫[IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-127">This function wraps a call to the [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="ae4ca-128">傳回的 MOF 文字不包含所有物件的相關資訊，但若要能夠重新建立原始物件的 MOF 編譯器足夠資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="ae4ca-129">比方說，沒有傳播的限定詞或父類別的內容會包含。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="ae4ca-130">下列演算法來重新建構方法的參數的文字：</span><span class="sxs-lookup"><span data-stu-id="ae4ca-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="ae4ca-131">參數會以其識別項值順序 resequenced。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="ae4ca-132">參數指定為`[in]`和`[out]`會結合成單一參數。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="ae4ca-133">`pstrObjectText`必須是指向`null`時呼叫的函式; 它必須指向在方法呼叫之前，因為無效的指標將不會重新配置的字串。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae4ca-134">需求</span><span class="sxs-lookup"><span data-stu-id="ae4ca-134">Requirements</span></span>  
<span data-ttu-id="ae4ca-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae4ca-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae4ca-136">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ae4ca-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ae4ca-137">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ae4ca-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4ca-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae4ca-138">See also</span></span>  
[<span data-ttu-id="ae4ca-139">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="ae4ca-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
