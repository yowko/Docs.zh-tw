---
title: 開始枚舉函數（非託管 API 引用）
description: BeginEe枚舉函數將枚舉器重置為枚舉的開頭
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176873"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="052dc-103">BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="052dc-103">BeginEnumeration function</span></span>
<span data-ttu-id="052dc-104">將枚舉器重置回枚舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="052dc-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="052dc-105">語法</span><span class="sxs-lookup"><span data-stu-id="052dc-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="052dc-106">參數</span><span class="sxs-lookup"><span data-stu-id="052dc-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="052dc-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="052dc-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="052dc-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="052dc-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="052dc-109">[在]控制枚舉中包含的屬性的[備註](#remarks)部分中描述的標誌或值的位組合。</span><span class="sxs-lookup"><span data-stu-id="052dc-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="052dc-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="052dc-110">Return value</span></span>

<span data-ttu-id="052dc-111">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="052dc-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="052dc-112">持續性</span><span class="sxs-lookup"><span data-stu-id="052dc-112">Constant</span></span>  |<span data-ttu-id="052dc-113">值</span><span class="sxs-lookup"><span data-stu-id="052dc-113">Value</span></span>  |<span data-ttu-id="052dc-114">描述</span><span class="sxs-lookup"><span data-stu-id="052dc-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="052dc-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="052dc-115">0x80041008</span></span> | <span data-ttu-id="052dc-116">中`lEnumFlags`的標誌組合無效，或指定了不正確參數。</span><span class="sxs-lookup"><span data-stu-id="052dc-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="052dc-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="052dc-117">0x8004101d</span></span> | <span data-ttu-id="052dc-118">第二次呼叫`BeginEnumeration`是在沒有干預調用[`EndEnumeration`](endenumeration.md)的情況下進行的。</span><span class="sxs-lookup"><span data-stu-id="052dc-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="052dc-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="052dc-119">0x80041006</span></span> | <span data-ttu-id="052dc-120">沒有足夠的記憶體可用於開始新的枚舉。</span><span class="sxs-lookup"><span data-stu-id="052dc-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="052dc-121">0</span><span class="sxs-lookup"><span data-stu-id="052dc-121">0</span></span> | <span data-ttu-id="052dc-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="052dc-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="052dc-123">備註</span><span class="sxs-lookup"><span data-stu-id="052dc-123">Remarks</span></span>

