---
title: QualifierSet_BeginEnumeration 函式 （Unmanaged API 參考）
description: QualifierSet_BeginEnumeration 函式會重設物件限定詞的列舉值。
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
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597232"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="55205-103">QualifierSet_BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="55205-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="55205-104">將物件限定詞的列舉程式重設為列舉開始時的狀態。</span><span class="sxs-lookup"><span data-stu-id="55205-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="55205-105">語法</span><span class="sxs-lookup"><span data-stu-id="55205-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="55205-106">參數</span><span class="sxs-lookup"><span data-stu-id="55205-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="55205-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="55205-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="55205-108">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="55205-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="55205-109">[in]中所述的旗標的位元組合[備註](#remarks)區段，指定要包含在列舉中的限定詞。</span><span class="sxs-lookup"><span data-stu-id="55205-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="55205-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="55205-110">Return value</span></span>

<span data-ttu-id="55205-111">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="55205-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="55205-112">常數</span><span class="sxs-lookup"><span data-stu-id="55205-112">Constant</span></span>  |<span data-ttu-id="55205-113">值</span><span class="sxs-lookup"><span data-stu-id="55205-113">Value</span></span>  |<span data-ttu-id="55205-114">描述</span><span class="sxs-lookup"><span data-stu-id="55205-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="55205-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="55205-115">0x80041008</span></span> | <span data-ttu-id="55205-116">`lFlags` 參數無效。</span><span class="sxs-lookup"><span data-stu-id="55205-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="55205-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="55205-117">0x8004101d</span></span> | <span data-ttu-id="55205-118">第二次呼叫`QualifierSet_BeginEnumeration`而不需要的介入呼叫進行[ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="55205-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="55205-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="55205-119">0x80041006</span></span> | <span data-ttu-id="55205-120">沒有足夠的記憶體可供開始新的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="55205-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="55205-121">0</span><span class="sxs-lookup"><span data-stu-id="55205-121">0</span></span> | <span data-ttu-id="55205-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="55205-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="55205-123">備註</span><span class="sxs-lookup"><span data-stu-id="55205-123">Remarks</span></span>

<span data-ttu-id="55205-124">此函式會包裝在呼叫[IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration)方法。</span><span class="sxs-lookup"><span data-stu-id="55205-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="55205-125">若要列舉所有的物件上的限定詞，必須呼叫這個方法的第一個呼叫之前[QualifierSet_Next](qualifierset-next.md)。</span><span class="sxs-lookup"><span data-stu-id="55205-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="55205-126">限定詞會列舉在其中的順序保證會針對指定的列舉型別而異。</span><span class="sxs-lookup"><span data-stu-id="55205-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="55205-127">可以做為傳遞的旗標`lEnumFlags`中所定義的引數*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。</span><span class="sxs-lookup"><span data-stu-id="55205-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="55205-128">常數</span><span class="sxs-lookup"><span data-stu-id="55205-128">Constant</span></span>  |<span data-ttu-id="55205-129">值</span><span class="sxs-lookup"><span data-stu-id="55205-129">Value</span></span>  |<span data-ttu-id="55205-130">描述</span><span class="sxs-lookup"><span data-stu-id="55205-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="55205-131">0</span><span class="sxs-lookup"><span data-stu-id="55205-131">0</span></span> | <span data-ttu-id="55205-132">傳回所有限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="55205-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="55205-133">0x10</span><span class="sxs-lookup"><span data-stu-id="55205-133">0x10</span></span> | <span data-ttu-id="55205-134">傳回目前的屬性或物件特定限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="55205-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="55205-135">屬性：傳回只特有的屬性 （包括覆寫） 限定詞，並不會傳播從類別定義的限定詞。</span><span class="sxs-lookup"><span data-stu-id="55205-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="55205-136">執行個體：傳回只有特定執行個體的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="55205-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="55205-137">類別：傳回特定只限定詞所衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="55205-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="55205-138">0x20</span><span class="sxs-lookup"><span data-stu-id="55205-138">0x20</span></span> | <span data-ttu-id="55205-139">傳回的傳播的限定詞的名稱，從另一個物件。</span><span class="sxs-lookup"><span data-stu-id="55205-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="55205-140">屬性：傳回只限定詞傳播至這個屬性從類別定義中，而不從本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="55205-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="55205-141">執行個體：傳回的只有這些限定詞傳播，從類別定義。</span><span class="sxs-lookup"><span data-stu-id="55205-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="55205-142">類別：傳回繼承自父類別的只有這些限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="55205-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="55205-143">需求</span><span class="sxs-lookup"><span data-stu-id="55205-143">Requirements</span></span>

<span data-ttu-id="55205-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55205-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="55205-145">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="55205-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="55205-146">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="55205-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="55205-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55205-147">See also</span></span>

- [<span data-ttu-id="55205-148">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="55205-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)