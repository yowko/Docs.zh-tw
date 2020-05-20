---
title: 全球化 config 設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，它如何剖析日文日期。
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703123"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="2b952-103">全球化的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="2b952-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="2b952-104">不變模式</span><span class="sxs-lookup"><span data-stu-id="2b952-104">Invariant mode</span></span>

- <span data-ttu-id="2b952-105">判斷 .NET Core 應用程式是否以全球化不變模式執行，而不需要存取特定文化特性的資料和行為。</span><span class="sxs-lookup"><span data-stu-id="2b952-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="2b952-106">預設值：執行具有文化特性資料存取權的應用程式（ `false` ）。</span><span class="sxs-lookup"><span data-stu-id="2b952-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="2b952-107">如需詳細資訊，請參閱[.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="2b952-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="2b952-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2b952-108">Setting name</span></span> | <span data-ttu-id="2b952-109">值</span><span class="sxs-lookup"><span data-stu-id="2b952-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2b952-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2b952-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="2b952-111">`false`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="2b952-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="2b952-112">`true`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="2b952-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="2b952-113">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="2b952-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="2b952-114">`false`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="2b952-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="2b952-115">`true`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="2b952-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="2b952-116">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2b952-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="2b952-117">`0`-文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="2b952-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="2b952-118">`1`-在不變模式下執行</span><span class="sxs-lookup"><span data-stu-id="2b952-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="2b952-119">範例</span><span class="sxs-lookup"><span data-stu-id="2b952-119">Examples</span></span>

<span data-ttu-id="2b952-120">*.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="2b952-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="2b952-121">專案檔：</span><span class="sxs-lookup"><span data-stu-id="2b952-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="2b952-122">紀元年份範圍</span><span class="sxs-lookup"><span data-stu-id="2b952-122">Era year ranges</span></span>

- <span data-ttu-id="2b952-123">判斷支援多個紀元之行事曆的範圍檢查是否會放寬，或是否會擲回紀元日期範圍溢位的日期 <xref:System.ArgumentOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="2b952-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="2b952-124">預設值：範圍檢查是寬鬆的（ `false` ）。</span><span class="sxs-lookup"><span data-stu-id="2b952-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="2b952-125">如需詳細資訊，請參閱行事[曆、紀元和日期範圍：寬鬆範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。</span><span class="sxs-lookup"><span data-stu-id="2b952-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="2b952-126">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2b952-126">Setting name</span></span> | <span data-ttu-id="2b952-127">值</span><span class="sxs-lookup"><span data-stu-id="2b952-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2b952-128">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2b952-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="2b952-129">`false`-寬鬆範圍檢查</span><span class="sxs-lookup"><span data-stu-id="2b952-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="2b952-130">`true`-溢位造成例外狀況</span><span class="sxs-lookup"><span data-stu-id="2b952-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="2b952-131">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2b952-131">**Environment variable**</span></span> | <span data-ttu-id="2b952-132">N/A</span><span class="sxs-lookup"><span data-stu-id="2b952-132">N/A</span></span> | <span data-ttu-id="2b952-133">N/A</span><span class="sxs-lookup"><span data-stu-id="2b952-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="2b952-134">日文日期剖析</span><span class="sxs-lookup"><span data-stu-id="2b952-134">Japanese date parsing</span></span>

- <span data-ttu-id="2b952-135">判斷在年份中包含 "1" 或 "Gannen" 的字串是否已成功剖析，或是否只支援 "1"。</span><span class="sxs-lookup"><span data-stu-id="2b952-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="2b952-136">預設值：剖析包含 "1" 或 "Gannen" 做為年份（）的字串 `false` 。</span><span class="sxs-lookup"><span data-stu-id="2b952-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="2b952-137">如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="2b952-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="2b952-138">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2b952-138">Setting name</span></span> | <span data-ttu-id="2b952-139">值</span><span class="sxs-lookup"><span data-stu-id="2b952-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2b952-140">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2b952-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="2b952-141">`false`-支援 "Gannen" 或 "1"</span><span class="sxs-lookup"><span data-stu-id="2b952-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="2b952-142">`true`-僅支援 "1"</span><span class="sxs-lookup"><span data-stu-id="2b952-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="2b952-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2b952-143">**Environment variable**</span></span> | <span data-ttu-id="2b952-144">N/A</span><span class="sxs-lookup"><span data-stu-id="2b952-144">N/A</span></span> | <span data-ttu-id="2b952-145">N/A</span><span class="sxs-lookup"><span data-stu-id="2b952-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="2b952-146">日文年份格式</span><span class="sxs-lookup"><span data-stu-id="2b952-146">Japanese year format</span></span>

- <span data-ttu-id="2b952-147">決定日本日曆紀元的第一年是否格式化為 "Gannen" 或數位。</span><span class="sxs-lookup"><span data-stu-id="2b952-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="2b952-148">預設值：將第一年格式化為 "Gannen" （ `false` ）。</span><span class="sxs-lookup"><span data-stu-id="2b952-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="2b952-149">如需詳細資訊，請參閱[代表具有多個紀元之行事曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="2b952-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="2b952-150">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2b952-150">Setting name</span></span> | <span data-ttu-id="2b952-151">值</span><span class="sxs-lookup"><span data-stu-id="2b952-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="2b952-152">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2b952-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="2b952-153">`false`-格式為 "Gannen"</span><span class="sxs-lookup"><span data-stu-id="2b952-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="2b952-154">`true`-格式為數字</span><span class="sxs-lookup"><span data-stu-id="2b952-154">`true` - format as number</span></span> |
| <span data-ttu-id="2b952-155">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2b952-155">**Environment variable**</span></span> | <span data-ttu-id="2b952-156">N/A</span><span class="sxs-lookup"><span data-stu-id="2b952-156">N/A</span></span> | <span data-ttu-id="2b952-157">N/A</span><span class="sxs-lookup"><span data-stu-id="2b952-157">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="2b952-158">NLS</span><span class="sxs-lookup"><span data-stu-id="2b952-158">NLS</span></span>

- <span data-ttu-id="2b952-159">判斷 .NET 是否針對 Windows 應用程式使用適用于 Unicode （ICU）全球化 Api 的國家語言支援（NLS）或國際元件。</span><span class="sxs-lookup"><span data-stu-id="2b952-159">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="2b952-160">根據預設，.NET 5.0 和更新版本會在 Windows 10 2019 更新和更新版本上使用 ICU 全球化 Api。</span><span class="sxs-lookup"><span data-stu-id="2b952-160">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="2b952-161">如果您省略此設定，.NET 預設會使用 ICU 全球化 Api。</span><span class="sxs-lookup"><span data-stu-id="2b952-161">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="2b952-162">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="2b952-162">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="2b952-163">如需詳細資訊，請參閱[全球化 api 在 Windows 上使用 ICU 程式庫](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows)。</span><span class="sxs-lookup"><span data-stu-id="2b952-163">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="2b952-164">設定名稱</span><span class="sxs-lookup"><span data-stu-id="2b952-164">Setting name</span></span> | <span data-ttu-id="2b952-165">值</span><span class="sxs-lookup"><span data-stu-id="2b952-165">Values</span></span> | <span data-ttu-id="2b952-166">引導</span><span class="sxs-lookup"><span data-stu-id="2b952-166">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2b952-167">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="2b952-167">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="2b952-168">`false`-使用 ICU 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="2b952-168">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="2b952-169">`true`-使用 NLS 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="2b952-169">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="2b952-170">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="2b952-170">.NET 5.0</span></span> |
| <span data-ttu-id="2b952-171">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="2b952-171">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="2b952-172">`false`-使用 ICU 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="2b952-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="2b952-173">`true`-使用 NLS 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="2b952-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="2b952-174">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="2b952-174">.NET 5.0</span></span> |