<span data-ttu-id="052dc-124">此函數包裝對[IWbemClassObject 的調用：：開始枚舉](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法。</span><span class="sxs-lookup"><span data-stu-id="052dc-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="052dc-125">可在`lEnumFlags`*WbemCli.h*標標頭檔中定義作為參數傳遞的標誌，也可以將它們定義為代碼中的常量。</span><span class="sxs-lookup"><span data-stu-id="052dc-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="052dc-126">您可以將每個組中的一個標誌與任何其他組的任何標誌合併。</span><span class="sxs-lookup"><span data-stu-id="052dc-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="052dc-127">但是，來自同一組的標誌是互斥的。</span><span class="sxs-lookup"><span data-stu-id="052dc-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="052dc-128">**組 1**</span><span class="sxs-lookup"><span data-stu-id="052dc-128">**Group 1**</span></span>

|<span data-ttu-id="052dc-129">持續性</span><span class="sxs-lookup"><span data-stu-id="052dc-129">Constant</span></span>  |<span data-ttu-id="052dc-130">值</span><span class="sxs-lookup"><span data-stu-id="052dc-130">Value</span></span>  |<span data-ttu-id="052dc-131">描述</span><span class="sxs-lookup"><span data-stu-id="052dc-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="052dc-132">0x4</span><span class="sxs-lookup"><span data-stu-id="052dc-132">0x4</span></span> | <span data-ttu-id="052dc-133">僅包含構成金鑰的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="052dc-134">0x8</span><span class="sxs-lookup"><span data-stu-id="052dc-134">0x8</span></span> | <span data-ttu-id="052dc-135">僅包含物件引用的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="052dc-136">**組 2**</span><span class="sxs-lookup"><span data-stu-id="052dc-136">**Group 2**</span></span>

<span data-ttu-id="052dc-137">持續性</span><span class="sxs-lookup"><span data-stu-id="052dc-137">Constant</span></span>  |<span data-ttu-id="052dc-138">值</span><span class="sxs-lookup"><span data-stu-id="052dc-138">Value</span></span>  |<span data-ttu-id="052dc-139">描述</span><span class="sxs-lookup"><span data-stu-id="052dc-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="052dc-140">0x30</span><span class="sxs-lookup"><span data-stu-id="052dc-140">0x30</span></span> | <span data-ttu-id="052dc-141">僅將枚舉限制為系統屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="052dc-142">0x40</span><span class="sxs-lookup"><span data-stu-id="052dc-142">0x40</span></span> | <span data-ttu-id="052dc-143">包括本地和傳播屬性，但從枚舉中排除系統屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="052dc-144">對於類：</span><span class="sxs-lookup"><span data-stu-id="052dc-144">For classes:</span></span>

<span data-ttu-id="052dc-145">持續性</span><span class="sxs-lookup"><span data-stu-id="052dc-145">Constant</span></span>  |<span data-ttu-id="052dc-146">值</span><span class="sxs-lookup"><span data-stu-id="052dc-146">Value</span></span>  |<span data-ttu-id="052dc-147">描述</span><span class="sxs-lookup"><span data-stu-id="052dc-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="052dc-148">0x100</span><span class="sxs-lookup"><span data-stu-id="052dc-148">0x100</span></span> | <span data-ttu-id="052dc-149">將枚舉限制為類定義中重寫的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="052dc-150">0x100</span><span class="sxs-lookup"><span data-stu-id="052dc-150">0x100</span></span> | <span data-ttu-id="052dc-151">將枚舉限制為當前類定義中重寫的屬性和類中定義的新屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="052dc-152">0 x 300</span><span class="sxs-lookup"><span data-stu-id="052dc-152">0x300</span></span> | <span data-ttu-id="052dc-153">要針對`lEnumFlags`值應用的蒙版（而不是標誌），以檢查是否設置了。 `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`</span><span class="sxs-lookup"><span data-stu-id="052dc-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="052dc-154">0x10</span><span class="sxs-lookup"><span data-stu-id="052dc-154">0x10</span></span> | <span data-ttu-id="052dc-155">將枚舉限制為在類本身中定義或修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="052dc-156">0x20</span><span class="sxs-lookup"><span data-stu-id="052dc-156">0x20</span></span> | <span data-ttu-id="052dc-157">將枚舉限制為從基類繼承的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="052dc-158">例如：</span><span class="sxs-lookup"><span data-stu-id="052dc-158">For instances:</span></span>

<span data-ttu-id="052dc-159">持續性</span><span class="sxs-lookup"><span data-stu-id="052dc-159">Constant</span></span>  |<span data-ttu-id="052dc-160">值</span><span class="sxs-lookup"><span data-stu-id="052dc-160">Value</span></span>  |<span data-ttu-id="052dc-161">描述</span><span class="sxs-lookup"><span data-stu-id="052dc-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="052dc-162">0x10</span><span class="sxs-lookup"><span data-stu-id="052dc-162">0x10</span></span> | <span data-ttu-id="052dc-163">將枚舉限制為在類本身中定義或修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="052dc-164">0x20</span><span class="sxs-lookup"><span data-stu-id="052dc-164">0x20</span></span> | <span data-ttu-id="052dc-165">將枚舉限制為從基類繼承的屬性。</span><span class="sxs-lookup"><span data-stu-id="052dc-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="052dc-166">需求</span><span class="sxs-lookup"><span data-stu-id="052dc-166">Requirements</span></span>  
 <span data-ttu-id="052dc-167">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="052dc-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="052dc-168">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="052dc-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="052dc-169">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="052dc-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052dc-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="052dc-170">See also</span></span>

- [<span data-ttu-id="052dc-171">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="052dc-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
