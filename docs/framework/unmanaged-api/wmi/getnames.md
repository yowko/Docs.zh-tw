---
title: GetNames 函式 （Unmanaged API 參考）
description: GetNames 函式來擷取物件屬性的名稱。
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
ms.openlocfilehash: b0065b2cbbd17c5bb3dca6773951cdb8729e59fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583557"
---
# <a name="getnames-function"></a><span data-ttu-id="e87f5-103">GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="e87f5-103">GetNames function</span></span>
<span data-ttu-id="e87f5-104">擷取物件屬性的子集合或所有名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e87f5-105">語法</span><span class="sxs-lookup"><span data-stu-id="e87f5-105">Syntax</span></span>  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="e87f5-106">參數</span><span class="sxs-lookup"><span data-stu-id="e87f5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e87f5-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="e87f5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e87f5-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="e87f5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="e87f5-109">[in]有效的指標`LPCWSTR`運作的限定詞名稱指定為篩選的一部分。</span><span class="sxs-lookup"><span data-stu-id="e87f5-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="e87f5-110">如需詳細資訊，請參閱 <<c0> [ 備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="e87f5-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="e87f5-111">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="e87f5-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="e87f5-112">[in]位元欄位的組合。</span><span class="sxs-lookup"><span data-stu-id="e87f5-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="e87f5-113">如需詳細資訊，請參閱 <<c0> [ 備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="e87f5-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="e87f5-114">[in]有效的指標`VARIANT`結構初始化為一個篩選值。</span><span class="sxs-lookup"><span data-stu-id="e87f5-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="e87f5-115">這個參數可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="e87f5-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="e87f5-116">[out]A`SAFEARRAY`結構，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="e87f5-117">項目，這個參數必須永遠是一個指向`null`。</span><span class="sxs-lookup"><span data-stu-id="e87f5-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="e87f5-118">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e87f5-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e87f5-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="e87f5-119">Return value</span></span>

<span data-ttu-id="e87f5-120">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="e87f5-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e87f5-121">常數</span><span class="sxs-lookup"><span data-stu-id="e87f5-121">Constant</span></span>  |<span data-ttu-id="e87f5-122">值</span><span class="sxs-lookup"><span data-stu-id="e87f5-122">Value</span></span>  |<span data-ttu-id="e87f5-123">描述</span><span class="sxs-lookup"><span data-stu-id="e87f5-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e87f5-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e87f5-124">0x80041001</span></span> | <span data-ttu-id="e87f5-125">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="e87f5-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e87f5-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e87f5-126">0x80041008</span></span> | <span data-ttu-id="e87f5-127">一或多個參數都不是有效的或指定的旗標和參數的正確組合。</span><span class="sxs-lookup"><span data-stu-id="e87f5-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e87f5-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e87f5-128">0x80041006</span></span> | <span data-ttu-id="e87f5-129">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="e87f5-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e87f5-130">0</span><span class="sxs-lookup"><span data-stu-id="e87f5-130">0</span></span> | <span data-ttu-id="e87f5-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e87f5-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e87f5-132">備註</span><span class="sxs-lookup"><span data-stu-id="e87f5-132">Remarks</span></span>

<span data-ttu-id="e87f5-133">此函式會包裝在呼叫[IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)方法。</span><span class="sxs-lookup"><span data-stu-id="e87f5-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="e87f5-134">傳回的具名是由控制旗標和參數的組合。</span><span class="sxs-lookup"><span data-stu-id="e87f5-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="e87f5-135">比方說，此函數可以傳回所有屬性的名稱或索引鍵屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="e87f5-136">主要的篩選條件中指定`lFlags`參數和其他參數根據它而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e87f5-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="e87f5-137">中的旗標值`lFlags`是位元欄位</span><span class="sxs-lookup"><span data-stu-id="e87f5-137">The flag values in `lFlags` are bit fields</span></span>


<span data-ttu-id="e87f5-138">可以做為傳遞的旗標`lEnumFlags`引數是中所定義的位元欄位*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。</span><span class="sxs-lookup"><span data-stu-id="e87f5-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="e87f5-139">您可以結合任何其他群組的任何旗標的每個群組中的一個旗標。</span><span class="sxs-lookup"><span data-stu-id="e87f5-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="e87f5-140">不過，從相同的群組的旗標是互斥的。</span><span class="sxs-lookup"><span data-stu-id="e87f5-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="e87f5-141">群組 1 旗標</span><span class="sxs-lookup"><span data-stu-id="e87f5-141">Group 1 flags</span></span> |<span data-ttu-id="e87f5-142">值</span><span class="sxs-lookup"><span data-stu-id="e87f5-142">Value</span></span>  |<span data-ttu-id="e87f5-143">描述</span><span class="sxs-lookup"><span data-stu-id="e87f5-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="e87f5-144">0</span><span class="sxs-lookup"><span data-stu-id="e87f5-144">0</span></span> | <span data-ttu-id="e87f5-145">傳回所有屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-145">Return all property names.</span></span> <span data-ttu-id="e87f5-146">`strQualifierName` 和`pQualifierVal`未使用。</span><span class="sxs-lookup"><span data-stu-id="e87f5-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="e87f5-147">1</span><span class="sxs-lookup"><span data-stu-id="e87f5-147">1</span></span> | <span data-ttu-id="e87f5-148">傳回具有所指定之名稱的限定詞的唯一屬性`strQualifierName`參數。</span><span class="sxs-lookup"><span data-stu-id="e87f5-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e87f5-149">如果會使用這個旗標，您必須指定`strQualifierName`。</span><span class="sxs-lookup"><span data-stu-id="e87f5-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="e87f5-150">2</span><span class="sxs-lookup"><span data-stu-id="e87f5-150">2</span></span> |  <span data-ttu-id="e87f5-151">傳回唯一的屬性所指定之名稱的限定詞沒有`strQualifierName`參數。</span><span class="sxs-lookup"><span data-stu-id="e87f5-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="e87f5-152">如果會使用這個旗標，您必須指定`strQualifierName`。</span><span class="sxs-lookup"><span data-stu-id="e87f5-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="e87f5-153">3</span><span class="sxs-lookup"><span data-stu-id="e87f5-153">3</span></span> | <span data-ttu-id="e87f5-154">傳回具有所指定之名稱的限定詞的屬性`wszQualifierName`參數也會有等於指定的值和`pQualifierVal`結構。</span><span class="sxs-lookup"><span data-stu-id="e87f5-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="e87f5-155">如果使用這個旗標，則您必須同時指定`wszQualifierName`和`pQualifierValue`。</span><span class="sxs-lookup"><span data-stu-id="e87f5-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="e87f5-156">群組 2 旗標</span><span class="sxs-lookup"><span data-stu-id="e87f5-156">Group 2 flags</span></span> |<span data-ttu-id="e87f5-157">值</span><span class="sxs-lookup"><span data-stu-id="e87f5-157">Value</span></span>  |<span data-ttu-id="e87f5-158">描述</span><span class="sxs-lookup"><span data-stu-id="e87f5-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="e87f5-159">0x4</span><span class="sxs-lookup"><span data-stu-id="e87f5-159">0x4</span></span> | <span data-ttu-id="e87f5-160">傳回只定義索引鍵的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="e87f5-161">0x8</span><span class="sxs-lookup"><span data-stu-id="e87f5-161">0x8</span></span> | <span data-ttu-id="e87f5-162">傳回唯一的屬性名稱是物件參考。</span><span class="sxs-lookup"><span data-stu-id="e87f5-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="e87f5-163">群組 3 旗標</span><span class="sxs-lookup"><span data-stu-id="e87f5-163">Group 3 flags</span></span> |<span data-ttu-id="e87f5-164">值</span><span class="sxs-lookup"><span data-stu-id="e87f5-164">Value</span></span>  |<span data-ttu-id="e87f5-165">描述</span><span class="sxs-lookup"><span data-stu-id="e87f5-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e87f5-166">0x10</span><span class="sxs-lookup"><span data-stu-id="e87f5-166">0x10</span></span> | <span data-ttu-id="e87f5-167">傳回屬於最具衍生性的類別屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="e87f5-168">排除的父類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="e87f5-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="e87f5-169">0x20</span><span class="sxs-lookup"><span data-stu-id="e87f5-169">0x20</span></span> | <span data-ttu-id="e87f5-170">傳回屬於父類別屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="e87f5-171">0x30</span><span class="sxs-lookup"><span data-stu-id="e87f5-171">0x30</span></span> | <span data-ttu-id="e87f5-172">傳回系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="e87f5-173">0x40</span><span class="sxs-lookup"><span data-stu-id="e87f5-173">0x40</span></span> | <span data-ttu-id="e87f5-174">傳回非系統屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e87f5-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="e87f5-175">此函式一律會配置新`SAFEARRAY`如果它傳回`WBEM_S_NO_ERROR`，和`pstrNames`一定會設定為指向它。</span><span class="sxs-lookup"><span data-stu-id="e87f5-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="e87f5-176">如果沒有屬性符合指定的篩選條件，傳回的陣列可以有 0 的項目。</span><span class="sxs-lookup"><span data-stu-id="e87f5-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="e87f5-177">如果函數傳回的值以外`WBM_S_NO_ERROR`，新`SAFEARRAY`結構並不會傳回。</span><span class="sxs-lookup"><span data-stu-id="e87f5-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="e87f5-178">需求</span><span class="sxs-lookup"><span data-stu-id="e87f5-178">Requirements</span></span>  
 <span data-ttu-id="e87f5-179">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e87f5-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e87f5-180">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e87f5-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e87f5-181">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e87f5-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87f5-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e87f5-182">See also</span></span>
- [<span data-ttu-id="e87f5-183">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="e87f5-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
