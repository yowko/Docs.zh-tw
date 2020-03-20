---
title: 獲取名稱功能（非託管 API 引用）
description: GetNames 函數檢索物件屬性的名稱。
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174949"
---
# <a name="getnames-function"></a><span data-ttu-id="12b26-103">GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="12b26-103">GetNames function</span></span>
<span data-ttu-id="12b26-104">擷取物件屬性的子集合或所有名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="12b26-105">語法</span><span class="sxs-lookup"><span data-stu-id="12b26-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="12b26-106">參數</span><span class="sxs-lookup"><span data-stu-id="12b26-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="12b26-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="12b26-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="12b26-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="12b26-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="12b26-109">[在]指向有效的`LPCWSTR`指標，用於指定作為篩選器一部分運行的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="12b26-110">有關詳細資訊，請參閱[備註](#remarks)部分。</span><span class="sxs-lookup"><span data-stu-id="12b26-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="12b26-111">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="12b26-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="12b26-112">[在]位欄位的組合。</span><span class="sxs-lookup"><span data-stu-id="12b26-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="12b26-113">有關詳細資訊，請參閱[備註](#remarks)部分。</span><span class="sxs-lookup"><span data-stu-id="12b26-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="12b26-114">`pQualifierValue`[在]指向初始化到篩選器`VARIANT`值的有效結構的指標。</span><span class="sxs-lookup"><span data-stu-id="12b26-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="12b26-115">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="12b26-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="12b26-116">[出]包含`SAFEARRAY`屬性名稱的結構。</span><span class="sxs-lookup"><span data-stu-id="12b26-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="12b26-117">在輸入時，此參數必須始終是指向`null`的指標。</span><span class="sxs-lookup"><span data-stu-id="12b26-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="12b26-118">有關詳細資訊，請參閱[備註](#remarks)部分。</span><span class="sxs-lookup"><span data-stu-id="12b26-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="12b26-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="12b26-119">Return value</span></span>

<span data-ttu-id="12b26-120">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="12b26-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="12b26-121">持續性</span><span class="sxs-lookup"><span data-stu-id="12b26-121">Constant</span></span>  |<span data-ttu-id="12b26-122">值</span><span class="sxs-lookup"><span data-stu-id="12b26-122">Value</span></span>  |<span data-ttu-id="12b26-123">描述</span><span class="sxs-lookup"><span data-stu-id="12b26-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="12b26-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="12b26-124">0x80041001</span></span> | <span data-ttu-id="12b26-125">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="12b26-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="12b26-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="12b26-126">0x80041008</span></span> | <span data-ttu-id="12b26-127">一個或多個參數無效，或指定了不正確的標誌和參數組合。</span><span class="sxs-lookup"><span data-stu-id="12b26-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="12b26-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="12b26-128">0x80041006</span></span> | <span data-ttu-id="12b26-129">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="12b26-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="12b26-130">0</span><span class="sxs-lookup"><span data-stu-id="12b26-130">0</span></span> | <span data-ttu-id="12b26-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="12b26-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="12b26-132">備註</span><span class="sxs-lookup"><span data-stu-id="12b26-132">Remarks</span></span>

<span data-ttu-id="12b26-133">此函數包裝對[IWbem ClassObject 的調用：：getNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)方法。</span><span class="sxs-lookup"><span data-stu-id="12b26-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="12b26-134">返回的命名由標誌和參數的組合控制。</span><span class="sxs-lookup"><span data-stu-id="12b26-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="12b26-135">例如，函數可以返回所有屬性的名稱，也可以僅返回鍵屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="12b26-136">主篩選器在`lFlags`參數中指定，其他參數因它而異。</span><span class="sxs-lookup"><span data-stu-id="12b26-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="12b26-137">中`lFlags`的標誌值是位欄位</span><span class="sxs-lookup"><span data-stu-id="12b26-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="12b26-138">可以作為`lEnumFlags`參數傳遞的標誌是在*WbemCli.h*標標頭檔中定義的位欄位，也可以將它們定義為代碼中的常量。</span><span class="sxs-lookup"><span data-stu-id="12b26-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="12b26-139">您可以將每個組中的一個標誌與任何其他組的任何標誌合併。</span><span class="sxs-lookup"><span data-stu-id="12b26-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="12b26-140">但是，來自同一組的標誌是互斥的。</span><span class="sxs-lookup"><span data-stu-id="12b26-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="12b26-141">組 1 標誌</span><span class="sxs-lookup"><span data-stu-id="12b26-141">Group 1 flags</span></span> |<span data-ttu-id="12b26-142">值</span><span class="sxs-lookup"><span data-stu-id="12b26-142">Value</span></span>  |<span data-ttu-id="12b26-143">描述</span><span class="sxs-lookup"><span data-stu-id="12b26-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="12b26-144">0</span><span class="sxs-lookup"><span data-stu-id="12b26-144">0</span></span> | <span data-ttu-id="12b26-145">返回所有屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-145">Return all property names.</span></span> <span data-ttu-id="12b26-146">`strQualifierName`未`pQualifierVal`使用。</span><span class="sxs-lookup"><span data-stu-id="12b26-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="12b26-147">1</span><span class="sxs-lookup"><span data-stu-id="12b26-147">1</span></span> | <span data-ttu-id="12b26-148">僅返回具有`strQualifierName`參數指定名稱限定詞的屬性。</span><span class="sxs-lookup"><span data-stu-id="12b26-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="12b26-149">如果使用此標誌，則必須指定`strQualifierName`。</span><span class="sxs-lookup"><span data-stu-id="12b26-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="12b26-150">2</span><span class="sxs-lookup"><span data-stu-id="12b26-150">2</span></span> |  <span data-ttu-id="12b26-151">僅返回沒有`strQualifierName`參數指定名稱限定詞的屬性。</span><span class="sxs-lookup"><span data-stu-id="12b26-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="12b26-152">如果使用此標誌，則必須指定`strQualifierName`。</span><span class="sxs-lookup"><span data-stu-id="12b26-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="12b26-153">3</span><span class="sxs-lookup"><span data-stu-id="12b26-153">3</span></span> | <span data-ttu-id="12b26-154">僅返回具有`wszQualifierName`參數指定名稱限定詞且值與`pQualifierVal`結構指定的值相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="12b26-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="12b26-155">如果使用此標誌，則必須同時指定 a`wszQualifierName`和 。 `pQualifierValue`</span><span class="sxs-lookup"><span data-stu-id="12b26-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="12b26-156">組 2 標誌</span><span class="sxs-lookup"><span data-stu-id="12b26-156">Group 2 flags</span></span> |<span data-ttu-id="12b26-157">值</span><span class="sxs-lookup"><span data-stu-id="12b26-157">Value</span></span>  |<span data-ttu-id="12b26-158">描述</span><span class="sxs-lookup"><span data-stu-id="12b26-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="12b26-159">0x4</span><span class="sxs-lookup"><span data-stu-id="12b26-159">0x4</span></span> | <span data-ttu-id="12b26-160">僅返回定義鍵的屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="12b26-161">0x8</span><span class="sxs-lookup"><span data-stu-id="12b26-161">0x8</span></span> | <span data-ttu-id="12b26-162">僅返回作為物件引用的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="12b26-163">組 3 標誌</span><span class="sxs-lookup"><span data-stu-id="12b26-163">Group 3 flags</span></span> |<span data-ttu-id="12b26-164">值</span><span class="sxs-lookup"><span data-stu-id="12b26-164">Value</span></span>  |<span data-ttu-id="12b26-165">描述</span><span class="sxs-lookup"><span data-stu-id="12b26-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="12b26-166">0x10</span><span class="sxs-lookup"><span data-stu-id="12b26-166">0x10</span></span> | <span data-ttu-id="12b26-167">僅返回屬於最派生類的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="12b26-168">從父類中排除屬性。</span><span class="sxs-lookup"><span data-stu-id="12b26-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="12b26-169">0x20</span><span class="sxs-lookup"><span data-stu-id="12b26-169">0x20</span></span> | <span data-ttu-id="12b26-170">僅返回屬於父類的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="12b26-171">0x30</span><span class="sxs-lookup"><span data-stu-id="12b26-171">0x30</span></span> | <span data-ttu-id="12b26-172">僅返回系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="12b26-173">0x40</span><span class="sxs-lookup"><span data-stu-id="12b26-173">0x40</span></span> | <span data-ttu-id="12b26-174">僅返回非系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="12b26-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="12b26-175">如果函數返回`SAFEARRAY``WBEM_S_NO_ERROR`，則始終分配新函數，並且`pstrNames`始終設置為指向它。</span><span class="sxs-lookup"><span data-stu-id="12b26-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="12b26-176">如果沒有與指定篩選器匹配的屬性，則返回的陣列可以具有 0 個元素。</span><span class="sxs-lookup"><span data-stu-id="12b26-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="12b26-177">如果函數返回的值，`WBM_S_NO_ERROR`則不返回新`SAFEARRAY`結構。</span><span class="sxs-lookup"><span data-stu-id="12b26-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="12b26-178">需求</span><span class="sxs-lookup"><span data-stu-id="12b26-178">Requirements</span></span>  
 <span data-ttu-id="12b26-179">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12b26-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b26-180">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="12b26-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="12b26-181">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="12b26-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b26-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12b26-182">See also</span></span>

- [<span data-ttu-id="12b26-183">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="12b26-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
