---
title: 'GetNames 函式 (非受控 API 參考) '
description: GetNames 函式會抓取物件的屬性名稱。
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
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687654"
---
# <a name="getnames-function"></a><span data-ttu-id="f5b8d-103">GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="f5b8d-103">GetNames function</span></span>

<span data-ttu-id="f5b8d-104">擷取物件屬性的子集合或所有名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f5b8d-105">語法</span><span class="sxs-lookup"><span data-stu-id="f5b8d-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="f5b8d-106">參數</span><span class="sxs-lookup"><span data-stu-id="f5b8d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f5b8d-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f5b8d-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="f5b8d-109">在有效的指標， `LPCWSTR` 指定做為篩選準則一部分運作的辨識符號名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="f5b8d-110">如需詳細資訊，請參閱「 [備註](#remarks) 」一節。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="f5b8d-111">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="f5b8d-112">在位欄位的組合。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="f5b8d-113">如需詳細資訊，請參閱「 [備註](#remarks) 」一節。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="f5b8d-114">`pQualifierValue` 在有效結構的指標，此 `VARIANT` 結構會初始化為篩選值。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="f5b8d-115">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="f5b8d-116">擴展 `SAFEARRAY` 包含屬性名稱的結構。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="f5b8d-117">在輸入時，這個參數必須一律為的指標 `null` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="f5b8d-118">如需詳細資訊，請參閱「 [備註](#remarks) 」一節。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5b8d-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="f5b8d-119">Return value</span></span>

<span data-ttu-id="f5b8d-120">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f5b8d-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f5b8d-121">常數</span><span class="sxs-lookup"><span data-stu-id="f5b8d-121">Constant</span></span>  |<span data-ttu-id="f5b8d-122">值</span><span class="sxs-lookup"><span data-stu-id="f5b8d-122">Value</span></span>  |<span data-ttu-id="f5b8d-123">描述</span><span class="sxs-lookup"><span data-stu-id="f5b8d-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="f5b8d-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f5b8d-124">0x80041001</span></span> | <span data-ttu-id="f5b8d-125">一般失敗。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f5b8d-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f5b8d-126">0x80041008</span></span> | <span data-ttu-id="f5b8d-127">一或多個參數無效，或指定了不正確的旗標和參數組合。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f5b8d-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f5b8d-128">0x80041006</span></span> | <span data-ttu-id="f5b8d-129">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f5b8d-130">0</span><span class="sxs-lookup"><span data-stu-id="f5b8d-130">0</span></span> | <span data-ttu-id="f5b8d-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f5b8d-132">備註</span><span class="sxs-lookup"><span data-stu-id="f5b8d-132">Remarks</span></span>

