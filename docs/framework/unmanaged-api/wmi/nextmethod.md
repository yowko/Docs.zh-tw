---
title: NextMethod 函式 （Unmanaged API 參考）
description: NextMethod 函式會擷取列舉中的下一個方法。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4559663194cb845fb0cc040e1f6739e38caa0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461139"
---
# <a name="nextmethod-function"></a><span data-ttu-id="d8f2d-103">NextMethod 函式</span><span class="sxs-lookup"><span data-stu-id="d8f2d-103">NextMethod function</span></span>
<span data-ttu-id="d8f2d-104">擷取下一個方法呼叫開始列舉型別中的[BeginMethodEnumeration](beginmethodenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d8f2d-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8f2d-105">Syntax</span></span>  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="d8f2d-106">參數</span><span class="sxs-lookup"><span data-stu-id="d8f2d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d8f2d-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d8f2d-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="d8f2d-109">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-109">[in] Reserved.</span></span> <span data-ttu-id="d8f2d-110">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="d8f2d-111">[out]指標指向`null`之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="d8f2d-112">當函式傳回時，新的位址`BSTR`，其中包含方法名稱。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="d8f2d-113">[out]接收資料指標的指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)包含`in`方法的參數。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-113">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="d8f2d-114">[out]接收資料指標的指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)包含`out`方法的參數。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-114">[out] A pointer that receives a pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d8f2d-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8f2d-115">Return value</span></span>

<span data-ttu-id="d8f2d-116">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="d8f2d-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d8f2d-117">常數</span><span class="sxs-lookup"><span data-stu-id="d8f2d-117">Constant</span></span>  |<span data-ttu-id="d8f2d-118">值</span><span class="sxs-lookup"><span data-stu-id="d8f2d-118">Value</span></span>  |<span data-ttu-id="d8f2d-119">描述</span><span class="sxs-lookup"><span data-stu-id="d8f2d-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="d8f2d-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="d8f2d-120">0x8004101d</span></span> | <span data-ttu-id="d8f2d-121">沒有不需要呼叫[ `BeginEnumeration` ](beginenumeration.md)函式。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d8f2d-122">0</span><span class="sxs-lookup"><span data-stu-id="d8f2d-122">0</span></span> | <span data-ttu-id="d8f2d-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="d8f2d-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="d8f2d-124">0x40005</span></span> | <span data-ttu-id="d8f2d-125">列舉中沒有其他內容。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d8f2d-126">備註</span><span class="sxs-lookup"><span data-stu-id="d8f2d-126">Remarks</span></span>

<span data-ttu-id="d8f2d-127">此函式會包裝呼叫[IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-127">This function wraps a call to the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d8f2d-128">呼叫端會開始將列舉序列呼叫[BeginMethodEnumeration](beginmethodenumeration.md)函式，，然後再呼叫 [NextMethod] 函式，直到此函數會傳回`WBEM_S_NO_MORE_DATA`。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="d8f2d-129">（選擇性） 呼叫端會完成序列藉由呼叫[EndMethodEnumeration](endmethodenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="d8f2d-130">呼叫端可能會提早終止列舉型別，藉由呼叫[EndMethodEnumeration](endmethodenumeration.md)在任何時間。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="d8f2d-131">範例</span><span class="sxs-lookup"><span data-stu-id="d8f2d-131">Example</span></span>

<span data-ttu-id="d8f2d-132">如需 c + + 的範例，請參閱[IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-132">For a C++ example, see the [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8f2d-133">需求</span><span class="sxs-lookup"><span data-stu-id="d8f2d-133">Requirements</span></span>  
 <span data-ttu-id="d8f2d-134">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f2d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8f2d-135">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d8f2d-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d8f2d-136">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8f2d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f2d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8f2d-137">See also</span></span>  
[<span data-ttu-id="d8f2d-138">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="d8f2d-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
