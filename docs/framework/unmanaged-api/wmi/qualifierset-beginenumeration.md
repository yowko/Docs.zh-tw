---
title: QualifierSet_BeginEnumeration 函式（非受控 API 參考）
description: QualifierSet_BeginEnumeration 函數會重設物件的限定詞枚舉器。
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798342"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="f7402-103">QualifierSet_BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="f7402-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="f7402-104">將物件限定詞的列舉程式重設為列舉開始時的狀態。</span><span class="sxs-lookup"><span data-stu-id="f7402-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f7402-105">語法</span><span class="sxs-lookup"><span data-stu-id="f7402-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="f7402-106">參數</span><span class="sxs-lookup"><span data-stu-id="f7402-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="f7402-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="f7402-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="f7402-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="f7402-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="f7402-109">在在 [[備註](#remarks)] 區段中所描述的旗標或值的位元組合，指定要包含在列舉中的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f7402-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f7402-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7402-110">Return value</span></span>

<span data-ttu-id="f7402-111">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f7402-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f7402-112">常數</span><span class="sxs-lookup"><span data-stu-id="f7402-112">Constant</span></span>  |<span data-ttu-id="f7402-113">值</span><span class="sxs-lookup"><span data-stu-id="f7402-113">Value</span></span>  |<span data-ttu-id="f7402-114">描述</span><span class="sxs-lookup"><span data-stu-id="f7402-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f7402-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f7402-115">0x80041008</span></span> | <span data-ttu-id="f7402-116">`lFlags` 參數無效。</span><span class="sxs-lookup"><span data-stu-id="f7402-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="f7402-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f7402-117">0x8004101d</span></span> | <span data-ttu-id="f7402-118">第二次呼叫`QualifierSet_BeginEnumeration`時，不需要介入的[`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="f7402-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f7402-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f7402-119">0x80041006</span></span> | <span data-ttu-id="f7402-120">沒有足夠的記憶體可以開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="f7402-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f7402-121">0</span><span class="sxs-lookup"><span data-stu-id="f7402-121">0</span></span> | <span data-ttu-id="f7402-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f7402-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f7402-123">備註</span><span class="sxs-lookup"><span data-stu-id="f7402-123">Remarks</span></span>

<span data-ttu-id="f7402-124">此函式會包裝對[IWbemQualifierSet：： BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f7402-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="f7402-125">若要列舉物件上的所有限定詞，必須在第一次呼叫[QualifierSet_Next](qualifierset-next.md)之前，呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f7402-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="f7402-126">辨識限定詞的順序，保證對指定的列舉而言是不變的。</span><span class="sxs-lookup"><span data-stu-id="f7402-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="f7402-127">可當做`lEnumFlags`引數傳遞的旗標會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。</span><span class="sxs-lookup"><span data-stu-id="f7402-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="f7402-128">常數</span><span class="sxs-lookup"><span data-stu-id="f7402-128">Constant</span></span>  |<span data-ttu-id="f7402-129">值</span><span class="sxs-lookup"><span data-stu-id="f7402-129">Value</span></span>  |<span data-ttu-id="f7402-130">描述</span><span class="sxs-lookup"><span data-stu-id="f7402-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="f7402-131">0</span><span class="sxs-lookup"><span data-stu-id="f7402-131">0</span></span> | <span data-ttu-id="f7402-132">傳回所有限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7402-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="f7402-133">0x10</span><span class="sxs-lookup"><span data-stu-id="f7402-133">0x10</span></span> | <span data-ttu-id="f7402-134">只傳回目前屬性或物件的特定限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="f7402-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="f7402-135">若為屬性：只傳回屬性的特定限定詞（包括覆寫），而不是從類別定義傳播的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f7402-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="f7402-136">針對實例：只傳回實例特有的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="f7402-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="f7402-137">若為類別：只傳回衍生的類別特定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f7402-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="f7402-138">0x20</span><span class="sxs-lookup"><span data-stu-id="f7402-138">0x20</span></span> | <span data-ttu-id="f7402-139">只傳回從另一個物件傳播的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="f7402-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="f7402-140">若為屬性：只傳回從類別定義傳播到這個屬性的限定詞，而不是屬性本身的辨識符號。</span><span class="sxs-lookup"><span data-stu-id="f7402-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="f7402-141">針對實例：只傳回從類別定義傳播的限定詞。</span><span class="sxs-lookup"><span data-stu-id="f7402-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="f7402-142">若為類別：只傳回繼承自父類別的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="f7402-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="f7402-143">需求</span><span class="sxs-lookup"><span data-stu-id="f7402-143">Requirements</span></span>

<span data-ttu-id="f7402-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7402-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f7402-145">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f7402-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="f7402-146">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f7402-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f7402-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7402-147">See also</span></span>

- [<span data-ttu-id="f7402-148">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="f7402-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
