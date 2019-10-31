---
title: QualifierSet_GetNames 函式（非受控 API 參考）
description: QualifierSet_GetNames 函數會從物件或屬性抓取限定詞的名稱。
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
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141701"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="13332-103">QualifierSet_GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="13332-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="13332-104">抓取目前物件或屬性中可用的所有限定詞或特定限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="13332-105">語法</span><span class="sxs-lookup"><span data-stu-id="13332-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="13332-106">參數</span><span class="sxs-lookup"><span data-stu-id="13332-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="13332-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="13332-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="13332-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="13332-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="13332-109">在下列其中一個旗標或值，指定要包含在列舉中的名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="13332-110">常數</span><span class="sxs-lookup"><span data-stu-id="13332-110">Constant</span></span>  |<span data-ttu-id="13332-111">值</span><span class="sxs-lookup"><span data-stu-id="13332-111">Value</span></span>  |<span data-ttu-id="13332-112">描述</span><span class="sxs-lookup"><span data-stu-id="13332-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="13332-113">0</span><span class="sxs-lookup"><span data-stu-id="13332-113">0</span></span> | <span data-ttu-id="13332-114">傳回所有限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="13332-115">0x10</span><span class="sxs-lookup"><span data-stu-id="13332-115">0x10</span></span> | <span data-ttu-id="13332-116">只傳回目前屬性或物件的特定限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="13332-117">對於屬性：只傳回屬性的特定限定詞（包括覆寫），而不是從類別定義傳播的限定詞。</span><span class="sxs-lookup"><span data-stu-id="13332-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="13332-118">針對實例：只傳回實例特定的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="13332-119">針對類別：只傳回所要衍生之類別的特定限定詞。</span><span class="sxs-lookup"><span data-stu-id="13332-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="13332-120">0x20</span><span class="sxs-lookup"><span data-stu-id="13332-120">0x20</span></span> | <span data-ttu-id="13332-121">只傳回從另一個物件傳播的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="13332-122">對於屬性：只傳回從類別定義傳播到這個屬性的限定詞，而不是來自屬性本身的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="13332-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="13332-123">針對實例：只傳回從類別定義傳播的限定詞。</span><span class="sxs-lookup"><span data-stu-id="13332-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="13332-124">針對類別：只傳回繼承自父類別的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="13332-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="13332-125">脫銷包含所要求名稱的新 `SAFEARRAY`。</span><span class="sxs-lookup"><span data-stu-id="13332-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="13332-126">陣列可以有0個元素。</span><span class="sxs-lookup"><span data-stu-id="13332-126">The array can have 0 elements.</span></span> <span data-ttu-id="13332-127">如果發生錯誤，則不會傳回新的 `SAFEARRAY`。</span><span class="sxs-lookup"><span data-stu-id="13332-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="13332-128">傳回值</span><span class="sxs-lookup"><span data-stu-id="13332-128">Return value</span></span>

<span data-ttu-id="13332-129">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="13332-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="13332-130">常數</span><span class="sxs-lookup"><span data-stu-id="13332-130">Constant</span></span>  |<span data-ttu-id="13332-131">值</span><span class="sxs-lookup"><span data-stu-id="13332-131">Value</span></span>  |<span data-ttu-id="13332-132">描述</span><span class="sxs-lookup"><span data-stu-id="13332-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="13332-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="13332-133">0x80041008</span></span> | <span data-ttu-id="13332-134">參數無效。</span><span class="sxs-lookup"><span data-stu-id="13332-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="13332-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="13332-135">0x80041006</span></span> | <span data-ttu-id="13332-136">沒有足夠的記憶體可以開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="13332-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="13332-137">0</span><span class="sxs-lookup"><span data-stu-id="13332-137">0</span></span> | <span data-ttu-id="13332-138">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="13332-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="13332-139">備註</span><span class="sxs-lookup"><span data-stu-id="13332-139">Remarks</span></span>

<span data-ttu-id="13332-140">此函式會包裝對[IWbemQualifierSet：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="13332-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="13332-141">抓取限定詞名稱之後，您就可以藉由呼叫[QualifierSet_Get](qualifierset-get.md)函數，依名稱存取每個限定詞。</span><span class="sxs-lookup"><span data-stu-id="13332-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="13332-142">如果指定的物件沒有任何限定詞，則不會發生錯誤，因此，`pstrNames` 中的字串數目可以是0，即使函式傳回 `WBEM_S_NO_ERROR`也一樣。</span><span class="sxs-lookup"><span data-stu-id="13332-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="13332-143">需求</span><span class="sxs-lookup"><span data-stu-id="13332-143">Requirements</span></span>

<span data-ttu-id="13332-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13332-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="13332-145">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="13332-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="13332-146">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="13332-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="13332-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="13332-147">See also</span></span>

- [<span data-ttu-id="13332-148">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="13332-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
