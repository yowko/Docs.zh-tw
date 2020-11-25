---
title: 'BeginEnumeration 函式 (非受控 API 參考) '
description: BeginEnumeration 函式會將列舉值重設為列舉的開頭
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
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708214"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="2205c-103">BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="2205c-103">BeginEnumeration function</span></span>

<span data-ttu-id="2205c-104">將列舉值重設回列舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="2205c-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2205c-105">語法</span><span class="sxs-lookup"><span data-stu-id="2205c-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="2205c-106">參數</span><span class="sxs-lookup"><span data-stu-id="2205c-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="2205c-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="2205c-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="2205c-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="2205c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="2205c-109">在 [備註](#remarks) 區段中所述之旗標或值的位元組合，可控制列舉中包含的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2205c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="2205c-110">Return value</span></span>

<span data-ttu-id="2205c-111">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="2205c-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2205c-112">常數</span><span class="sxs-lookup"><span data-stu-id="2205c-112">Constant</span></span>  |<span data-ttu-id="2205c-113">值</span><span class="sxs-lookup"><span data-stu-id="2205c-113">Value</span></span>  |<span data-ttu-id="2205c-114">描述</span><span class="sxs-lookup"><span data-stu-id="2205c-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2205c-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2205c-115">0x80041008</span></span> | <span data-ttu-id="2205c-116">中的旗標組合 `lEnumFlags` 無效，或指定的引數無效。</span><span class="sxs-lookup"><span data-stu-id="2205c-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="2205c-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2205c-117">0x8004101d</span></span> | <span data-ttu-id="2205c-118">對進行的第二個呼叫， `BeginEnumeration` 而不需要中間的呼叫 [`EndEnumeration`](endenumeration.md) 。</span><span class="sxs-lookup"><span data-stu-id="2205c-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2205c-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2205c-119">0x80041006</span></span> | <span data-ttu-id="2205c-120">沒有足夠的記憶體可用來開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="2205c-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2205c-121">0</span><span class="sxs-lookup"><span data-stu-id="2205c-121">0</span></span> | <span data-ttu-id="2205c-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2205c-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2205c-123">備註</span><span class="sxs-lookup"><span data-stu-id="2205c-123">Remarks</span></span>

<span data-ttu-id="2205c-124">此函數會包裝對 [IWbemClassObject：： BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2205c-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="2205c-125">可以傳遞做為引數的旗 `lEnumFlags` 標是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="2205c-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="2205c-126">您可以結合每個群組中的一個旗標與任何其他群組的任何旗標。</span><span class="sxs-lookup"><span data-stu-id="2205c-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="2205c-127">不過，來自相同群組的旗標是互斥的。</span><span class="sxs-lookup"><span data-stu-id="2205c-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="2205c-128">**群組1**</span><span class="sxs-lookup"><span data-stu-id="2205c-128">**Group 1**</span></span>

|<span data-ttu-id="2205c-129">常數</span><span class="sxs-lookup"><span data-stu-id="2205c-129">Constant</span></span>  |<span data-ttu-id="2205c-130">值</span><span class="sxs-lookup"><span data-stu-id="2205c-130">Value</span></span>  |<span data-ttu-id="2205c-131">描述</span><span class="sxs-lookup"><span data-stu-id="2205c-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="2205c-132">0x4</span><span class="sxs-lookup"><span data-stu-id="2205c-132">0x4</span></span> | <span data-ttu-id="2205c-133">包含只構成索引鍵的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="2205c-134">0x8</span><span class="sxs-lookup"><span data-stu-id="2205c-134">0x8</span></span> | <span data-ttu-id="2205c-135">包含僅為物件參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="2205c-136">**群組2**</span><span class="sxs-lookup"><span data-stu-id="2205c-136">**Group 2**</span></span>

<span data-ttu-id="2205c-137">常數</span><span class="sxs-lookup"><span data-stu-id="2205c-137">Constant</span></span>  |<span data-ttu-id="2205c-138">值</span><span class="sxs-lookup"><span data-stu-id="2205c-138">Value</span></span>  |<span data-ttu-id="2205c-139">描述</span><span class="sxs-lookup"><span data-stu-id="2205c-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="2205c-140">0x30</span><span class="sxs-lookup"><span data-stu-id="2205c-140">0x30</span></span> | <span data-ttu-id="2205c-141">僅將列舉限制為系統屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="2205c-142">0x40</span><span class="sxs-lookup"><span data-stu-id="2205c-142">0x40</span></span> | <span data-ttu-id="2205c-143">包含本機和傳播的屬性，但從列舉中排除系統屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="2205c-144">針對類別：</span><span class="sxs-lookup"><span data-stu-id="2205c-144">For classes:</span></span>

<span data-ttu-id="2205c-145">常數</span><span class="sxs-lookup"><span data-stu-id="2205c-145">Constant</span></span>  |<span data-ttu-id="2205c-146">值</span><span class="sxs-lookup"><span data-stu-id="2205c-146">Value</span></span>  |<span data-ttu-id="2205c-147">描述</span><span class="sxs-lookup"><span data-stu-id="2205c-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="2205c-148">0x100</span><span class="sxs-lookup"><span data-stu-id="2205c-148">0x100</span></span> | <span data-ttu-id="2205c-149">將列舉限制為在類別定義中覆寫的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="2205c-150">0x100</span><span class="sxs-lookup"><span data-stu-id="2205c-150">0x100</span></span> | <span data-ttu-id="2205c-151">將列舉限制為目前類別定義中所覆寫的屬性，以及在類別中定義的新屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="2205c-152">0x300</span><span class="sxs-lookup"><span data-stu-id="2205c-152">0x300</span></span> | <span data-ttu-id="2205c-153">遮罩 (而不是旗標，) 套用至 `lEnumFlags` 值以檢查是否 `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` 已設定或。</span><span class="sxs-lookup"><span data-stu-id="2205c-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2205c-154">0x10</span><span class="sxs-lookup"><span data-stu-id="2205c-154">0x10</span></span> | <span data-ttu-id="2205c-155">將列舉限制為在類別本身中定義或修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="2205c-156">0x20</span><span class="sxs-lookup"><span data-stu-id="2205c-156">0x20</span></span> | <span data-ttu-id="2205c-157">將列舉限制為繼承自基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="2205c-158">針對實例：</span><span class="sxs-lookup"><span data-stu-id="2205c-158">For instances:</span></span>

<span data-ttu-id="2205c-159">常數</span><span class="sxs-lookup"><span data-stu-id="2205c-159">Constant</span></span>  |<span data-ttu-id="2205c-160">值</span><span class="sxs-lookup"><span data-stu-id="2205c-160">Value</span></span>  |<span data-ttu-id="2205c-161">描述</span><span class="sxs-lookup"><span data-stu-id="2205c-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2205c-162">0x10</span><span class="sxs-lookup"><span data-stu-id="2205c-162">0x10</span></span> | <span data-ttu-id="2205c-163">將列舉限制為在類別本身中定義或修改的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="2205c-164">0x20</span><span class="sxs-lookup"><span data-stu-id="2205c-164">0x20</span></span> | <span data-ttu-id="2205c-165">將列舉限制為繼承自基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="2205c-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2205c-166">需求</span><span class="sxs-lookup"><span data-stu-id="2205c-166">Requirements</span></span>  

 <span data-ttu-id="2205c-167">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2205c-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2205c-168">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="2205c-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2205c-169">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2205c-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2205c-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2205c-170">See also</span></span>

- [<span data-ttu-id="2205c-171">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="2205c-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
