---
title: "QualifierSet_GetNames 函式 （Unmanaged API 參考）"
description: "QualifierSet_GetNames 函式物件或屬性擷取限定詞的名稱。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b87518bdc1f6ac19eb48991538be5904fdb63f1f
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="75d20-103">QualifierSet_GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="75d20-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="75d20-104">擷取所有的限定詞或都是從目前的物件或屬性的某些限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="75d20-105">語法</span><span class="sxs-lookup"><span data-stu-id="75d20-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="75d20-106">參數</span><span class="sxs-lookup"><span data-stu-id="75d20-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="75d20-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="75d20-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="75d20-108">[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="75d20-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="75d20-109">[in]其中一個的下列旗標或值，指定要包含在列舉中的名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="75d20-110">常數</span><span class="sxs-lookup"><span data-stu-id="75d20-110">Constant</span></span>  |<span data-ttu-id="75d20-111">值</span><span class="sxs-lookup"><span data-stu-id="75d20-111">Value</span></span>  |<span data-ttu-id="75d20-112">描述</span><span class="sxs-lookup"><span data-stu-id="75d20-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="75d20-113">0</span><span class="sxs-lookup"><span data-stu-id="75d20-113">0</span></span> | <span data-ttu-id="75d20-114">傳回所有限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="75d20-115">0x10</span><span class="sxs-lookup"><span data-stu-id="75d20-115">0x10</span></span> | <span data-ttu-id="75d20-116">傳回目前的屬性或物件特定限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="75d20-117">屬性： 返回 （包括覆寫） 的屬性特定辨識符號，並不是這些限定詞傳播從類別定義。</span><span class="sxs-lookup"><span data-stu-id="75d20-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="75d20-118">執行個體： 傳回只可使用特定執行個體的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="75d20-119">類別： 返回衍生的類別 beiong 特定只限定詞。</span><span class="sxs-lookup"><span data-stu-id="75d20-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="75d20-120">0x20</span><span class="sxs-lookup"><span data-stu-id="75d20-120">0x20</span></span> | <span data-ttu-id="75d20-121">傳回的傳播限定詞的名稱，從另一個物件。</span><span class="sxs-lookup"><span data-stu-id="75d20-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="75d20-122">屬性： 傳回僅限定詞傳播給這個屬性從類別定義中，而不從本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="75d20-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="75d20-123">執行個體： 傳回傳播這些辨識符號，從類別定義。</span><span class="sxs-lookup"><span data-stu-id="75d20-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="75d20-124">類別： 傳回繼承自父類別的只有這些限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="75d20-125">`pstrNames`[out]新`SAFEARRAY`包含要求的名稱。</span><span class="sxs-lookup"><span data-stu-id="75d20-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="75d20-126">陣列可以有項目為 0。</span><span class="sxs-lookup"><span data-stu-id="75d20-126">The array can have 0 elements.</span></span> <span data-ttu-id="75d20-127">如果發生錯誤時，新`SAFEARRAY`就不會傳回。</span><span class="sxs-lookup"><span data-stu-id="75d20-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="75d20-128">傳回值</span><span class="sxs-lookup"><span data-stu-id="75d20-128">Return value</span></span>

<span data-ttu-id="75d20-129">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="75d20-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75d20-130">常數</span><span class="sxs-lookup"><span data-stu-id="75d20-130">Constant</span></span>  |<span data-ttu-id="75d20-131">值</span><span class="sxs-lookup"><span data-stu-id="75d20-131">Value</span></span>  |<span data-ttu-id="75d20-132">說明</span><span class="sxs-lookup"><span data-stu-id="75d20-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75d20-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75d20-133">0x80041008</span></span> | <span data-ttu-id="75d20-134">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="75d20-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="75d20-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="75d20-135">0x80041006</span></span> | <span data-ttu-id="75d20-136">使用開始新的列舉型別沒有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="75d20-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="75d20-137">0</span><span class="sxs-lookup"><span data-stu-id="75d20-137">0</span></span> | <span data-ttu-id="75d20-138">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="75d20-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="75d20-139">備註</span><span class="sxs-lookup"><span data-stu-id="75d20-139">Remarks</span></span>

<span data-ttu-id="75d20-140">此函式會包裝呼叫[IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="75d20-140">This function wraps a call to the [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="75d20-141">一旦您已擷取的限定詞的名稱，您可以藉由呼叫依照名稱存取每個限定詞[QualifierSet_Get](qualifierset-get.md)函式。</span><span class="sxs-lookup"><span data-stu-id="75d20-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="75d20-142">不是給定的物件，因此有零個限定詞，針對錯誤中的字串數目`pstrNames`傳回可以是 0，即使此函數會傳回`WBEM_S_NO_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="75d20-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="75d20-143">需求</span><span class="sxs-lookup"><span data-stu-id="75d20-143">Requirements</span></span>  
 <span data-ttu-id="75d20-144">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75d20-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75d20-145">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75d20-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="75d20-146">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75d20-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d20-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="75d20-147">See also</span></span>  
[<span data-ttu-id="75d20-148">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="75d20-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
