---
title: QualifierSet_Put 函式 （Unmanaged API 參考）
description: QualifierSet_Put 函式會寫入具名的辨識符號和其值。
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
ms.openlocfilehash: 7b2e1b08d1091e482c6b02fe015a58219ff80768
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517557"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="ef5b8-103">QualifierSet_Put 函式</span><span class="sxs-lookup"><span data-stu-id="ef5b8-103">QualifierSet_Put function</span></span>
<span data-ttu-id="ef5b8-104">寫入具名限定詞與值。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="ef5b8-105">新限定詞會覆寫先前的相同名稱的值。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="ef5b8-106">如果不存在的辨識符號，它會建立它。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ef5b8-107">語法</span><span class="sxs-lookup"><span data-stu-id="ef5b8-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="ef5b8-108">參數</span><span class="sxs-lookup"><span data-stu-id="ef5b8-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="ef5b8-109">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="ef5b8-110">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="ef5b8-111">[in]要寫入的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="ef5b8-112">`pVal` [in]有效的指標`VARIANT`，其中包含要寫入的限定詞。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="ef5b8-113">此參數不得為`null`。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="ef5b8-114">`lFlavor` [in]其中一個的所需的限定詞標註，這個辨識符號會定義下列常數。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="ef5b8-115">預設值是`WBEM_FLAVOR_OVERRIDABLE`(0)。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="ef5b8-116">常數</span><span class="sxs-lookup"><span data-stu-id="ef5b8-116">Constant</span></span>  |<span data-ttu-id="ef5b8-117">值</span><span class="sxs-lookup"><span data-stu-id="ef5b8-117">Value</span></span>  |<span data-ttu-id="ef5b8-118">描述</span><span class="sxs-lookup"><span data-stu-id="ef5b8-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="ef5b8-119">0</span><span class="sxs-lookup"><span data-stu-id="ef5b8-119">0</span></span> | <span data-ttu-id="ef5b8-120">限定詞可以覆寫於衍生的類別或執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="ef5b8-121">**這是預設值。**</span><span class="sxs-lookup"><span data-stu-id="ef5b8-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="ef5b8-122">1</span><span class="sxs-lookup"><span data-stu-id="ef5b8-122">1</span></span> | <span data-ttu-id="ef5b8-123">限定詞會傳播到執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="ef5b8-124">2</span><span class="sxs-lookup"><span data-stu-id="ef5b8-124">2</span></span> | <span data-ttu-id="ef5b8-125">限定詞會傳播到衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="ef5b8-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="ef5b8-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="ef5b8-127">0x10</span><span class="sxs-lookup"><span data-stu-id="ef5b8-127">0x10</span></span> | <span data-ttu-id="ef5b8-128">無法在衍生類別或執行個體中覆寫限定詞。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="ef5b8-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="ef5b8-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="ef5b8-130">0x80</span><span class="sxs-lookup"><span data-stu-id="ef5b8-130">0x80</span></span> | <span data-ttu-id="ef5b8-131">限定詞會進行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="ef5b8-132">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef5b8-132">Return value</span></span>

<span data-ttu-id="ef5b8-133">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="ef5b8-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ef5b8-134">常數</span><span class="sxs-lookup"><span data-stu-id="ef5b8-134">Constant</span></span>  |<span data-ttu-id="ef5b8-135">值</span><span class="sxs-lookup"><span data-stu-id="ef5b8-135">Value</span></span>  |<span data-ttu-id="ef5b8-136">描述</span><span class="sxs-lookup"><span data-stu-id="ef5b8-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="ef5b8-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="ef5b8-137">0x8004101f</span></span> | <span data-ttu-id="ef5b8-138">發生不合法嘗試指定**金鑰**不得為索引鍵屬性上的限定詞。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="ef5b8-139">指定索引鍵 om c; as 物件的定義，無法變更每個執行個體為基礎。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ef5b8-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ef5b8-140">0x80041008</span></span> | <span data-ttu-id="ef5b8-141">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="ef5b8-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="ef5b8-142">0x80041029</span></span> | <span data-ttu-id="ef5b8-143">`pVal`參數不是合法的限定詞型別。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="ef5b8-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="ef5b8-144">0x8004101a</span></span> | <span data-ttu-id="ef5b8-145">不可能呼叫`QualifierSet_Put`方法在限定詞上的因為主控物件不允許覆寫。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ef5b8-146">0</span><span class="sxs-lookup"><span data-stu-id="ef5b8-146">0</span></span> | <span data-ttu-id="ef5b8-147">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ef5b8-148">備註</span><span class="sxs-lookup"><span data-stu-id="ef5b8-148">Remarks</span></span>

<span data-ttu-id="ef5b8-149">此函式會包裝在呼叫[IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put)方法。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-149">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef5b8-150">需求</span><span class="sxs-lookup"><span data-stu-id="ef5b8-150">Requirements</span></span>  
 <span data-ttu-id="ef5b8-151">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef5b8-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef5b8-152">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ef5b8-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ef5b8-153">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef5b8-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5b8-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef5b8-154">See also</span></span>  
[<span data-ttu-id="ef5b8-155">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="ef5b8-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
