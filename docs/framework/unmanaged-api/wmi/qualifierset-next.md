---
title: QualifierSet_Next 函式 （Unmanaged API 參考）
description: QualifierSet_Next 函式會擷取下一步的限定詞列舉型別。
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
ms.openlocfilehash: a8232691c697c51b5a480a68c6d952f294a63460
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460223"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="b8ca9-103">QualifierSet_Next 函式</span><span class="sxs-lookup"><span data-stu-id="b8ca9-103">QualifierSet_Next function</span></span>
<span data-ttu-id="b8ca9-104">擷取列舉型別呼叫啟動下一步的限定詞[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b8ca9-105">語法</span><span class="sxs-lookup"><span data-stu-id="b8ca9-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="b8ca9-106">參數</span><span class="sxs-lookup"><span data-stu-id="b8ca9-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="b8ca9-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="b8ca9-108">[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="b8ca9-109">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-109">[in] Reserved.</span></span> <span data-ttu-id="b8ca9-110">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="b8ca9-111">[out]限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="b8ca9-112">如果`null`，這個參數已忽略; 否則`pstrName`應該不指向有效`BSTR`或發生記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="b8ca9-113">如果不是 null，函式一律會配置新`BSTR`當傳回`WBEM_S_NO_ERROR`。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="b8ca9-114">[out]成功時，辨識符號的值。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="b8ca9-115">如果函式失敗，`VARIANT`指向`pVal`則不會修改。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="b8ca9-116">如果這個參數是`null`，會忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="b8ca9-117">[out]接收限定詞標註的長指標。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="b8ca9-118">如果不想要的類別資訊，這個參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b8ca9-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="b8ca9-119">Return value</span></span>

<span data-ttu-id="b8ca9-120">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="b8ca9-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b8ca9-121">常數</span><span class="sxs-lookup"><span data-stu-id="b8ca9-121">Constant</span></span>  |<span data-ttu-id="b8ca9-122">值</span><span class="sxs-lookup"><span data-stu-id="b8ca9-122">Value</span></span>  |<span data-ttu-id="b8ca9-123">描述</span><span class="sxs-lookup"><span data-stu-id="b8ca9-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b8ca9-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b8ca9-124">0x80041008</span></span> | <span data-ttu-id="b8ca9-125">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="b8ca9-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="b8ca9-126">0x8004101d</span></span> | <span data-ttu-id="b8ca9-127">呼叫端沒有呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b8ca9-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b8ca9-128">0x80041006</span></span> | <span data-ttu-id="b8ca9-129">使用開始新的列舉型別沒有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="b8ca9-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="b8ca9-130">0x40005</span></span> | <span data-ttu-id="b8ca9-131">沒有多個限定詞會保留在列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b8ca9-132">0</span><span class="sxs-lookup"><span data-stu-id="b8ca9-132">0</span></span> | <span data-ttu-id="b8ca9-133">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b8ca9-134">備註</span><span class="sxs-lookup"><span data-stu-id="b8ca9-134">Remarks</span></span>

<span data-ttu-id="b8ca9-135">此函式會包裝呼叫[IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-135">This function wraps a call to the [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b8ca9-136">您呼叫`QualifierSet_Next`重複列舉所有的限定詞，直到函式傳回的函式`WBEM_S_NO_MORE_DATA`。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="b8ca9-137">若要終止列舉早期，呼叫[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函式。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="b8ca9-138">傳回在列舉期間的限定詞的順序是未定義。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8ca9-139">需求</span><span class="sxs-lookup"><span data-stu-id="b8ca9-139">Requirements</span></span>  
 <span data-ttu-id="b8ca9-140">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ca9-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ca9-141">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b8ca9-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b8ca9-142">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ca9-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ca9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8ca9-143">See also</span></span>  
[<span data-ttu-id="b8ca9-144">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="b8ca9-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
