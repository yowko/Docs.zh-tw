---
title: "FormatFromRawValue 函式 （Unmanaged API 參考）"
description: "FormatFromRawValue 函式會將未經處理的效能資料轉換成指定的格式。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c01db47b5362d7048e2e5ecd1b63acfe03eff860
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="bfae5-103">FormatFromRawValue 函式</span><span class="sxs-lookup"><span data-stu-id="bfae5-103">FormatFromRawValue function</span></span>
<span data-ttu-id="bfae5-104">將指定的格式，一個的未經處理的效能資料值或兩個原始效能資料值的轉換，如果格式轉換是以時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="bfae5-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bfae5-105">語法</span><span class="sxs-lookup"><span data-stu-id="bfae5-105">Syntax</span></span>  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a><span data-ttu-id="bfae5-106">參數</span><span class="sxs-lookup"><span data-stu-id="bfae5-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="bfae5-107">[in]計數器類型。</span><span class="sxs-lookup"><span data-stu-id="bfae5-107">[in] The counter type.</span></span> <span data-ttu-id="bfae5-108">如需計數器類型的清單，請參閱[WMI 效能計數器型別](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="bfae5-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="bfae5-109">`dwCounterType`可以是除了任何計數器類型`PERF_LARGE_RAW_FRACTION`和`PERF_LARGE_RAW_BASE`。</span><span class="sxs-lookup"><span data-stu-id="bfae5-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="bfae5-110">[in]要轉換的未經處理的效能資料的格式。</span><span class="sxs-lookup"><span data-stu-id="bfae5-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="bfae5-111">它可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="bfae5-111">It can be one of the following values:</span></span>

|<span data-ttu-id="bfae5-112">常數</span><span class="sxs-lookup"><span data-stu-id="bfae5-112">Constant</span></span>  |<span data-ttu-id="bfae5-113">值</span><span class="sxs-lookup"><span data-stu-id="bfae5-113">Value</span></span>  |<span data-ttu-id="bfae5-114">說明</span><span class="sxs-lookup"><span data-stu-id="bfae5-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="bfae5-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="bfae5-115">0x00000200</span></span> | <span data-ttu-id="bfae5-116">傳回的導出的值做為雙精確度浮點數值。</span><span class="sxs-lookup"><span data-stu-id="bfae5-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="bfae5-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="bfae5-117">0x00000400</span></span> | <span data-ttu-id="bfae5-118">以 64 位元整數的形式傳回導出的值。</span><span class="sxs-lookup"><span data-stu-id="bfae5-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="bfae5-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="bfae5-119">0x00000100</span></span> | <span data-ttu-id="bfae5-120">以 32 位元整數的形式傳回導出的值。</span><span class="sxs-lookup"><span data-stu-id="bfae5-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="bfae5-121">其中一個先前的值可以是其中一個下列調整旗標 ORed:</span><span class="sxs-lookup"><span data-stu-id="bfae5-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="bfae5-122">常數</span><span class="sxs-lookup"><span data-stu-id="bfae5-122">Constant</span></span>  |<span data-ttu-id="bfae5-123">值</span><span class="sxs-lookup"><span data-stu-id="bfae5-123">Value</span></span>  |<span data-ttu-id="bfae5-124">說明</span><span class="sxs-lookup"><span data-stu-id="bfae5-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="bfae5-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="bfae5-125">0x00001000</span></span> | <span data-ttu-id="bfae5-126">不會套用計數器的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="bfae5-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="bfae5-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="bfae5-127">0x00002000</span></span> | <span data-ttu-id="bfae5-128">最終的值乘以 1000。</span><span class="sxs-lookup"><span data-stu-id="bfae5-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="bfae5-129">[in]如果所需的格式轉換的時間基底指標。</span><span class="sxs-lookup"><span data-stu-id="bfae5-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="bfae5-130">如果找不到所需的格式轉換的時間基底的資訊，則會忽略此參數的值。</span><span class="sxs-lookup"><span data-stu-id="bfae5-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="bfae5-131">`pRawValue1`[in]指標[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)結構，表示原始效能值。</span><span class="sxs-lookup"><span data-stu-id="bfae5-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="bfae5-132">`pRawValue2`[in]指標[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)結構，表示第二個的未經處理的效能值。</span><span class="sxs-lookup"><span data-stu-id="bfae5-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="bfae5-133">如果第二個的未經處理的效能值不是必要的這個參數應該是`null`。</span><span class="sxs-lookup"><span data-stu-id="bfae5-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="bfae5-134">`pFmtValue`[out]指標[ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx)接收格式化的效能值的結構。</span><span class="sxs-lookup"><span data-stu-id="bfae5-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="bfae5-135">傳回值</span><span class="sxs-lookup"><span data-stu-id="bfae5-135">Return value</span></span>

<span data-ttu-id="bfae5-136">這個函式會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="bfae5-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="bfae5-137">常數</span><span class="sxs-lookup"><span data-stu-id="bfae5-137">Constant</span></span>  |<span data-ttu-id="bfae5-138">值</span><span class="sxs-lookup"><span data-stu-id="bfae5-138">Value</span></span>  |<span data-ttu-id="bfae5-139">描述</span><span class="sxs-lookup"><span data-stu-id="bfae5-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="bfae5-140">0</span><span class="sxs-lookup"><span data-stu-id="bfae5-140">0</span></span> | <span data-ttu-id="bfae5-141">函式呼叫會成功。</span><span class="sxs-lookup"><span data-stu-id="bfae5-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="bfae5-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="bfae5-142">0xC0000BBD</span></span> | <span data-ttu-id="bfae5-143">必要的引數已遺失或不正確。</span><span class="sxs-lookup"><span data-stu-id="bfae5-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="bfae5-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="bfae5-144">0xC0000BBC</span></span> | <span data-ttu-id="bfae5-145">控制代碼不是有效的 PDH 物件。</span><span class="sxs-lookup"><span data-stu-id="bfae5-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="bfae5-146">備註</span><span class="sxs-lookup"><span data-stu-id="bfae5-146">Remarks</span></span>

<span data-ttu-id="bfae5-147">此函式會包裝呼叫[FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx)函式。</span><span class="sxs-lookup"><span data-stu-id="bfae5-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfae5-148">需求</span><span class="sxs-lookup"><span data-stu-id="bfae5-148">Requirements</span></span>  
 <span data-ttu-id="bfae5-149">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfae5-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfae5-150">**程式庫：** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="bfae5-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="bfae5-151">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bfae5-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfae5-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="bfae5-152">See also</span></span>  
[<span data-ttu-id="bfae5-153">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="bfae5-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
