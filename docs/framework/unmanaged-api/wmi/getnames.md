---
title: GetNames 函式（非受控 API 參考）
description: GetNames 函數會抓取物件屬性的名稱。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 748767596a8f4680a2d7b63cb0579acaed5f53f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798521"
---
# <a name="getnames-function"></a><span data-ttu-id="3a32e-103">GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="3a32e-103">GetNames function</span></span>
<span data-ttu-id="3a32e-104">擷取物件屬性的子集合或所有名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3a32e-105">語法</span><span class="sxs-lookup"><span data-stu-id="3a32e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="3a32e-106">參數</span><span class="sxs-lookup"><span data-stu-id="3a32e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3a32e-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="3a32e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3a32e-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="3a32e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="3a32e-109">在有效`LPCWSTR`的指標，指定做為篩選準則一部分運作的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="3a32e-110">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="3a32e-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="3a32e-111">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="3a32e-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="3a32e-112">在位欄位的組合。</span><span class="sxs-lookup"><span data-stu-id="3a32e-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="3a32e-113">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="3a32e-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="3a32e-114">在已初始化為篩選值`VARIANT`之有效結構的指標。</span><span class="sxs-lookup"><span data-stu-id="3a32e-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="3a32e-115">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="3a32e-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="3a32e-116">脫銷包含屬性名稱的結構。`SAFEARRAY`</span><span class="sxs-lookup"><span data-stu-id="3a32e-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="3a32e-117">在輸入時，這個參數必須一律為的指標`null`。</span><span class="sxs-lookup"><span data-stu-id="3a32e-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="3a32e-118">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="3a32e-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="3a32e-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a32e-119">Return value</span></span>

<span data-ttu-id="3a32e-120">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="3a32e-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3a32e-121">常數</span><span class="sxs-lookup"><span data-stu-id="3a32e-121">Constant</span></span>  |<span data-ttu-id="3a32e-122">值</span><span class="sxs-lookup"><span data-stu-id="3a32e-122">Value</span></span>  |<span data-ttu-id="3a32e-123">說明</span><span class="sxs-lookup"><span data-stu-id="3a32e-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3a32e-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3a32e-124">0x80041001</span></span> | <span data-ttu-id="3a32e-125">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="3a32e-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3a32e-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3a32e-126">0x80041008</span></span> | <span data-ttu-id="3a32e-127">一或多個參數無效，或指定了不正確的旗標和參數組合。</span><span class="sxs-lookup"><span data-stu-id="3a32e-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3a32e-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3a32e-128">0x80041006</span></span> | <span data-ttu-id="3a32e-129">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="3a32e-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3a32e-130">0</span><span class="sxs-lookup"><span data-stu-id="3a32e-130">0</span></span> | <span data-ttu-id="3a32e-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3a32e-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3a32e-132">備註</span><span class="sxs-lookup"><span data-stu-id="3a32e-132">Remarks</span></span>

