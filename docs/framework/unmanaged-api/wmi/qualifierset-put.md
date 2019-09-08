---
title: QualifierSet_Put 函式（非受控 API 參考）
description: QualifierSet_Put 函數會寫入已命名的限定詞和其值。
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798266"
---
# <a name="qualifierset_put-function"></a><span data-ttu-id="18ae8-103">QualifierSet_Put 函式</span><span class="sxs-lookup"><span data-stu-id="18ae8-103">QualifierSet_Put function</span></span>

<span data-ttu-id="18ae8-104">寫入具名限定詞與值。</span><span class="sxs-lookup"><span data-stu-id="18ae8-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="18ae8-105">新的限定詞會覆寫相同名稱的先前值。</span><span class="sxs-lookup"><span data-stu-id="18ae8-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="18ae8-106">如果辨識符號不存在，則會加以建立。</span><span class="sxs-lookup"><span data-stu-id="18ae8-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="18ae8-107">語法</span><span class="sxs-lookup"><span data-stu-id="18ae8-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="18ae8-108">參數</span><span class="sxs-lookup"><span data-stu-id="18ae8-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="18ae8-109">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="18ae8-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="18ae8-110">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="18ae8-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="18ae8-111">在要寫入的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="18ae8-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="18ae8-112">在有效`VARIANT`的指標，其中包含要寫入的限定詞。</span><span class="sxs-lookup"><span data-stu-id="18ae8-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="18ae8-113">這個參數不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="18ae8-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="18ae8-114">在下列其中一個常數，定義此辨識符號的所需限定詞類別。</span><span class="sxs-lookup"><span data-stu-id="18ae8-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="18ae8-115">預設值為`WBEM_FLAVOR_OVERRIDABLE` （0）。</span><span class="sxs-lookup"><span data-stu-id="18ae8-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="18ae8-116">常數</span><span class="sxs-lookup"><span data-stu-id="18ae8-116">Constant</span></span>  |<span data-ttu-id="18ae8-117">值</span><span class="sxs-lookup"><span data-stu-id="18ae8-117">Value</span></span>  |<span data-ttu-id="18ae8-118">描述</span><span class="sxs-lookup"><span data-stu-id="18ae8-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="18ae8-119">0</span><span class="sxs-lookup"><span data-stu-id="18ae8-119">0</span></span> | <span data-ttu-id="18ae8-120">限定詞可以在衍生類別或實例中覆寫。</span><span class="sxs-lookup"><span data-stu-id="18ae8-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="18ae8-121">**這是預設值。**</span><span class="sxs-lookup"><span data-stu-id="18ae8-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="18ae8-122">1</span><span class="sxs-lookup"><span data-stu-id="18ae8-122">1</span></span> | <span data-ttu-id="18ae8-123">限定詞會傳播到執行個體。</span><span class="sxs-lookup"><span data-stu-id="18ae8-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="18ae8-124">2</span><span class="sxs-lookup"><span data-stu-id="18ae8-124">2</span></span> | <span data-ttu-id="18ae8-125">限定詞會傳播到衍生類別。</span><span class="sxs-lookup"><span data-stu-id="18ae8-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="18ae8-126">0x10</span><span class="sxs-lookup"><span data-stu-id="18ae8-126">0x10</span></span> | <span data-ttu-id="18ae8-127">無法在衍生類別或執行個體中覆寫限定詞。</span><span class="sxs-lookup"><span data-stu-id="18ae8-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="18ae8-128">0x80</span><span class="sxs-lookup"><span data-stu-id="18ae8-128">0x80</span></span> | <span data-ttu-id="18ae8-129">辨識符號已當地語系化。</span><span class="sxs-lookup"><span data-stu-id="18ae8-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="18ae8-130">傳回值</span><span class="sxs-lookup"><span data-stu-id="18ae8-130">Return value</span></span>

<span data-ttu-id="18ae8-131">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="18ae8-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="18ae8-132">常數</span><span class="sxs-lookup"><span data-stu-id="18ae8-132">Constant</span></span>  |<span data-ttu-id="18ae8-133">值</span><span class="sxs-lookup"><span data-stu-id="18ae8-133">Value</span></span>  |<span data-ttu-id="18ae8-134">說明</span><span class="sxs-lookup"><span data-stu-id="18ae8-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="18ae8-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="18ae8-135">0x8004101f</span></span> | <span data-ttu-id="18ae8-136">在無法做為索引鍵的屬性上，指定索引**鍵**辨識符號的嘗試不合法。</span><span class="sxs-lookup"><span data-stu-id="18ae8-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="18ae8-137">索引鍵是在物件的類別定義中指定，而且無法針對每個實例進行變更。</span><span class="sxs-lookup"><span data-stu-id="18ae8-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="18ae8-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="18ae8-138">0x80041008</span></span> | <span data-ttu-id="18ae8-139">參數無效。</span><span class="sxs-lookup"><span data-stu-id="18ae8-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="18ae8-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="18ae8-140">0x80041029</span></span> | <span data-ttu-id="18ae8-141">`pVal`參數不是合法的限定詞類型。</span><span class="sxs-lookup"><span data-stu-id="18ae8-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="18ae8-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="18ae8-142">0x8004101a</span></span> | <span data-ttu-id="18ae8-143">因為主控物件不允許覆寫`QualifierSet_Put` ，所以無法在辨識符號上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="18ae8-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="18ae8-144">0</span><span class="sxs-lookup"><span data-stu-id="18ae8-144">0</span></span> | <span data-ttu-id="18ae8-145">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="18ae8-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="18ae8-146">備註</span><span class="sxs-lookup"><span data-stu-id="18ae8-146">Remarks</span></span>

<span data-ttu-id="18ae8-147">此函式會包裝對[IWbemQualifierSet：:P](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put)的工作方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="18ae8-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18ae8-148">需求</span><span class="sxs-lookup"><span data-stu-id="18ae8-148">Requirements</span></span>

<span data-ttu-id="18ae8-149">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18ae8-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="18ae8-150">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="18ae8-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="18ae8-151">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="18ae8-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="18ae8-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18ae8-152">See also</span></span>

- [<span data-ttu-id="18ae8-153">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="18ae8-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
