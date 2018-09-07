---
title: FormatFromRawValue 函式 （Unmanaged API 參考）
description: FormatFromRawValue 函式會將未經處理的效能資料轉換成指定的格式。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95ef445d41672c5c2895bd7115afb6a73a57e8f9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086133"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="510c8-103">FormatFromRawValue 函式</span><span class="sxs-lookup"><span data-stu-id="510c8-103">FormatFromRawValue function</span></span>
<span data-ttu-id="510c8-104">將一個原始效能資料值轉換為指定的格式，或轉換為兩個原始效能資料值 (若格式轉換是以時間為基礎)。</span><span class="sxs-lookup"><span data-stu-id="510c8-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="510c8-105">語法</span><span class="sxs-lookup"><span data-stu-id="510c8-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="510c8-106">參數</span><span class="sxs-lookup"><span data-stu-id="510c8-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="510c8-107">[in]計數器型別。</span><span class="sxs-lookup"><span data-stu-id="510c8-107">[in] The counter type.</span></span> <span data-ttu-id="510c8-108">如需計數器型別，請參閱[WMI 效能計數器類型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。</span><span class="sxs-lookup"><span data-stu-id="510c8-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="510c8-109">`dwCounterType` 可以是任何計數器型別，除了`PERF_LARGE_RAW_FRACTION`和`PERF_LARGE_RAW_BASE`。</span><span class="sxs-lookup"><span data-stu-id="510c8-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="510c8-110">[in]要用來轉換未經處理的效能資料的格式。</span><span class="sxs-lookup"><span data-stu-id="510c8-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="510c8-111">它可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="510c8-111">It can be one of the following values:</span></span>

|<span data-ttu-id="510c8-112">常數</span><span class="sxs-lookup"><span data-stu-id="510c8-112">Constant</span></span>  |<span data-ttu-id="510c8-113">值</span><span class="sxs-lookup"><span data-stu-id="510c8-113">Value</span></span>  |<span data-ttu-id="510c8-114">描述</span><span class="sxs-lookup"><span data-stu-id="510c8-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="510c8-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="510c8-115">0x00000200</span></span> | <span data-ttu-id="510c8-116">傳回的導出的值做為雙精度浮點數值。</span><span class="sxs-lookup"><span data-stu-id="510c8-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="510c8-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="510c8-117">0x00000400</span></span> | <span data-ttu-id="510c8-118">傳回計算的值為 64 位元整數。</span><span class="sxs-lookup"><span data-stu-id="510c8-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="510c8-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="510c8-119">0x00000100</span></span> | <span data-ttu-id="510c8-120">傳回計算的值為 32 位元整數。</span><span class="sxs-lookup"><span data-stu-id="510c8-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="510c8-121">其中一個先前的值可以是其中一個下列調整旗標 ored 加入：</span><span class="sxs-lookup"><span data-stu-id="510c8-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="510c8-122">常數</span><span class="sxs-lookup"><span data-stu-id="510c8-122">Constant</span></span>  |<span data-ttu-id="510c8-123">值</span><span class="sxs-lookup"><span data-stu-id="510c8-123">Value</span></span>  |<span data-ttu-id="510c8-124">描述</span><span class="sxs-lookup"><span data-stu-id="510c8-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="510c8-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="510c8-125">0x00001000</span></span> | <span data-ttu-id="510c8-126">不會套用計數器的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="510c8-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="510c8-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="510c8-127">0x00002000</span></span> | <span data-ttu-id="510c8-128">最終的值乘以 1000。</span><span class="sxs-lookup"><span data-stu-id="510c8-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="510c8-129">[in]如果所需的格式轉換的時間基底指標。</span><span class="sxs-lookup"><span data-stu-id="510c8-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="510c8-130">如果時間基底資訊不是所需的格式轉換，則會忽略此參數的值。</span><span class="sxs-lookup"><span data-stu-id="510c8-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="510c8-131">`pRawValue1` [in]指標[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)結構，表示原始效能值。</span><span class="sxs-lookup"><span data-stu-id="510c8-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="510c8-132">`pRawValue2` [in]指標[ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)結構，表示第二個的未經處理的效能值。</span><span class="sxs-lookup"><span data-stu-id="510c8-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="510c8-133">如果第二個的未經處理的效能值不是必要的這個參數應該是`null`。</span><span class="sxs-lookup"><span data-stu-id="510c8-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="510c8-134">`pFmtValue` [out]指標[ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx)接收格式化的效能值的結構。</span><span class="sxs-lookup"><span data-stu-id="510c8-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="510c8-135">傳回值</span><span class="sxs-lookup"><span data-stu-id="510c8-135">Return value</span></span>

<span data-ttu-id="510c8-136">這個函式會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="510c8-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="510c8-137">常數</span><span class="sxs-lookup"><span data-stu-id="510c8-137">Constant</span></span>  |<span data-ttu-id="510c8-138">值</span><span class="sxs-lookup"><span data-stu-id="510c8-138">Value</span></span>  |<span data-ttu-id="510c8-139">描述</span><span class="sxs-lookup"><span data-stu-id="510c8-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="510c8-140">0</span><span class="sxs-lookup"><span data-stu-id="510c8-140">0</span></span> | <span data-ttu-id="510c8-141">函式呼叫會成功。</span><span class="sxs-lookup"><span data-stu-id="510c8-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="510c8-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="510c8-142">0xC0000BBD</span></span> | <span data-ttu-id="510c8-143">必要的引數是遺失或不正確。</span><span class="sxs-lookup"><span data-stu-id="510c8-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="510c8-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="510c8-144">0xC0000BBC</span></span> | <span data-ttu-id="510c8-145">控制代碼不是有效的 PDH 物件。</span><span class="sxs-lookup"><span data-stu-id="510c8-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="510c8-146">備註</span><span class="sxs-lookup"><span data-stu-id="510c8-146">Remarks</span></span>

<span data-ttu-id="510c8-147">此函式會包裝在呼叫[FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx)函式。</span><span class="sxs-lookup"><span data-stu-id="510c8-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="510c8-148">需求</span><span class="sxs-lookup"><span data-stu-id="510c8-148">Requirements</span></span>  
 <span data-ttu-id="510c8-149">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="510c8-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="510c8-150">**程式庫：** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="510c8-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="510c8-151">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="510c8-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510c8-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="510c8-152">See also</span></span>  
[<span data-ttu-id="510c8-153">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="510c8-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
