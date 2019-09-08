---
title: QualifierSet_Next 函式（非受控 API 參考）
description: QualifierSet_Next 函數會抓取列舉中的下一個辨識符號。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97a19f236b87a7f4c5b2014aca6ee4abd338c63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798276"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="36c39-103">QualifierSet_Next 函式</span><span class="sxs-lookup"><span data-stu-id="36c39-103">QualifierSet_Next function</span></span>
<span data-ttu-id="36c39-104">擷取透過呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式而開始之列舉中的下一個限定詞。</span><span class="sxs-lookup"><span data-stu-id="36c39-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="36c39-105">語法</span><span class="sxs-lookup"><span data-stu-id="36c39-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="36c39-106">參數</span><span class="sxs-lookup"><span data-stu-id="36c39-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="36c39-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="36c39-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="36c39-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="36c39-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="36c39-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="36c39-109">[in] Reserved.</span></span> <span data-ttu-id="36c39-110">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="36c39-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="36c39-111">脫銷辨識符號的名稱。</span><span class="sxs-lookup"><span data-stu-id="36c39-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="36c39-112">如果`null`為，則會忽略這個參數， `pstrName`否則不應指向有效`BSTR`的或發生記憶體流失的情況。</span><span class="sxs-lookup"><span data-stu-id="36c39-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="36c39-113">如果不是 null，函式`BSTR` `WBEM_S_NO_ERROR`會在傳回時一律配置新的。</span><span class="sxs-lookup"><span data-stu-id="36c39-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="36c39-114">脫銷如果成功，則為限定詞的值。</span><span class="sxs-lookup"><span data-stu-id="36c39-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="36c39-115">如果函式失敗，則`VARIANT`不`pVal`會修改所指向的。</span><span class="sxs-lookup"><span data-stu-id="36c39-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="36c39-116">如果此參數為`null`，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="36c39-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="36c39-117">脫銷接收限定詞類別的長整數指標。</span><span class="sxs-lookup"><span data-stu-id="36c39-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="36c39-118">如果不需要類別資訊，此參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="36c39-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="36c39-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="36c39-119">Return value</span></span>

<span data-ttu-id="36c39-120">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="36c39-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="36c39-121">常數</span><span class="sxs-lookup"><span data-stu-id="36c39-121">Constant</span></span>  |<span data-ttu-id="36c39-122">值</span><span class="sxs-lookup"><span data-stu-id="36c39-122">Value</span></span>  |<span data-ttu-id="36c39-123">描述</span><span class="sxs-lookup"><span data-stu-id="36c39-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="36c39-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="36c39-124">0x80041008</span></span> | <span data-ttu-id="36c39-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="36c39-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="36c39-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="36c39-126">0x8004101d</span></span> | <span data-ttu-id="36c39-127">呼叫端未呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="36c39-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="36c39-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="36c39-128">0x80041006</span></span> | <span data-ttu-id="36c39-129">沒有足夠的記憶體可以開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="36c39-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="36c39-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="36c39-130">0x40005</span></span> | <span data-ttu-id="36c39-131">列舉中不會有更多的限定詞。</span><span class="sxs-lookup"><span data-stu-id="36c39-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="36c39-132">0</span><span class="sxs-lookup"><span data-stu-id="36c39-132">0</span></span> | <span data-ttu-id="36c39-133">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="36c39-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="36c39-134">備註</span><span class="sxs-lookup"><span data-stu-id="36c39-134">Remarks</span></span>

<span data-ttu-id="36c39-135">此函式會包裝對[IWbemQualifierSet：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="36c39-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="36c39-136">您會重複`QualifierSet_Next`呼叫函式來列舉所有的限定詞，直到函`WBEM_S_NO_MORE_DATA`式傳回為止。</span><span class="sxs-lookup"><span data-stu-id="36c39-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="36c39-137">若要及早終止列舉，請呼叫[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函數。</span><span class="sxs-lookup"><span data-stu-id="36c39-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="36c39-138">列舉期間傳回的限定詞順序未定義。</span><span class="sxs-lookup"><span data-stu-id="36c39-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="36c39-139">需求</span><span class="sxs-lookup"><span data-stu-id="36c39-139">Requirements</span></span>  
 <span data-ttu-id="36c39-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36c39-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c39-141">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="36c39-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="36c39-142">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="36c39-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c39-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36c39-143">See also</span></span>

- [<span data-ttu-id="36c39-144">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="36c39-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