<span data-ttu-id="3a32e-133">此函式會包裝對[IWbemClassObject：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3a32e-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="3a32e-134">已命名的傳回是由旗標和參數的組合所控制。</span><span class="sxs-lookup"><span data-stu-id="3a32e-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="3a32e-135">例如，函式可以傳回所有屬性的名稱，或只傳回索引鍵屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="3a32e-136">主要篩選準則是在`lFlags`參數中指定，而其他參數則會根據它而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3a32e-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="3a32e-137">中`lFlags`的旗標值為位欄位</span><span class="sxs-lookup"><span data-stu-id="3a32e-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="3a32e-138">可當做`lEnumFlags`引數傳遞的旗標是在*WbemCli*標頭檔中定義的位欄位，或者您可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="3a32e-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="3a32e-139">您可以將每個群組中的一個旗標與任何其他群組中的任何旗標結合。</span><span class="sxs-lookup"><span data-stu-id="3a32e-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="3a32e-140">不過，來自相同群組的旗標是互斥的。</span><span class="sxs-lookup"><span data-stu-id="3a32e-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="3a32e-141">群組1旗標</span><span class="sxs-lookup"><span data-stu-id="3a32e-141">Group 1 flags</span></span> |<span data-ttu-id="3a32e-142">值</span><span class="sxs-lookup"><span data-stu-id="3a32e-142">Value</span></span>  |<span data-ttu-id="3a32e-143">描述</span><span class="sxs-lookup"><span data-stu-id="3a32e-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="3a32e-144">0</span><span class="sxs-lookup"><span data-stu-id="3a32e-144">0</span></span> | <span data-ttu-id="3a32e-145">傳回所有屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-145">Return all property names.</span></span> <span data-ttu-id="3a32e-146">`strQualifierName`和`pQualifierVal`未使用。</span><span class="sxs-lookup"><span data-stu-id="3a32e-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="3a32e-147">1</span><span class="sxs-lookup"><span data-stu-id="3a32e-147">1</span></span> | <span data-ttu-id="3a32e-148">只傳回具有`strQualifierName`參數所指定名稱之限定詞的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a32e-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="3a32e-149">如果使用此旗標，您必須指定`strQualifierName`。</span><span class="sxs-lookup"><span data-stu-id="3a32e-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="3a32e-150">2</span><span class="sxs-lookup"><span data-stu-id="3a32e-150">2</span></span> |  <span data-ttu-id="3a32e-151">只傳回沒有`strQualifierName`參數所指定名稱之限定詞的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a32e-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="3a32e-152">如果使用此旗標，您必須指定`strQualifierName`。</span><span class="sxs-lookup"><span data-stu-id="3a32e-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="3a32e-153">3</span><span class="sxs-lookup"><span data-stu-id="3a32e-153">3</span></span> | <span data-ttu-id="3a32e-154">只傳回具有`wszQualifierName`參數所指定名稱之限定詞的屬性，而且其值與結構所`pQualifierVal`指定的值相同。</span><span class="sxs-lookup"><span data-stu-id="3a32e-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="3a32e-155">如果使用這個旗標，您必須同時`wszQualifierName`指定`pQualifierValue`和。</span><span class="sxs-lookup"><span data-stu-id="3a32e-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="3a32e-156">群組2旗標</span><span class="sxs-lookup"><span data-stu-id="3a32e-156">Group 2 flags</span></span> |<span data-ttu-id="3a32e-157">值</span><span class="sxs-lookup"><span data-stu-id="3a32e-157">Value</span></span>  |<span data-ttu-id="3a32e-158">描述</span><span class="sxs-lookup"><span data-stu-id="3a32e-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="3a32e-159">0x4</span><span class="sxs-lookup"><span data-stu-id="3a32e-159">0x4</span></span> | <span data-ttu-id="3a32e-160">只傳回定義索引鍵的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="3a32e-161">0x8</span><span class="sxs-lookup"><span data-stu-id="3a32e-161">0x8</span></span> | <span data-ttu-id="3a32e-162">只傳回物件參考的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="3a32e-163">群組3旗標</span><span class="sxs-lookup"><span data-stu-id="3a32e-163">Group 3 flags</span></span> |<span data-ttu-id="3a32e-164">值</span><span class="sxs-lookup"><span data-stu-id="3a32e-164">Value</span></span>  |<span data-ttu-id="3a32e-165">描述</span><span class="sxs-lookup"><span data-stu-id="3a32e-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3a32e-166">0x10</span><span class="sxs-lookup"><span data-stu-id="3a32e-166">0x10</span></span> | <span data-ttu-id="3a32e-167">只傳回屬於最衍生類別的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="3a32e-168">從父類別中排除屬性。</span><span class="sxs-lookup"><span data-stu-id="3a32e-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="3a32e-169">0x20</span><span class="sxs-lookup"><span data-stu-id="3a32e-169">0x20</span></span> | <span data-ttu-id="3a32e-170">只傳回屬於父類別的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="3a32e-171">0x30</span><span class="sxs-lookup"><span data-stu-id="3a32e-171">0x30</span></span> | <span data-ttu-id="3a32e-172">只傳回系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="3a32e-173">0x40</span><span class="sxs-lookup"><span data-stu-id="3a32e-173">0x40</span></span> | <span data-ttu-id="3a32e-174">只傳回非系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a32e-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="3a32e-175">函式一律會配置新`SAFEARRAY`的`WBEM_S_NO_ERROR`（如果它傳回`pstrNames` ），而且一律會設定為指向它。</span><span class="sxs-lookup"><span data-stu-id="3a32e-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="3a32e-176">如果沒有屬性符合指定的篩選準則，則傳回的陣列可以有0個元素。</span><span class="sxs-lookup"><span data-stu-id="3a32e-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="3a32e-177">如果函數傳回的值`WBM_S_NO_ERROR`不是，則不會傳回新`SAFEARRAY`的結構。</span><span class="sxs-lookup"><span data-stu-id="3a32e-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="3a32e-178">需求</span><span class="sxs-lookup"><span data-stu-id="3a32e-178">Requirements</span></span>  
 <span data-ttu-id="3a32e-179">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a32e-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a32e-180">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3a32e-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3a32e-181">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3a32e-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a32e-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a32e-182">See also</span></span>

- [<span data-ttu-id="3a32e-183">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="3a32e-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
