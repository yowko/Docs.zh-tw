---
title: 全球化 config 設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，它如何剖析日文日期。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 7668c345181d7c08cfca9c5cb76b8addd76223ec
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506801"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="ad1fe-103">全球化的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="ad1fe-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="ad1fe-104">不變模式</span><span class="sxs-lookup"><span data-stu-id="ad1fe-104">Invariant mode</span></span>

- <span data-ttu-id="ad1fe-105">判斷 .NET Core 應用程式是否以全球化不變模式執行，而不需要存取特定文化特性的資料和行為。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="ad1fe-106">預設值：執行具有文化特性資料存取權的`false`應用程式（）。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="ad1fe-107">如需詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="ad1fe-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad1fe-108">Setting name</span></span> | <span data-ttu-id="ad1fe-109">值</span><span class="sxs-lookup"><span data-stu-id="ad1fe-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad1fe-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="ad1fe-111">`false`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="ad1fe-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="ad1fe-112">`true`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="ad1fe-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="ad1fe-113">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="ad1fe-114">`false`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="ad1fe-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="ad1fe-115">`true`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="ad1fe-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="ad1fe-116">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="ad1fe-117">`0`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="ad1fe-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="ad1fe-118">`1`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="ad1fe-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="ad1fe-119">範例</span><span class="sxs-lookup"><span data-stu-id="ad1fe-119">Examples</span></span>

<span data-ttu-id="ad1fe-120">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="ad1fe-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="ad1fe-121">專案檔：</span><span class="sxs-lookup"><span data-stu-id="ad1fe-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="ad1fe-122">紀元年份範圍</span><span class="sxs-lookup"><span data-stu-id="ad1fe-122">Era year ranges</span></span>

- <span data-ttu-id="ad1fe-123">判斷支援多個紀元之行事曆的範圍檢查是否會放寬，或是否會擲回紀元日期範圍溢<xref:System.ArgumentOutOfRangeException>位的日期。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="ad1fe-124">預設值：範圍檢查是寬鬆`false`的（）。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="ad1fe-125">如需詳細資訊，請參閱行事[曆、紀元和日期範圍：寬鬆範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="ad1fe-126">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad1fe-126">Setting name</span></span> | <span data-ttu-id="ad1fe-127">值</span><span class="sxs-lookup"><span data-stu-id="ad1fe-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad1fe-128">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="ad1fe-129">`false`-寬鬆範圍檢查</span><span class="sxs-lookup"><span data-stu-id="ad1fe-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="ad1fe-130">`true`-溢位造成例外狀況</span><span class="sxs-lookup"><span data-stu-id="ad1fe-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="ad1fe-131">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-131">**Environment variable**</span></span> | <span data-ttu-id="ad1fe-132">N/A</span><span class="sxs-lookup"><span data-stu-id="ad1fe-132">N/A</span></span> | <span data-ttu-id="ad1fe-133">N/A</span><span class="sxs-lookup"><span data-stu-id="ad1fe-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="ad1fe-134">日文日期剖析</span><span class="sxs-lookup"><span data-stu-id="ad1fe-134">Japanese date parsing</span></span>

- <span data-ttu-id="ad1fe-135">判斷在年份中包含 "1" 或 "Gannen" 的字串是否已成功剖析，或是否只支援 "1"。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="ad1fe-136">預設值：剖析包含 "1" 或 "Gannen" 做為年份（`false`）的字串。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="ad1fe-137">如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="ad1fe-138">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad1fe-138">Setting name</span></span> | <span data-ttu-id="ad1fe-139">值</span><span class="sxs-lookup"><span data-stu-id="ad1fe-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad1fe-140">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="ad1fe-141">`false`-支援 "Gannen" 或 "1"</span><span class="sxs-lookup"><span data-stu-id="ad1fe-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="ad1fe-142">`true`-僅支援 "1"</span><span class="sxs-lookup"><span data-stu-id="ad1fe-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="ad1fe-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-143">**Environment variable**</span></span> | <span data-ttu-id="ad1fe-144">N/A</span><span class="sxs-lookup"><span data-stu-id="ad1fe-144">N/A</span></span> | <span data-ttu-id="ad1fe-145">N/A</span><span class="sxs-lookup"><span data-stu-id="ad1fe-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="ad1fe-146">日文年份格式</span><span class="sxs-lookup"><span data-stu-id="ad1fe-146">Japanese year format</span></span>

- <span data-ttu-id="ad1fe-147">決定日本日曆紀元的第一年是否格式化為 "Gannen" 或數位。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="ad1fe-148">預設值：將第一年格式化為 "Gannen`false`" （）。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="ad1fe-149">如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="ad1fe-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="ad1fe-150">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ad1fe-150">Setting name</span></span> | <span data-ttu-id="ad1fe-151">值</span><span class="sxs-lookup"><span data-stu-id="ad1fe-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ad1fe-152">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="ad1fe-153">`false`-格式為 "Gannen"</span><span class="sxs-lookup"><span data-stu-id="ad1fe-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="ad1fe-154">`true`-格式為數字</span><span class="sxs-lookup"><span data-stu-id="ad1fe-154">`true` - format as number</span></span> |
| <span data-ttu-id="ad1fe-155">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ad1fe-155">**Environment variable**</span></span> | <span data-ttu-id="ad1fe-156">N/A</span><span class="sxs-lookup"><span data-stu-id="ad1fe-156">N/A</span></span> | <span data-ttu-id="ad1fe-157">N/A</span><span class="sxs-lookup"><span data-stu-id="ad1fe-157">N/A</span></span> |
