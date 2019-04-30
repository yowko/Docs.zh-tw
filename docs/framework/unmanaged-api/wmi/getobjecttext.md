---
title: GetObjectText 函式 （Unmanaged API 參考）
description: GetObjectText 函式會傳回物件的文字呈現以 MOF 語法。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d34cb399ac0e8780c442eeb2e95cebfd0a22ca02
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040569"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="41a9f-103">GetObjectText 函式</span><span class="sxs-lookup"><span data-stu-id="41a9f-103">GetObjectText function</span></span>
<span data-ttu-id="41a9f-104">在受管理物件格式 (MOF) 語法中傳回之物件的文字呈現。</span><span class="sxs-lookup"><span data-stu-id="41a9f-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="41a9f-105">語法</span><span class="sxs-lookup"><span data-stu-id="41a9f-105">Syntax</span></span>  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="41a9f-106">參數</span><span class="sxs-lookup"><span data-stu-id="41a9f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="41a9f-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="41a9f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="41a9f-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="41a9f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="41a9f-109">[in]通常是 0。</span><span class="sxs-lookup"><span data-stu-id="41a9f-109">[in] Normally 0.</span></span> <span data-ttu-id="41a9f-110">如果`WBEM_FLAG_NO_FLAVORS`（或 0x1） 指定，限定詞會包含不含傳播或類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="41a9f-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="41a9f-111">[out]指標`null`項目。</span><span class="sxs-lookup"><span data-stu-id="41a9f-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="41a9f-112">傳回時，新配置`BSTR`，其中包含物件的 MOF 語法呈現。</span><span class="sxs-lookup"><span data-stu-id="41a9f-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="41a9f-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="41a9f-113">Return value</span></span>

<span data-ttu-id="41a9f-114">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="41a9f-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="41a9f-115">常數</span><span class="sxs-lookup"><span data-stu-id="41a9f-115">Constant</span></span>  |<span data-ttu-id="41a9f-116">值</span><span class="sxs-lookup"><span data-stu-id="41a9f-116">Value</span></span>  |<span data-ttu-id="41a9f-117">描述</span><span class="sxs-lookup"><span data-stu-id="41a9f-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="41a9f-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="41a9f-118">0x80041001</span></span> | <span data-ttu-id="41a9f-119">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="41a9f-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="41a9f-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="41a9f-120">0x80041008</span></span> | <span data-ttu-id="41a9f-121">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="41a9f-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="41a9f-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="41a9f-122">0x80041006</span></span> | <span data-ttu-id="41a9f-123">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="41a9f-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="41a9f-124">0</span><span class="sxs-lookup"><span data-stu-id="41a9f-124">0</span></span> | <span data-ttu-id="41a9f-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="41a9f-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="41a9f-126">備註</span><span class="sxs-lookup"><span data-stu-id="41a9f-126">Remarks</span></span>

<span data-ttu-id="41a9f-127">此函式會包裝在呼叫[IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext)方法。</span><span class="sxs-lookup"><span data-stu-id="41a9f-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="41a9f-128">傳回的 MOF 文字不包含所有物件的資訊，但僅足夠 MOF 編譯器能夠重新建立原始物件的資訊。</span><span class="sxs-lookup"><span data-stu-id="41a9f-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="41a9f-129">比方說，沒有傳播的限定詞或父類別的內容會包含。</span><span class="sxs-lookup"><span data-stu-id="41a9f-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="41a9f-130">若要重新建構方法的參數的文字使用下列演算法：</span><span class="sxs-lookup"><span data-stu-id="41a9f-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="41a9f-131">參數是以它們的識別碼值順序 resequenced。</span><span class="sxs-lookup"><span data-stu-id="41a9f-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="41a9f-132">為指定的參數`[in]`和`[out]`會結合成單一參數。</span><span class="sxs-lookup"><span data-stu-id="41a9f-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="41a9f-133">`pstrObjectText` 必須是指標，`null`時呼叫的函式; 它必須指向是有效的方法呼叫前，因為指標將不會取消配置的字串。</span><span class="sxs-lookup"><span data-stu-id="41a9f-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="41a9f-134">需求</span><span class="sxs-lookup"><span data-stu-id="41a9f-134">Requirements</span></span>  
<span data-ttu-id="41a9f-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41a9f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a9f-136">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="41a9f-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="41a9f-137">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="41a9f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a9f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41a9f-138">See also</span></span>

- [<span data-ttu-id="41a9f-139">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="41a9f-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
