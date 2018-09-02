---
title: QualifierSet_GetNames 函式 （Unmanaged API 參考）
description: QualifierSet_GetNames 函式會從物件或屬性擷取限定詞的名稱。
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84059c5e5542e13b1d4fc4efcfc4c7f418db391e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452589"
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="4305c-103">QualifierSet_GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="4305c-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="4305c-104">擷取所有的限定詞或目前的物件或屬性提供的特定限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4305c-105">語法</span><span class="sxs-lookup"><span data-stu-id="4305c-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="4305c-106">參數</span><span class="sxs-lookup"><span data-stu-id="4305c-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="4305c-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="4305c-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="4305c-108">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="4305c-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="4305c-109">[in]其中一個下列的旗標或值，指定要包含在列舉中的名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="4305c-110">常數</span><span class="sxs-lookup"><span data-stu-id="4305c-110">Constant</span></span>  |<span data-ttu-id="4305c-111">值</span><span class="sxs-lookup"><span data-stu-id="4305c-111">Value</span></span>  |<span data-ttu-id="4305c-112">描述</span><span class="sxs-lookup"><span data-stu-id="4305c-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="4305c-113">0</span><span class="sxs-lookup"><span data-stu-id="4305c-113">0</span></span> | <span data-ttu-id="4305c-114">傳回所有限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="4305c-115">0x10</span><span class="sxs-lookup"><span data-stu-id="4305c-115">0x10</span></span> | <span data-ttu-id="4305c-116">傳回目前的屬性或物件特定限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="4305c-117">屬性： 返回 （包括覆寫） 的屬性特定的辨識符號，並不是這些限定詞會傳播從類別定義。</span><span class="sxs-lookup"><span data-stu-id="4305c-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="4305c-118">執行個體： 傳回只有特定執行個體的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="4305c-119">類別： 傳回衍生的類別 beiong 特定只限定詞。</span><span class="sxs-lookup"><span data-stu-id="4305c-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="4305c-120">0x20</span><span class="sxs-lookup"><span data-stu-id="4305c-120">0x20</span></span> | <span data-ttu-id="4305c-121">傳回的傳播的限定詞的名稱，從另一個物件。</span><span class="sxs-lookup"><span data-stu-id="4305c-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="4305c-122">屬性： 傳回的限定詞傳播至這個屬性從類別定義中，而不從本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="4305c-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="4305c-123">執行個體： 傳回只有這些限定詞會傳播從類別定義。</span><span class="sxs-lookup"><span data-stu-id="4305c-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="4305c-124">類別： 傳回繼承自父類別的只有這些限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="4305c-125">`pstrNames` [out]新`SAFEARRAY`包含要求的名稱。</span><span class="sxs-lookup"><span data-stu-id="4305c-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="4305c-126">陣列可以有 0 的項目。</span><span class="sxs-lookup"><span data-stu-id="4305c-126">The array can have 0 elements.</span></span> <span data-ttu-id="4305c-127">如果發生錯誤時，新`SAFEARRAY`就不會傳回。</span><span class="sxs-lookup"><span data-stu-id="4305c-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="4305c-128">傳回值</span><span class="sxs-lookup"><span data-stu-id="4305c-128">Return value</span></span>

<span data-ttu-id="4305c-129">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="4305c-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4305c-130">常數</span><span class="sxs-lookup"><span data-stu-id="4305c-130">Constant</span></span>  |<span data-ttu-id="4305c-131">值</span><span class="sxs-lookup"><span data-stu-id="4305c-131">Value</span></span>  |<span data-ttu-id="4305c-132">描述</span><span class="sxs-lookup"><span data-stu-id="4305c-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4305c-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4305c-133">0x80041008</span></span> | <span data-ttu-id="4305c-134">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="4305c-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4305c-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4305c-135">0x80041006</span></span> | <span data-ttu-id="4305c-136">沒有足夠的記憶體可供開始新的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4305c-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4305c-137">0</span><span class="sxs-lookup"><span data-stu-id="4305c-137">0</span></span> | <span data-ttu-id="4305c-138">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4305c-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4305c-139">備註</span><span class="sxs-lookup"><span data-stu-id="4305c-139">Remarks</span></span>

<span data-ttu-id="4305c-140">此函式會包裝在呼叫[IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)方法。</span><span class="sxs-lookup"><span data-stu-id="4305c-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="4305c-141">一旦您已擷取的辨識符號名稱，您可以藉由呼叫依名稱存取每個辨識符號[QualifierSet_Get](qualifierset-get.md)函式。</span><span class="sxs-lookup"><span data-stu-id="4305c-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="4305c-142">它不是發生錯誤，因此擁有零的限定詞，指定物件中的字串數目`pstrNames`在傳回時可能為 0，即使函式會傳回`WBEM_S_NO_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="4305c-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="4305c-143">需求</span><span class="sxs-lookup"><span data-stu-id="4305c-143">Requirements</span></span>  
 <span data-ttu-id="4305c-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4305c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4305c-145">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4305c-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4305c-146">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4305c-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4305c-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4305c-147">See also</span></span>  
[<span data-ttu-id="4305c-148">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="4305c-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
