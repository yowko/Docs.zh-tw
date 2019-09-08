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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266462a5393c8e26aa2bc3f2ec8ab72d4410a431
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798289"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="169e8-103">QualifierSet_GetNames 函式</span><span class="sxs-lookup"><span data-stu-id="169e8-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="169e8-104">抓取目前物件或屬性中可用的所有限定詞或特定限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="169e8-105">語法</span><span class="sxs-lookup"><span data-stu-id="169e8-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="169e8-106">參數</span><span class="sxs-lookup"><span data-stu-id="169e8-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="169e8-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="169e8-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="169e8-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="169e8-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="169e8-109">在下列其中一個旗標或值，指定要包含在列舉中的名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="169e8-110">常數</span><span class="sxs-lookup"><span data-stu-id="169e8-110">Constant</span></span>  |<span data-ttu-id="169e8-111">值</span><span class="sxs-lookup"><span data-stu-id="169e8-111">Value</span></span>  |<span data-ttu-id="169e8-112">描述</span><span class="sxs-lookup"><span data-stu-id="169e8-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="169e8-113">0</span><span class="sxs-lookup"><span data-stu-id="169e8-113">0</span></span> | <span data-ttu-id="169e8-114">傳回所有限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="169e8-115">0x10</span><span class="sxs-lookup"><span data-stu-id="169e8-115">0x10</span></span> | <span data-ttu-id="169e8-116">只傳回目前屬性或物件的特定限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="169e8-117">若為屬性：只傳回屬性的特定限定詞（包括覆寫），而不是從類別定義傳播的限定詞。</span><span class="sxs-lookup"><span data-stu-id="169e8-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="169e8-118">針對實例：只傳回實例特有的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="169e8-119">若為類別：只傳回衍生的類別特定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="169e8-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="169e8-120">0x20</span><span class="sxs-lookup"><span data-stu-id="169e8-120">0x20</span></span> | <span data-ttu-id="169e8-121">只傳回從另一個物件傳播的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="169e8-122">若為屬性：只傳回從類別定義傳播到這個屬性的限定詞，而不是屬性本身的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="169e8-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="169e8-123">針對實例：只傳回從類別定義傳播的限定詞。</span><span class="sxs-lookup"><span data-stu-id="169e8-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="169e8-124">若為類別：只傳回繼承自父類別的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="169e8-125">脫銷新`SAFEARRAY`的，其中包含要求的名稱。</span><span class="sxs-lookup"><span data-stu-id="169e8-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="169e8-126">陣列可以有0個元素。</span><span class="sxs-lookup"><span data-stu-id="169e8-126">The array can have 0 elements.</span></span> <span data-ttu-id="169e8-127">如果發生錯誤，則不會`SAFEARRAY`傳回新的。</span><span class="sxs-lookup"><span data-stu-id="169e8-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="169e8-128">傳回值</span><span class="sxs-lookup"><span data-stu-id="169e8-128">Return value</span></span>

<span data-ttu-id="169e8-129">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="169e8-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="169e8-130">常數</span><span class="sxs-lookup"><span data-stu-id="169e8-130">Constant</span></span>  |<span data-ttu-id="169e8-131">值</span><span class="sxs-lookup"><span data-stu-id="169e8-131">Value</span></span>  |<span data-ttu-id="169e8-132">描述</span><span class="sxs-lookup"><span data-stu-id="169e8-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="169e8-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="169e8-133">0x80041008</span></span> | <span data-ttu-id="169e8-134">參數無效。</span><span class="sxs-lookup"><span data-stu-id="169e8-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="169e8-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="169e8-135">0x80041006</span></span> | <span data-ttu-id="169e8-136">沒有足夠的記憶體可以開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="169e8-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="169e8-137">0</span><span class="sxs-lookup"><span data-stu-id="169e8-137">0</span></span> | <span data-ttu-id="169e8-138">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="169e8-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="169e8-139">備註</span><span class="sxs-lookup"><span data-stu-id="169e8-139">Remarks</span></span>

<span data-ttu-id="169e8-140">此函式會包裝對[IWbemQualifierSet：： GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="169e8-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="169e8-141">抓取限定詞名稱之後，您就可以藉由呼叫[QualifierSet_Get](qualifierset-get.md)函數，依名稱存取每個限定詞。</span><span class="sxs-lookup"><span data-stu-id="169e8-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="169e8-142">如果指定的物件沒有任何限定詞，就不會發生錯誤，因此`pstrNames` on 傳回的字串數目可以是0，即使函式傳回也一樣。 `WBEM_S_NO_ERROR`</span><span class="sxs-lookup"><span data-stu-id="169e8-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="169e8-143">需求</span><span class="sxs-lookup"><span data-stu-id="169e8-143">Requirements</span></span>

<span data-ttu-id="169e8-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="169e8-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="169e8-145">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="169e8-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="169e8-146">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="169e8-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="169e8-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="169e8-147">See also</span></span>

- [<span data-ttu-id="169e8-148">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="169e8-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
