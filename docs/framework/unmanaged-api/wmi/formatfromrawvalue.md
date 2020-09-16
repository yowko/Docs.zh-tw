---
title: 'FormatFromRawValue 函式 (非受控 API 參考) '
description: FormatFromRawValue 函數會將原始效能資料轉換成指定的格式。
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
ms.openlocfilehash: e7f3e4eef4a7e378529c2097a8fe1a753a98c961
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553710"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="a8a4d-103">FormatFromRawValue 函式</span><span class="sxs-lookup"><span data-stu-id="a8a4d-103">FormatFromRawValue function</span></span>
<span data-ttu-id="a8a4d-104">將一個原始效能資料值轉換為指定的格式，或轉換為兩個原始效能資料值 (若格式轉換是以時間為基礎)。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a8a4d-105">語法</span><span class="sxs-lookup"><span data-stu-id="a8a4d-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="a8a4d-106">參數</span><span class="sxs-lookup"><span data-stu-id="a8a4d-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="a8a4d-107">在計數器類型。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-107">[in] The counter type.</span></span> <span data-ttu-id="a8a4d-108">如需計數器類型的清單，請參閱 [WMI 效能計數器類型](/windows/desktop/WmiSdk/wmi-performance-counter-types)。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="a8a4d-109">`dwCounterType` 可以是和以外的任何計數器 `PERF_LARGE_RAW_FRACTION` 類型 `PERF_LARGE_RAW_BASE` 。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="a8a4d-110">在要轉換原始效能資料的格式。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="a8a4d-111">它可能是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="a8a4d-111">It can be one of the following values:</span></span>

|<span data-ttu-id="a8a4d-112">常數</span><span class="sxs-lookup"><span data-stu-id="a8a4d-112">Constant</span></span>  |<span data-ttu-id="a8a4d-113">值</span><span class="sxs-lookup"><span data-stu-id="a8a4d-113">Value</span></span>  |<span data-ttu-id="a8a4d-114">說明</span><span class="sxs-lookup"><span data-stu-id="a8a4d-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="a8a4d-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="a8a4d-115">0x00000200</span></span> | <span data-ttu-id="a8a4d-116">傳回作為雙精確度浮點數的計算值。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="a8a4d-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="a8a4d-117">0x00000400</span></span> | <span data-ttu-id="a8a4d-118">傳回做為64位整數的計算值。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="a8a4d-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="a8a4d-119">0x00000100</span></span> | <span data-ttu-id="a8a4d-120">傳回做為32位整數的計算值。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="a8a4d-121">您可以使用下列其中一個調整旗標來 Or 運算先前的其中一個值：</span><span class="sxs-lookup"><span data-stu-id="a8a4d-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="a8a4d-122">常數</span><span class="sxs-lookup"><span data-stu-id="a8a4d-122">Constant</span></span>  |<span data-ttu-id="a8a4d-123">值</span><span class="sxs-lookup"><span data-stu-id="a8a4d-123">Value</span></span>  |<span data-ttu-id="a8a4d-124">說明</span><span class="sxs-lookup"><span data-stu-id="a8a4d-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="a8a4d-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="a8a4d-125">0x00001000</span></span> | <span data-ttu-id="a8a4d-126">請勿套用計數器的縮放比例因數。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="a8a4d-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="a8a4d-127">0x00002000</span></span> | <span data-ttu-id="a8a4d-128">將最終值乘以1000。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="a8a4d-129">在針對格式轉換所需的時間基底指標。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="a8a4d-130">如果格式轉換不需要時間基底資訊，則會忽略這個參數的值。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="a8a4d-131">在 [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 結構的指標，表示原始效能值。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="a8a4d-132">在 [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 結構的指標，表示第二個原始效能值。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="a8a4d-133">如果不需要第二個原始效能值，此參數應為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="a8a4d-134">擴展 [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) 接收格式化效能值之結構的指標。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8a4d-135">傳回值</span><span class="sxs-lookup"><span data-stu-id="a8a4d-135">Return value</span></span>

<span data-ttu-id="a8a4d-136">此函數會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="a8a4d-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="a8a4d-137">常數</span><span class="sxs-lookup"><span data-stu-id="a8a4d-137">Constant</span></span>  |<span data-ttu-id="a8a4d-138">值</span><span class="sxs-lookup"><span data-stu-id="a8a4d-138">Value</span></span>  |<span data-ttu-id="a8a4d-139">說明</span><span class="sxs-lookup"><span data-stu-id="a8a4d-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="a8a4d-140">0</span><span class="sxs-lookup"><span data-stu-id="a8a4d-140">0</span></span> | <span data-ttu-id="a8a4d-141">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="a8a4d-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="a8a4d-142">0xC0000BBD</span></span> | <span data-ttu-id="a8a4d-143">必要的引數遺失或不正確。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="a8a4d-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="a8a4d-144">0xC0000BBC</span></span> | <span data-ttu-id="a8a4d-145">控制碼不是有效的 PDH 物件。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a8a4d-146">備註</span><span class="sxs-lookup"><span data-stu-id="a8a4d-146">Remarks</span></span>

<span data-ttu-id="a8a4d-147">此函數會包裝對 [FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) 函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-147">This function wraps a call to the [FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8a4d-148">需求</span><span class="sxs-lookup"><span data-stu-id="a8a4d-148">Requirements</span></span>

 <span data-ttu-id="a8a4d-149">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8a4d-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="a8a4d-150">連結**庫：** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="a8a4d-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="a8a4d-151">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a4d-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a8a4d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8a4d-152">See also</span></span>

- [<span data-ttu-id="a8a4d-153">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="a8a4d-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