<span data-ttu-id="f5b8d-133">此函數會包裝對 [IWbemClassObject：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="f5b8d-134">命名傳回的會由旗標和參數的組合來控制。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="f5b8d-135">例如，函數可以傳回所有屬性的名稱，或只傳回索引鍵屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="f5b8d-136">主要篩選準則是在參數中指定 `lFlags` ，而其他參數則會根據它而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="f5b8d-137">中的旗標值 `lFlags` 為位欄位</span><span class="sxs-lookup"><span data-stu-id="f5b8d-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="f5b8d-138">可以做為引數傳遞的旗 `lEnumFlags` 標是 *WbemCli .h* 標頭檔中定義的位欄位，您也可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="f5b8d-139">您可以結合每個群組中的一個旗標與任何其他群組的任何旗標。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="f5b8d-140">不過，來自相同群組的旗標是互斥的。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="f5b8d-141">群組1旗標</span><span class="sxs-lookup"><span data-stu-id="f5b8d-141">Group 1 flags</span></span> |<span data-ttu-id="f5b8d-142">值</span><span class="sxs-lookup"><span data-stu-id="f5b8d-142">Value</span></span>  |<span data-ttu-id="f5b8d-143">描述</span><span class="sxs-lookup"><span data-stu-id="f5b8d-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="f5b8d-144">0</span><span class="sxs-lookup"><span data-stu-id="f5b8d-144">0</span></span> | <span data-ttu-id="f5b8d-145">傳回所有屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-145">Return all property names.</span></span> <span data-ttu-id="f5b8d-146">`strQualifierName` 和 `pQualifierVal` 都未使用。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="f5b8d-147">1</span><span class="sxs-lookup"><span data-stu-id="f5b8d-147">1</span></span> | <span data-ttu-id="f5b8d-148">只傳回具有參數所指定名稱之限定詞的屬性 `strQualifierName` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="f5b8d-149">如果使用此旗標，您必須指定 `strQualifierName` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="f5b8d-150">2</span><span class="sxs-lookup"><span data-stu-id="f5b8d-150">2</span></span> |  <span data-ttu-id="f5b8d-151">只傳回沒有參數所指定名稱之限定詞的屬性 `strQualifierName` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="f5b8d-152">如果使用此旗標，您必須指定 `strQualifierName` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="f5b8d-153">3</span><span class="sxs-lookup"><span data-stu-id="f5b8d-153">3</span></span> | <span data-ttu-id="f5b8d-154">只傳回具有參數所指定名稱之限定詞的屬性 `wszQualifierName` ，而且其值與結構所指定的值相同 `pQualifierVal` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="f5b8d-155">如果使用此旗標，您必須同時指定 `wszQualifierName` 和 `pQualifierValue` 。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="f5b8d-156">群組2旗標</span><span class="sxs-lookup"><span data-stu-id="f5b8d-156">Group 2 flags</span></span> |<span data-ttu-id="f5b8d-157">值</span><span class="sxs-lookup"><span data-stu-id="f5b8d-157">Value</span></span>  |<span data-ttu-id="f5b8d-158">描述</span><span class="sxs-lookup"><span data-stu-id="f5b8d-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="f5b8d-159">0x4</span><span class="sxs-lookup"><span data-stu-id="f5b8d-159">0x4</span></span> | <span data-ttu-id="f5b8d-160">只傳回定義索引鍵之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="f5b8d-161">0x8</span><span class="sxs-lookup"><span data-stu-id="f5b8d-161">0x8</span></span> | <span data-ttu-id="f5b8d-162">只傳回物件參考的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="f5b8d-163">群組3旗標</span><span class="sxs-lookup"><span data-stu-id="f5b8d-163">Group 3 flags</span></span> |<span data-ttu-id="f5b8d-164">值</span><span class="sxs-lookup"><span data-stu-id="f5b8d-164">Value</span></span>  |<span data-ttu-id="f5b8d-165">描述</span><span class="sxs-lookup"><span data-stu-id="f5b8d-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="f5b8d-166">0x10</span><span class="sxs-lookup"><span data-stu-id="f5b8d-166">0x10</span></span> | <span data-ttu-id="f5b8d-167">只傳回屬於最衍生類別的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="f5b8d-168">排除父類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="f5b8d-169">0x20</span><span class="sxs-lookup"><span data-stu-id="f5b8d-169">0x20</span></span> | <span data-ttu-id="f5b8d-170">只傳回屬於父類別的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="f5b8d-171">0x30</span><span class="sxs-lookup"><span data-stu-id="f5b8d-171">0x30</span></span> | <span data-ttu-id="f5b8d-172">只傳回系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="f5b8d-173">0x40</span><span class="sxs-lookup"><span data-stu-id="f5b8d-173">0x40</span></span> | <span data-ttu-id="f5b8d-174">只傳回非系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="f5b8d-175">函式一律會在傳回時配置新的 `SAFEARRAY` `WBEM_S_NO_ERROR` ，而且 `pstrNames` 一律設定為指向它。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="f5b8d-176">如果沒有屬性符合指定的篩選準則，則傳回的陣列可以有0個元素。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="f5b8d-177">如果函數傳回以外的值 `WBM_S_NO_ERROR` ， `SAFEARRAY` 則不會傳回新的結構。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5b8d-178">需求</span><span class="sxs-lookup"><span data-stu-id="f5b8d-178">Requirements</span></span>  

 <span data-ttu-id="f5b8d-179">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5b8d-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b8d-180">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="f5b8d-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f5b8d-181">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b8d-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b8d-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5b8d-182">See also</span></span>

- [<span data-ttu-id="f5b8d-183">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="f5b8d-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
