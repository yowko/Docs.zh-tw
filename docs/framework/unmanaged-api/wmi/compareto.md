---
title: CompareTo 函式 （Unmanaged API 參考）
description: CompareTo 函式會比較的物件，與其他的 WMI 物件。
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208417"
---
# <a name="compareto-function"></a><span data-ttu-id="02bc7-103">CompareTo 函式</span><span class="sxs-lookup"><span data-stu-id="02bc7-103">CompareTo function</span></span>
<span data-ttu-id="02bc7-104">將物件與另一個 Windows 管理物件比較。</span><span class="sxs-lookup"><span data-stu-id="02bc7-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="02bc7-105">語法</span><span class="sxs-lookup"><span data-stu-id="02bc7-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="02bc7-106">參數</span><span class="sxs-lookup"><span data-stu-id="02bc7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="02bc7-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="02bc7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="02bc7-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="02bc7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`  
<span data-ttu-id="02bc7-109">[in]指定物件特性時應考量的比較旗標的位元組合。</span><span class="sxs-lookup"><span data-stu-id="02bc7-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="02bc7-110">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="02bc7-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="02bc7-111">[in]比較的物件。</span><span class="sxs-lookup"><span data-stu-id="02bc7-111">[in] The object for comparison.</span></span> <span data-ttu-id="02bc7-112">`pcompareTo` 必須是有效[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體，它不能是`null`。</span><span class="sxs-lookup"><span data-stu-id="02bc7-112">`pcompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="02bc7-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="02bc7-113">Return value</span></span>

<span data-ttu-id="02bc7-114">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="02bc7-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="02bc7-115">常數</span><span class="sxs-lookup"><span data-stu-id="02bc7-115">Constant</span></span>  |<span data-ttu-id="02bc7-116">值</span><span class="sxs-lookup"><span data-stu-id="02bc7-116">Value</span></span>  |<span data-ttu-id="02bc7-117">描述</span><span class="sxs-lookup"><span data-stu-id="02bc7-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="02bc7-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="02bc7-118">0x80041001</span></span> | <span data-ttu-id="02bc7-119">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="02bc7-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="02bc7-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="02bc7-120">0x80041008</span></span> | <span data-ttu-id="02bc7-121">參數無效。</span><span class="sxs-lookup"><span data-stu-id="02bc7-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="02bc7-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="02bc7-122">0x8004101d</span></span> | <span data-ttu-id="02bc7-123">第二次呼叫`BeginEnumeration`而不需要的介入呼叫進行[ `EndEnumeration` ](endenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="02bc7-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="02bc7-124">0</span><span class="sxs-lookup"><span data-stu-id="02bc7-124">0</span></span> | <span data-ttu-id="02bc7-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="02bc7-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="02bc7-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="02bc7-126">0x40003</span></span> | <span data-ttu-id="02bc7-127">物件不相同。</span><span class="sxs-lookup"><span data-stu-id="02bc7-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="02bc7-128">0</span><span class="sxs-lookup"><span data-stu-id="02bc7-128">0</span></span> | <span data-ttu-id="02bc7-129">物件是相同的比較旗標為基礎。</span><span class="sxs-lookup"><span data-stu-id="02bc7-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="02bc7-130">備註</span><span class="sxs-lookup"><span data-stu-id="02bc7-130">Remarks</span></span>

<span data-ttu-id="02bc7-131">此函式會包裝在呼叫[IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)方法。</span><span class="sxs-lookup"><span data-stu-id="02bc7-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="02bc7-132">可以做為傳遞的旗標`lEnumFlags`中所定義的引數*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。</span><span class="sxs-lookup"><span data-stu-id="02bc7-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="02bc7-133">您可以藉由指定下列旗標的位元組合，指定在比較中涉及的個別特性：</span><span class="sxs-lookup"><span data-stu-id="02bc7-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="02bc7-134">常數</span><span class="sxs-lookup"><span data-stu-id="02bc7-134">Constant</span></span>  |<span data-ttu-id="02bc7-135">值</span><span class="sxs-lookup"><span data-stu-id="02bc7-135">Value</span></span>  |<span data-ttu-id="02bc7-136">描述</span><span class="sxs-lookup"><span data-stu-id="02bc7-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="02bc7-137">2</span><span class="sxs-lookup"><span data-stu-id="02bc7-137">2</span></span> | <span data-ttu-id="02bc7-138">忽略來源 （伺服器和其來源的命名空間）。</span><span class="sxs-lookup"><span data-stu-id="02bc7-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="02bc7-139">1</span><span class="sxs-lookup"><span data-stu-id="02bc7-139">1</span></span> | <span data-ttu-id="02bc7-140">忽略所有的限定詞 (包括**金鑰**並**動態**)</span><span class="sxs-lookup"><span data-stu-id="02bc7-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="02bc7-141">4</span><span class="sxs-lookup"><span data-stu-id="02bc7-141">4</span></span> | <span data-ttu-id="02bc7-142">忽略屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="02bc7-142">Ignore default values of properties.</span></span> <span data-ttu-id="02bc7-143">這個旗標僅適用於比較的類別。</span><span class="sxs-lookup"><span data-stu-id="02bc7-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="02bc7-144">0x20</span><span class="sxs-lookup"><span data-stu-id="02bc7-144">0x20</span></span> | <span data-ttu-id="02bc7-145">忽略限定詞標註。</span><span class="sxs-lookup"><span data-stu-id="02bc7-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="02bc7-146">這個旗標仍限定詞納入考量，但會忽略類型差異，例如傳用規則並覆寫限制。</span><span class="sxs-lookup"><span data-stu-id="02bc7-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="02bc7-147">0x10</span><span class="sxs-lookup"><span data-stu-id="02bc7-147">0x10</span></span> | <span data-ttu-id="02bc7-148">忽略大小寫比較字串值。</span><span class="sxs-lookup"><span data-stu-id="02bc7-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="02bc7-149">這適用於字串和限定詞的值。</span><span class="sxs-lookup"><span data-stu-id="02bc7-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="02bc7-150">屬性和限定詞的名稱比較一律會區分大小寫，不論是否設定此旗標的。</span><span class="sxs-lookup"><span data-stu-id="02bc7-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="02bc7-151">0x8</span><span class="sxs-lookup"><span data-stu-id="02bc7-151">0x8</span></span> | <span data-ttu-id="02bc7-152">假設正在比較的物件都是相同類別的執行個體的序列。</span><span class="sxs-lookup"><span data-stu-id="02bc7-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="02bc7-153">因此，這個旗標會比較執行個體相關資訊僅供參考。</span><span class="sxs-lookup"><span data-stu-id="02bc7-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="02bc7-154">您可以使用這個旗標來最佳化效能。</span><span class="sxs-lookup"><span data-stu-id="02bc7-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="02bc7-155">如果物件不在相同類別中，則結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="02bc7-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="02bc7-156">或者，您也可以指定單一複合旗標，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02bc7-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="02bc7-157">常數</span><span class="sxs-lookup"><span data-stu-id="02bc7-157">Constant</span></span>  |<span data-ttu-id="02bc7-158">值</span><span class="sxs-lookup"><span data-stu-id="02bc7-158">Value</span></span>  |<span data-ttu-id="02bc7-159">描述</span><span class="sxs-lookup"><span data-stu-id="02bc7-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="02bc7-160">0</span><span class="sxs-lookup"><span data-stu-id="02bc7-160">0</span></span> | <span data-ttu-id="02bc7-161">請考慮在比較中的所有功能。</span><span class="sxs-lookup"><span data-stu-id="02bc7-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="02bc7-162">需求</span><span class="sxs-lookup"><span data-stu-id="02bc7-162">Requirements</span></span>  
 <span data-ttu-id="02bc7-163">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02bc7-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02bc7-164">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="02bc7-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="02bc7-165">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="02bc7-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bc7-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02bc7-166">See also</span></span>  
[<span data-ttu-id="02bc7-167">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="02bc7-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
