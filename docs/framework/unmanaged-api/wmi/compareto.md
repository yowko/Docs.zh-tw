---
title: CompareTo 函式（非受控 API 參考）
description: CompareTo 函數會比較物件與另一個 WMI 物件。
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
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798782"
---
# <a name="compareto-function"></a><span data-ttu-id="86b26-103">CompareTo 函式</span><span class="sxs-lookup"><span data-stu-id="86b26-103">CompareTo function</span></span>

<span data-ttu-id="86b26-104">將物件與另一個 Windows 管理物件比較。</span><span class="sxs-lookup"><span data-stu-id="86b26-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="86b26-105">語法</span><span class="sxs-lookup"><span data-stu-id="86b26-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="86b26-106">參數</span><span class="sxs-lookup"><span data-stu-id="86b26-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="86b26-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="86b26-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="86b26-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="86b26-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="86b26-109">在旗標的位元組合，指定要考慮比較的物件特性。</span><span class="sxs-lookup"><span data-stu-id="86b26-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="86b26-110">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="86b26-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="86b26-111">在要比較的物件。</span><span class="sxs-lookup"><span data-stu-id="86b26-111">[in] The object for comparison.</span></span> <span data-ttu-id="86b26-112">`pCompareTo`必須是有效的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例;不能是`null`。</span><span class="sxs-lookup"><span data-stu-id="86b26-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="86b26-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="86b26-113">Return value</span></span>

<span data-ttu-id="86b26-114">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="86b26-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="86b26-115">常數</span><span class="sxs-lookup"><span data-stu-id="86b26-115">Constant</span></span>  |<span data-ttu-id="86b26-116">值</span><span class="sxs-lookup"><span data-stu-id="86b26-116">Value</span></span>  |<span data-ttu-id="86b26-117">描述</span><span class="sxs-lookup"><span data-stu-id="86b26-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="86b26-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="86b26-118">0x80041001</span></span> | <span data-ttu-id="86b26-119">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="86b26-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="86b26-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="86b26-120">0x80041008</span></span> | <span data-ttu-id="86b26-121">參數無效。</span><span class="sxs-lookup"><span data-stu-id="86b26-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="86b26-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="86b26-122">0x8004101d</span></span> | <span data-ttu-id="86b26-123">第二次呼叫`BeginEnumeration`時，不需要介入的[`EndEnumeration`](endenumeration.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="86b26-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="86b26-124">0</span><span class="sxs-lookup"><span data-stu-id="86b26-124">0</span></span> | <span data-ttu-id="86b26-125">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="86b26-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="86b26-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="86b26-126">0x40003</span></span> | <span data-ttu-id="86b26-127">物件不同。</span><span class="sxs-lookup"><span data-stu-id="86b26-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="86b26-128">0</span><span class="sxs-lookup"><span data-stu-id="86b26-128">0</span></span> | <span data-ttu-id="86b26-129">根據比較旗標，物件是相同的。</span><span class="sxs-lookup"><span data-stu-id="86b26-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="86b26-130">備註</span><span class="sxs-lookup"><span data-stu-id="86b26-130">Remarks</span></span>

<span data-ttu-id="86b26-131">此函式會包裝對[IWbemClassObject：： CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="86b26-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="86b26-132">可當做`lEnumFlags`引數傳遞的旗標會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="86b26-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="86b26-133">您可以藉由指定下列旗標的位元組合，指定涉及比較的個別特性：</span><span class="sxs-lookup"><span data-stu-id="86b26-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="86b26-134">常數</span><span class="sxs-lookup"><span data-stu-id="86b26-134">Constant</span></span>  |<span data-ttu-id="86b26-135">值</span><span class="sxs-lookup"><span data-stu-id="86b26-135">Value</span></span>  |<span data-ttu-id="86b26-136">說明</span><span class="sxs-lookup"><span data-stu-id="86b26-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="86b26-137">2</span><span class="sxs-lookup"><span data-stu-id="86b26-137">2</span></span> | <span data-ttu-id="86b26-138">忽略來源（伺服器及其來源的命名空間）。</span><span class="sxs-lookup"><span data-stu-id="86b26-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="86b26-139">1</span><span class="sxs-lookup"><span data-stu-id="86b26-139">1</span></span> | <span data-ttu-id="86b26-140">忽略所有限定詞（包括**金鑰**和**動態**）</span><span class="sxs-lookup"><span data-stu-id="86b26-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="86b26-141">4</span><span class="sxs-lookup"><span data-stu-id="86b26-141">4</span></span> | <span data-ttu-id="86b26-142">忽略屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="86b26-142">Ignore default values of properties.</span></span> <span data-ttu-id="86b26-143">此旗標僅適用于類別的比較。</span><span class="sxs-lookup"><span data-stu-id="86b26-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="86b26-144">0x20</span><span class="sxs-lookup"><span data-stu-id="86b26-144">0x20</span></span> | <span data-ttu-id="86b26-145">略過辨識符號類別。</span><span class="sxs-lookup"><span data-stu-id="86b26-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="86b26-146">此旗標仍會將限定詞納入考慮，但會忽略類似傳播規則和覆寫限制的類別區別。</span><span class="sxs-lookup"><span data-stu-id="86b26-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="86b26-147">0x10</span><span class="sxs-lookup"><span data-stu-id="86b26-147">0x10</span></span> | <span data-ttu-id="86b26-148">比較字串值時，忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="86b26-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="86b26-149">這同時適用于字串和辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="86b26-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="86b26-150">不論是否已設定此旗標，屬性和限定詞名稱的比較一律會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="86b26-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="86b26-151">0x8</span><span class="sxs-lookup"><span data-stu-id="86b26-151">0x8</span></span> | <span data-ttu-id="86b26-152">假設要比較的物件是相同類別的實例。</span><span class="sxs-lookup"><span data-stu-id="86b26-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="86b26-153">因此，此旗標只會比較與實例相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="86b26-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="86b26-154">使用此旗標來優化效能。</span><span class="sxs-lookup"><span data-stu-id="86b26-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="86b26-155">如果物件不是相同的類別，則結果會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="86b26-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="86b26-156">或者，您可以指定單一複合旗標，如下所示：</span><span class="sxs-lookup"><span data-stu-id="86b26-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="86b26-157">常數</span><span class="sxs-lookup"><span data-stu-id="86b26-157">Constant</span></span>  |<span data-ttu-id="86b26-158">值</span><span class="sxs-lookup"><span data-stu-id="86b26-158">Value</span></span>  |<span data-ttu-id="86b26-159">描述</span><span class="sxs-lookup"><span data-stu-id="86b26-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="86b26-160">0</span><span class="sxs-lookup"><span data-stu-id="86b26-160">0</span></span> | <span data-ttu-id="86b26-161">請考慮比較中的所有功能。</span><span class="sxs-lookup"><span data-stu-id="86b26-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="86b26-162">需求</span><span class="sxs-lookup"><span data-stu-id="86b26-162">Requirements</span></span>

<span data-ttu-id="86b26-163">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86b26-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="86b26-164">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="86b26-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="86b26-165">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="86b26-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="86b26-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86b26-166">See also</span></span>

- [<span data-ttu-id="86b26-167">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="86b26-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
