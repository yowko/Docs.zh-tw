---
title: QualifierSet_Next函數（非託管 API 引用）
description: QualifierSet_Next函數在枚舉中檢索下一個限定詞。
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
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174871"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="5e708-103">QualifierSet_Next 函式</span><span class="sxs-lookup"><span data-stu-id="5e708-103">QualifierSet_Next function</span></span>
<span data-ttu-id="5e708-104">擷取透過呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式而開始之列舉中的下一個限定詞。</span><span class="sxs-lookup"><span data-stu-id="5e708-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5e708-105">語法</span><span class="sxs-lookup"><span data-stu-id="5e708-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="5e708-106">參數</span><span class="sxs-lookup"><span data-stu-id="5e708-106">Parameters</span></span>

<span data-ttu-id="5e708-107">`vFunc`[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="5e708-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="5e708-108">`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。</span><span class="sxs-lookup"><span data-stu-id="5e708-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="5e708-109">`lFlags`[在]保留。</span><span class="sxs-lookup"><span data-stu-id="5e708-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="5e708-110">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="5e708-110">This parameter must be 0.</span></span>

<span data-ttu-id="5e708-111">`pstrName`[出]限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e708-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="5e708-112">如果`null`忽略 此 參數，則忽略此參數。否則，`pstrName`不應指向有效`BSTR`或發生記憶體洩漏。</span><span class="sxs-lookup"><span data-stu-id="5e708-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="5e708-113">如果不是 null，則函數在返回`BSTR``WBEM_S_NO_ERROR`時始終分配一個新的。</span><span class="sxs-lookup"><span data-stu-id="5e708-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="5e708-114">`pVal`[出]成功時，限定詞的值。</span><span class="sxs-lookup"><span data-stu-id="5e708-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="5e708-115">如果函數失敗，`VARIANT`則 不修改`pVal`指向 的 。</span><span class="sxs-lookup"><span data-stu-id="5e708-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="5e708-116">如果此參數為`null`，則忽略該參數。</span><span class="sxs-lookup"><span data-stu-id="5e708-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="5e708-117">`plFlavor`[出]指向接收限定詞味道的 LONG 的指標。</span><span class="sxs-lookup"><span data-stu-id="5e708-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="5e708-118">如果不需要風味資訊，則此參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="5e708-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5e708-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e708-119">Return value</span></span>

<span data-ttu-id="5e708-120">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="5e708-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5e708-121">持續性</span><span class="sxs-lookup"><span data-stu-id="5e708-121">Constant</span></span>  |<span data-ttu-id="5e708-122">值</span><span class="sxs-lookup"><span data-stu-id="5e708-122">Value</span></span>  |<span data-ttu-id="5e708-123">描述</span><span class="sxs-lookup"><span data-stu-id="5e708-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5e708-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5e708-124">0x80041008</span></span> | <span data-ttu-id="5e708-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="5e708-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="5e708-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="5e708-126">0x8004101d</span></span> | <span data-ttu-id="5e708-127">呼叫者未呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="5e708-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5e708-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5e708-128">0x80041006</span></span> | <span data-ttu-id="5e708-129">沒有足夠的記憶體可用於開始新的枚舉。</span><span class="sxs-lookup"><span data-stu-id="5e708-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="5e708-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="5e708-130">0x40005</span></span> | <span data-ttu-id="5e708-131">枚舉中不再保留限定詞。</span><span class="sxs-lookup"><span data-stu-id="5e708-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5e708-132">0</span><span class="sxs-lookup"><span data-stu-id="5e708-132">0</span></span> | <span data-ttu-id="5e708-133">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5e708-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5e708-134">備註</span><span class="sxs-lookup"><span data-stu-id="5e708-134">Remarks</span></span>

<span data-ttu-id="5e708-135">此函數包裝對[IWbem 限定詞集的調用：：下一個](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)方法。</span><span class="sxs-lookup"><span data-stu-id="5e708-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="5e708-136">重複調用函數`QualifierSet_Next`以枚舉所有限定詞，直到函數返回`WBEM_S_NO_MORE_DATA`。</span><span class="sxs-lookup"><span data-stu-id="5e708-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="5e708-137">要提前終止枚舉，請調用[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函數。</span><span class="sxs-lookup"><span data-stu-id="5e708-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="5e708-138">枚舉期間返回的限定詞的順序未定義。</span><span class="sxs-lookup"><span data-stu-id="5e708-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e708-139">需求</span><span class="sxs-lookup"><span data-stu-id="5e708-139">Requirements</span></span>  
 <span data-ttu-id="5e708-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e708-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e708-141">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5e708-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5e708-142">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e708-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e708-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e708-143">See also</span></span>

- [<span data-ttu-id="5e708-144">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="5e708-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
