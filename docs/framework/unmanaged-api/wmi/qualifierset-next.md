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
ms.openlocfilehash: c9c824b0158618848c13183d92f88604460d5099
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141718"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="a37a5-103">QualifierSet_Next 函式</span><span class="sxs-lookup"><span data-stu-id="a37a5-103">QualifierSet_Next function</span></span>
<span data-ttu-id="a37a5-104">擷取透過呼叫 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式而開始之列舉中的下一個限定詞。</span><span class="sxs-lookup"><span data-stu-id="a37a5-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a37a5-105">語法</span><span class="sxs-lookup"><span data-stu-id="a37a5-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="a37a5-106">參數</span><span class="sxs-lookup"><span data-stu-id="a37a5-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="a37a5-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="a37a5-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="a37a5-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a37a5-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="a37a5-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="a37a5-109">[in] Reserved.</span></span> <span data-ttu-id="a37a5-110">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="a37a5-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="a37a5-111">脫銷辨識符號的名稱。</span><span class="sxs-lookup"><span data-stu-id="a37a5-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="a37a5-112">如果 `null`，則會忽略此參數;否則，`pstrName` 不應該指向有效的 `BSTR` 或發生記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="a37a5-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="a37a5-113">如果不是 null，當函式傳回 `WBEM_S_NO_ERROR`時，一律會配置新的 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="a37a5-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="a37a5-114">脫銷如果成功，則為限定詞的值。</span><span class="sxs-lookup"><span data-stu-id="a37a5-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="a37a5-115">如果函式失敗，`pVal` 所指向的 `VARIANT` 不會修改。</span><span class="sxs-lookup"><span data-stu-id="a37a5-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="a37a5-116">如果 `null`此參數，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="a37a5-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="a37a5-117">脫銷接收限定詞類別的長整數指標。</span><span class="sxs-lookup"><span data-stu-id="a37a5-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="a37a5-118">如果不想要的是類別資訊，可以 `null`此參數。</span><span class="sxs-lookup"><span data-stu-id="a37a5-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a37a5-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="a37a5-119">Return value</span></span>

<span data-ttu-id="a37a5-120">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a37a5-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a37a5-121">常數</span><span class="sxs-lookup"><span data-stu-id="a37a5-121">Constant</span></span>  |<span data-ttu-id="a37a5-122">值</span><span class="sxs-lookup"><span data-stu-id="a37a5-122">Value</span></span>  |<span data-ttu-id="a37a5-123">描述</span><span class="sxs-lookup"><span data-stu-id="a37a5-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a37a5-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a37a5-124">0x80041008</span></span> | <span data-ttu-id="a37a5-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="a37a5-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="a37a5-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a37a5-126">0x8004101d</span></span> | <span data-ttu-id="a37a5-127">呼叫端未呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="a37a5-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a37a5-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a37a5-128">0x80041006</span></span> | <span data-ttu-id="a37a5-129">沒有足夠的記憶體可以開始新的列舉。</span><span class="sxs-lookup"><span data-stu-id="a37a5-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="a37a5-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="a37a5-130">0x40005</span></span> | <span data-ttu-id="a37a5-131">列舉中不會有更多的限定詞。</span><span class="sxs-lookup"><span data-stu-id="a37a5-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a37a5-132">0</span><span class="sxs-lookup"><span data-stu-id="a37a5-132">0</span></span> | <span data-ttu-id="a37a5-133">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a37a5-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a37a5-134">備註</span><span class="sxs-lookup"><span data-stu-id="a37a5-134">Remarks</span></span>

<span data-ttu-id="a37a5-135">此函式會包裝對[IWbemQualifierSet：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a37a5-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="a37a5-136">您會重複呼叫 `QualifierSet_Next` 函式，以列舉所有的限定詞，直到函式傳回 `WBEM_S_NO_MORE_DATA`為止。</span><span class="sxs-lookup"><span data-stu-id="a37a5-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="a37a5-137">若要及早終止列舉，請呼叫[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函數。</span><span class="sxs-lookup"><span data-stu-id="a37a5-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="a37a5-138">列舉期間傳回的限定詞順序未定義。</span><span class="sxs-lookup"><span data-stu-id="a37a5-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="a37a5-139">需求</span><span class="sxs-lookup"><span data-stu-id="a37a5-139">Requirements</span></span>  
 <span data-ttu-id="a37a5-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a37a5-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a37a5-141">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="a37a5-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a37a5-142">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a37a5-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37a5-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="a37a5-143">See also</span></span>

- [<span data-ttu-id="a37a5-144">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="a37a5-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
