---
title: 格式從原始值函數（非託管 API 引用）
description: FormatFromRawValue 函數將原始效能資料轉換為指定的格式。
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
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176834"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="8f52d-103">FormatFromRawValue 函式</span><span class="sxs-lookup"><span data-stu-id="8f52d-103">FormatFromRawValue function</span></span>
<span data-ttu-id="8f52d-104">將一個原始效能資料值轉換為指定的格式，或轉換為兩個原始效能資料值 (若格式轉換是以時間為基礎)。</span><span class="sxs-lookup"><span data-stu-id="8f52d-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="8f52d-105">語法</span><span class="sxs-lookup"><span data-stu-id="8f52d-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a><span data-ttu-id="8f52d-106">參數</span><span class="sxs-lookup"><span data-stu-id="8f52d-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="8f52d-107">[在]計數器類型。</span><span class="sxs-lookup"><span data-stu-id="8f52d-107">[in] The counter type.</span></span> <span data-ttu-id="8f52d-108">有關計數器類型的清單，請參閱[WMI 效能計數器類型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。</span><span class="sxs-lookup"><span data-stu-id="8f52d-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="8f52d-109">`dwCounterType`可以是 除`PERF_LARGE_RAW_FRACTION`和`PERF_LARGE_RAW_BASE`之外的任何計數器類型。</span><span class="sxs-lookup"><span data-stu-id="8f52d-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="8f52d-110">[在]要將原始效能資料轉換為的格式。</span><span class="sxs-lookup"><span data-stu-id="8f52d-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="8f52d-111">它可能是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="8f52d-111">It can be one of the following values:</span></span>

|<span data-ttu-id="8f52d-112">持續性</span><span class="sxs-lookup"><span data-stu-id="8f52d-112">Constant</span></span>  |<span data-ttu-id="8f52d-113">值</span><span class="sxs-lookup"><span data-stu-id="8f52d-113">Value</span></span>  |<span data-ttu-id="8f52d-114">描述</span><span class="sxs-lookup"><span data-stu-id="8f52d-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="8f52d-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="8f52d-115">0x00000200</span></span> | <span data-ttu-id="8f52d-116">將計算值作為雙精度浮點值返回。</span><span class="sxs-lookup"><span data-stu-id="8f52d-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="8f52d-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="8f52d-117">0x00000400</span></span> | <span data-ttu-id="8f52d-118">將計算的值作為 64 位整數返回。</span><span class="sxs-lookup"><span data-stu-id="8f52d-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="8f52d-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="8f52d-119">0x00000100</span></span> | <span data-ttu-id="8f52d-120">將計算的值作為 32 位整數返回。</span><span class="sxs-lookup"><span data-stu-id="8f52d-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="8f52d-121">前面的值之一可以是 ORed，具有以下縮放標誌之一：</span><span class="sxs-lookup"><span data-stu-id="8f52d-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="8f52d-122">持續性</span><span class="sxs-lookup"><span data-stu-id="8f52d-122">Constant</span></span>  |<span data-ttu-id="8f52d-123">值</span><span class="sxs-lookup"><span data-stu-id="8f52d-123">Value</span></span>  |<span data-ttu-id="8f52d-124">描述</span><span class="sxs-lookup"><span data-stu-id="8f52d-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="8f52d-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="8f52d-125">0x00001000</span></span> | <span data-ttu-id="8f52d-126">不要應用計數器的縮放因數。</span><span class="sxs-lookup"><span data-stu-id="8f52d-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="8f52d-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="8f52d-127">0x00002000</span></span> | <span data-ttu-id="8f52d-128">將最終值乘以 1，000。</span><span class="sxs-lookup"><span data-stu-id="8f52d-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="8f52d-129">[在]指向時間基的指標，如果需要進行格式轉換。</span><span class="sxs-lookup"><span data-stu-id="8f52d-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="8f52d-130">如果格式轉換不需要時間基礎資訊，則忽略此參數的值。</span><span class="sxs-lookup"><span data-stu-id="8f52d-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="8f52d-131">[在]指向表示原始性能[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)值的結構的指標。</span><span class="sxs-lookup"><span data-stu-id="8f52d-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="8f52d-132">[在]指向表示第二[`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter)個原始性能值的結構的指標。</span><span class="sxs-lookup"><span data-stu-id="8f52d-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="8f52d-133">如果不需要第二個原始性能值，則此參數應為`null`。</span><span class="sxs-lookup"><span data-stu-id="8f52d-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="8f52d-134">[出]指向接收格式化性能[`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue)值的結構的指標。</span><span class="sxs-lookup"><span data-stu-id="8f52d-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f52d-135">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f52d-135">Return value</span></span>

<span data-ttu-id="8f52d-136">此函數返回以下值：</span><span class="sxs-lookup"><span data-stu-id="8f52d-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="8f52d-137">持續性</span><span class="sxs-lookup"><span data-stu-id="8f52d-137">Constant</span></span>  |<span data-ttu-id="8f52d-138">值</span><span class="sxs-lookup"><span data-stu-id="8f52d-138">Value</span></span>  |<span data-ttu-id="8f52d-139">描述</span><span class="sxs-lookup"><span data-stu-id="8f52d-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="8f52d-140">0</span><span class="sxs-lookup"><span data-stu-id="8f52d-140">0</span></span> | <span data-ttu-id="8f52d-141">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="8f52d-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="8f52d-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="8f52d-142">0xC0000BBD</span></span> | <span data-ttu-id="8f52d-143">所需的參數丟失或不正確。</span><span class="sxs-lookup"><span data-stu-id="8f52d-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="8f52d-144">0xC00000BBC</span><span class="sxs-lookup"><span data-stu-id="8f52d-144">0xC0000BBC</span></span> | <span data-ttu-id="8f52d-145">控制碼不是有效的 PDH 物件。</span><span class="sxs-lookup"><span data-stu-id="8f52d-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8f52d-146">備註</span><span class="sxs-lookup"><span data-stu-id="8f52d-146">Remarks</span></span>

<span data-ttu-id="8f52d-147">此函數將調用格式[從RawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))函數結束。</span><span class="sxs-lookup"><span data-stu-id="8f52d-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f52d-148">需求</span><span class="sxs-lookup"><span data-stu-id="8f52d-148">Requirements</span></span>

 <span data-ttu-id="8f52d-149">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f52d-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="8f52d-150">**庫：** 佩爾夫·德雷爾</span><span class="sxs-lookup"><span data-stu-id="8f52d-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="8f52d-151">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8f52d-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8f52d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f52d-152">See also</span></span>

- [<span data-ttu-id="8f52d-153">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="8f52d-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
