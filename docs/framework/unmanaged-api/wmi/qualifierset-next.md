---
title: 'QualifierSet_Next 函式 (非受控 API 參考) '
description: QualifierSet_Next 函式會捕獲列舉中的下一個限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721123"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="e6f34-103">QualifierSet_Next 函式</span><span class="sxs-lookup"><span data-stu-id="e6f34-103">QualifierSet_Next function</span></span>

<span data-ttu-id="e6f34-104">擷取透過呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式而開始之列舉中的下一個限定詞。</span><span class="sxs-lookup"><span data-stu-id="e6f34-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e6f34-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6f34-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="e6f34-106">參數</span><span class="sxs-lookup"><span data-stu-id="e6f34-106">Parameters</span></span>

<span data-ttu-id="e6f34-107">`vFunc` 在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="e6f34-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="e6f34-108">`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="e6f34-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="e6f34-109">`lFlags` 在保留。</span><span class="sxs-lookup"><span data-stu-id="e6f34-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="e6f34-110">此參數必須為0。</span><span class="sxs-lookup"><span data-stu-id="e6f34-110">This parameter must be 0.</span></span>

<span data-ttu-id="e6f34-111">`pstrName` 擴展限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f34-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="e6f34-112">如果為 `null` ，則會忽略這個參數，否則 `pstrName` 不應指向有效 `BSTR` 或記憶體流失的情況。</span><span class="sxs-lookup"><span data-stu-id="e6f34-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="e6f34-113">如果不是 null，則函式會在傳回時一律配置新的 `BSTR` `WBEM_S_NO_ERROR` 。</span><span class="sxs-lookup"><span data-stu-id="e6f34-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="e6f34-114">`pVal` 擴展成功時，辨識符號的值。</span><span class="sxs-lookup"><span data-stu-id="e6f34-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="e6f34-115">如果函式失敗，則 `VARIANT` `pVal` 不會修改指向的。</span><span class="sxs-lookup"><span data-stu-id="e6f34-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="e6f34-116">如果此參數為 `null` ，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="e6f34-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="e6f34-117">`plFlavor` 擴展收到限定詞類別的 LONG 指標。</span><span class="sxs-lookup"><span data-stu-id="e6f34-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="e6f34-118">如果不需要類別資訊，這個參數可以是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="e6f34-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6f34-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6f34-119">Return value</span></span>

<span data-ttu-id="e6f34-120">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="e6f34-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e6f34-121">常數</span><span class="sxs-lookup"><span data-stu-id="e6f34-121">Constant</span></span>  |<span data-ttu-id="e6f34-122">值</span><span class="sxs-lookup"><span data-stu-id="e6f34-122">Value</span></span>  |<span data-ttu-id="e6f34-123">描述</span><span class="sxs-lookup"><span data-stu-id="e6f34-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e6f34-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e6f34-124">0x80041008</span></span> | <span data-ttu-id="e6f34-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="e6f34-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="e6f34-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="e6f34-126">0x8004101d</span></span> | <span data-ttu-id="e6f34-127">呼叫端未呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f34-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e6f34-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e6f34-128">0x80041006</span></span> | <span data-ttu-id="e6f34-129">沒有足夠的記憶體可用來開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="e6f34-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="e6f34-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="e6f34-130">0x40005</span></span> | <span data-ttu-id="e6f34-131">列舉中沒有剩餘的限定詞。</span><span class="sxs-lookup"><span data-stu-id="e6f34-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e6f34-132">0</span><span class="sxs-lookup"><span data-stu-id="e6f34-132">0</span></span> | <span data-ttu-id="e6f34-133">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e6f34-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e6f34-134">備註</span><span class="sxs-lookup"><span data-stu-id="e6f34-134">Remarks</span></span>

<span data-ttu-id="e6f34-135">此函數會包裝對 [IWbemQualifierSet：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e6f34-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="e6f34-136">您可以重複呼叫函式 `QualifierSet_Next` 來列舉所有的限定詞，直到函數傳回為止 `WBEM_S_NO_MORE_DATA` 。</span><span class="sxs-lookup"><span data-stu-id="e6f34-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="e6f34-137">若要提早終止列舉，請呼叫 [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="e6f34-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="e6f34-138">列舉期間傳回的限定詞順序未定義。</span><span class="sxs-lookup"><span data-stu-id="e6f34-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6f34-139">需求</span><span class="sxs-lookup"><span data-stu-id="e6f34-139">Requirements</span></span>  

 <span data-ttu-id="e6f34-140">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f34-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f34-141">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="e6f34-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e6f34-142">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f34-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f34-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f34-143">See also</span></span>

- [<span data-ttu-id="e6f34-144">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="e6f34-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
