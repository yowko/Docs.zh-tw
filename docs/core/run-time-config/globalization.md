---
title: 全球化 config 設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，它如何剖析日文日期。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0571c64eff5b38aafa37026fb2ba7f4aef778beb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802775"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="dc104-103">全球化的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="dc104-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="dc104-104">不變模式</span><span class="sxs-lookup"><span data-stu-id="dc104-104">Invariant mode</span></span>

- <span data-ttu-id="dc104-105">判斷 .NET Core 應用程式是否以全球化不變模式執行，而不需要存取特定文化特性的資料和行為，或是否可存取文化特性資料。</span><span class="sxs-lookup"><span data-stu-id="dc104-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="dc104-106">預設值：執行可存取文化特性資料的應用程式（`false`）。</span><span class="sxs-lookup"><span data-stu-id="dc104-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="dc104-107">如需詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="dc104-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="dc104-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="dc104-108">Setting name</span></span> | <span data-ttu-id="dc104-109">值</span><span class="sxs-lookup"><span data-stu-id="dc104-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="dc104-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="dc104-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="dc104-111">`false`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="dc104-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="dc104-112">`true`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="dc104-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="dc104-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="dc104-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="dc104-114">`0`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="dc104-114">`0` - access to cultural data</span></span><br/><span data-ttu-id="dc104-115">`1`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="dc104-115">`1` - run in invariant mode</span></span> |

## <a name="era-year-ranges"></a><span data-ttu-id="dc104-116">紀元年份範圍</span><span class="sxs-lookup"><span data-stu-id="dc104-116">Era year ranges</span></span>

- <span data-ttu-id="dc104-117">判斷支援多個紀元之行事曆的範圍檢查是否會被放寬，或是否會擲回 <xref:System.ArgumentOutOfRangeException>的日期。</span><span class="sxs-lookup"><span data-stu-id="dc104-117">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="dc104-118">預設值：範圍檢查是寬鬆的（`false`）。</span><span class="sxs-lookup"><span data-stu-id="dc104-118">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="dc104-119">如需詳細資訊，請參閱行事[曆、紀元和日期範圍：寬鬆範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。</span><span class="sxs-lookup"><span data-stu-id="dc104-119">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="dc104-120">設定名稱</span><span class="sxs-lookup"><span data-stu-id="dc104-120">Setting name</span></span> | <span data-ttu-id="dc104-121">值</span><span class="sxs-lookup"><span data-stu-id="dc104-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="dc104-122">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="dc104-122">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="dc104-123">`false` 寬鬆的範圍檢查</span><span class="sxs-lookup"><span data-stu-id="dc104-123">`false` - relaxed range checks</span></span><br/><span data-ttu-id="dc104-124">`true`-溢位造成例外狀況</span><span class="sxs-lookup"><span data-stu-id="dc104-124">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="dc104-125">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="dc104-125">**Environment variable**</span></span> | <span data-ttu-id="dc104-126">N/A</span><span class="sxs-lookup"><span data-stu-id="dc104-126">N/A</span></span> | <span data-ttu-id="dc104-127">N/A</span><span class="sxs-lookup"><span data-stu-id="dc104-127">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="dc104-128">日文日期剖析</span><span class="sxs-lookup"><span data-stu-id="dc104-128">Japanese date parsing</span></span>

- <span data-ttu-id="dc104-129">判斷在年份中包含 "1" 或 "Gannen" 的字串是否已成功剖析，或是否只支援 "1"。</span><span class="sxs-lookup"><span data-stu-id="dc104-129">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="dc104-130">預設值：剖析包含 "1" 或 "Gannen" 做為年份的字串（`false`）。</span><span class="sxs-lookup"><span data-stu-id="dc104-130">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="dc104-131">如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="dc104-131">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="dc104-132">設定名稱</span><span class="sxs-lookup"><span data-stu-id="dc104-132">Setting name</span></span> | <span data-ttu-id="dc104-133">值</span><span class="sxs-lookup"><span data-stu-id="dc104-133">Values</span></span> |
| - | - | - |
| <span data-ttu-id="dc104-134">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="dc104-134">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="dc104-135">`false`-支援 "Gannen" 或 "1"</span><span class="sxs-lookup"><span data-stu-id="dc104-135">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="dc104-136">僅支援 `true` "1"</span><span class="sxs-lookup"><span data-stu-id="dc104-136">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="dc104-137">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="dc104-137">**Environment variable**</span></span> | <span data-ttu-id="dc104-138">N/A</span><span class="sxs-lookup"><span data-stu-id="dc104-138">N/A</span></span> | <span data-ttu-id="dc104-139">N/A</span><span class="sxs-lookup"><span data-stu-id="dc104-139">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="dc104-140">日文年份格式</span><span class="sxs-lookup"><span data-stu-id="dc104-140">Japanese year format</span></span>

- <span data-ttu-id="dc104-141">決定日本日曆紀元的第一年是否格式化為 "Gannen" 或數位。</span><span class="sxs-lookup"><span data-stu-id="dc104-141">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="dc104-142">預設值：將第一年份格式化為 "Gannen" （`false`）。</span><span class="sxs-lookup"><span data-stu-id="dc104-142">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="dc104-143">如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="dc104-143">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="dc104-144">設定名稱</span><span class="sxs-lookup"><span data-stu-id="dc104-144">Setting name</span></span> | <span data-ttu-id="dc104-145">值</span><span class="sxs-lookup"><span data-stu-id="dc104-145">Values</span></span> |
| - | - | - |
| <span data-ttu-id="dc104-146">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="dc104-146">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="dc104-147">`false` 格式為 "Gannen"</span><span class="sxs-lookup"><span data-stu-id="dc104-147">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="dc104-148">`true` 格式為數字</span><span class="sxs-lookup"><span data-stu-id="dc104-148">`true` - format as number</span></span> |
| <span data-ttu-id="dc104-149">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="dc104-149">**Environment variable**</span></span> | <span data-ttu-id="dc104-150">N/A</span><span class="sxs-lookup"><span data-stu-id="dc104-150">N/A</span></span> | <span data-ttu-id="dc104-151">N/A</span><span class="sxs-lookup"><span data-stu-id="dc104-151">N/A</span></span> |
