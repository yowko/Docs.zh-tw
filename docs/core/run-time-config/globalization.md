---
title: 全球化設定
description: 瞭解設定 .NET Core 應用程式全球化層面的執行時間設定，例如，如何剖析日文日期。
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: fc98e965093c28b75b9b66e4f1c9f147abd4680e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721905"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="95e18-103">全球化的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="95e18-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="95e18-104">不變模式</span><span class="sxs-lookup"><span data-stu-id="95e18-104">Invariant mode</span></span>

- <span data-ttu-id="95e18-105">判斷 .NET Core 應用程式是否以全球化非變異模式執行，而不需存取特定文化特性的資料和行為。</span><span class="sxs-lookup"><span data-stu-id="95e18-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="95e18-106">如果您省略此設定，則會執行應用程式並存取文化特性資料。</span><span class="sxs-lookup"><span data-stu-id="95e18-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="95e18-107">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="95e18-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="95e18-108">如需詳細資訊，請參閱 [.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="95e18-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="95e18-109">設定名稱</span><span class="sxs-lookup"><span data-stu-id="95e18-109">Setting name</span></span> | <span data-ttu-id="95e18-110">值</span><span class="sxs-lookup"><span data-stu-id="95e18-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="95e18-111">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="95e18-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="95e18-112">`false` -文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="95e18-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="95e18-113">`true` -在不變模式中執行</span><span class="sxs-lookup"><span data-stu-id="95e18-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="95e18-114">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="95e18-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="95e18-115">`false` -文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="95e18-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="95e18-116">`true` -在不變模式中執行</span><span class="sxs-lookup"><span data-stu-id="95e18-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="95e18-117">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="95e18-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="95e18-118">`0` -文化特性資料的存取權</span><span class="sxs-lookup"><span data-stu-id="95e18-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="95e18-119">`1` -在不變模式中執行</span><span class="sxs-lookup"><span data-stu-id="95e18-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="95e18-120">範例</span><span class="sxs-lookup"><span data-stu-id="95e18-120">Examples</span></span>

<span data-ttu-id="95e18-121">*runtimeconfig.json* file：</span><span class="sxs-lookup"><span data-stu-id="95e18-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="95e18-122">專案檔：</span><span class="sxs-lookup"><span data-stu-id="95e18-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="95e18-123">紀元年份範圍</span><span class="sxs-lookup"><span data-stu-id="95e18-123">Era year ranges</span></span>

- <span data-ttu-id="95e18-124">決定是否要放寬支援多個紀元之行事曆的範圍檢查，或是否會擲回某紀元日期範圍溢位的日期 <xref:System.ArgumentOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="95e18-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="95e18-125">如果您省略此設定，則會放寬範圍檢查。</span><span class="sxs-lookup"><span data-stu-id="95e18-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="95e18-126">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="95e18-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="95e18-127">如需詳細資訊，請參閱行事 [曆、紀元和日期範圍：寬鬆的範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。</span><span class="sxs-lookup"><span data-stu-id="95e18-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="95e18-128">設定名稱</span><span class="sxs-lookup"><span data-stu-id="95e18-128">Setting name</span></span> | <span data-ttu-id="95e18-129">值</span><span class="sxs-lookup"><span data-stu-id="95e18-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="95e18-130">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="95e18-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="95e18-131">`false` -寬鬆範圍檢查</span><span class="sxs-lookup"><span data-stu-id="95e18-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="95e18-132">`true` -溢位會造成例外狀況</span><span class="sxs-lookup"><span data-stu-id="95e18-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="95e18-133">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="95e18-133">**Environment variable**</span></span> | <span data-ttu-id="95e18-134">N/A</span><span class="sxs-lookup"><span data-stu-id="95e18-134">N/A</span></span> | <span data-ttu-id="95e18-135">N/A</span><span class="sxs-lookup"><span data-stu-id="95e18-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="95e18-136">日文日期剖析</span><span class="sxs-lookup"><span data-stu-id="95e18-136">Japanese date parsing</span></span>

- <span data-ttu-id="95e18-137">判斷是否成功剖析包含 "1" 或 "Gannen" 的字串，或是否只支援 "1"。</span><span class="sxs-lookup"><span data-stu-id="95e18-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="95e18-138">如果您省略此設定，則會成功剖析包含 "1" 或 "Gannen" 的字串。</span><span class="sxs-lookup"><span data-stu-id="95e18-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="95e18-139">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="95e18-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="95e18-140">如需詳細資訊，請參閱 [使用多個紀元表示日曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="95e18-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="95e18-141">設定名稱</span><span class="sxs-lookup"><span data-stu-id="95e18-141">Setting name</span></span> | <span data-ttu-id="95e18-142">值</span><span class="sxs-lookup"><span data-stu-id="95e18-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="95e18-143">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="95e18-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="95e18-144">`false` -支援 "Gannen" 或 "1"</span><span class="sxs-lookup"><span data-stu-id="95e18-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="95e18-145">`true` -只支援 "1"</span><span class="sxs-lookup"><span data-stu-id="95e18-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="95e18-146">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="95e18-146">**Environment variable**</span></span> | <span data-ttu-id="95e18-147">N/A</span><span class="sxs-lookup"><span data-stu-id="95e18-147">N/A</span></span> | <span data-ttu-id="95e18-148">N/A</span><span class="sxs-lookup"><span data-stu-id="95e18-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="95e18-149">日文年份格式</span><span class="sxs-lookup"><span data-stu-id="95e18-149">Japanese year format</span></span>

- <span data-ttu-id="95e18-150">判斷日文日曆紀元的第一年是否格式化為 "Gannen" 或數位。</span><span class="sxs-lookup"><span data-stu-id="95e18-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="95e18-151">如果您省略此設定，則第一年的格式會是 "Gannen"。</span><span class="sxs-lookup"><span data-stu-id="95e18-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="95e18-152">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="95e18-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="95e18-153">如需詳細資訊，請參閱 [使用多個紀元表示日曆中的日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="95e18-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="95e18-154">設定名稱</span><span class="sxs-lookup"><span data-stu-id="95e18-154">Setting name</span></span> | <span data-ttu-id="95e18-155">值</span><span class="sxs-lookup"><span data-stu-id="95e18-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="95e18-156">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="95e18-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="95e18-157">`false` -格式為 "Gannen"</span><span class="sxs-lookup"><span data-stu-id="95e18-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="95e18-158">`true` -格式為數字</span><span class="sxs-lookup"><span data-stu-id="95e18-158">`true` - format as number</span></span> |
| <span data-ttu-id="95e18-159">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="95e18-159">**Environment variable**</span></span> | <span data-ttu-id="95e18-160">N/A</span><span class="sxs-lookup"><span data-stu-id="95e18-160">N/A</span></span> | <span data-ttu-id="95e18-161">N/A</span><span class="sxs-lookup"><span data-stu-id="95e18-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="95e18-162">Nls</span><span class="sxs-lookup"><span data-stu-id="95e18-162">NLS</span></span>

- <span data-ttu-id="95e18-163">判斷 .NET 是否針對 Unicode (ICU) 適用于 Windows 應用程式的全球化 Api，使用國家語言支援 (NLS) 或國際元件。</span><span class="sxs-lookup"><span data-stu-id="95e18-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="95e18-164">.NET 5.0 和更新版本預設會在 Windows 10 2019 年5月更新和更新版本上使用 ICU 全球化 Api。</span><span class="sxs-lookup"><span data-stu-id="95e18-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="95e18-165">如果您省略此設定，.NET 預設會使用 ICU 全球化 Api。</span><span class="sxs-lookup"><span data-stu-id="95e18-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="95e18-166">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="95e18-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="95e18-167">如需詳細資訊，請參閱 [全球化 api 在 Windows 上使用 ICU 程式庫](../compatibility/globalization/5.0/icu-globalization-api.md)。</span><span class="sxs-lookup"><span data-stu-id="95e18-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

| | <span data-ttu-id="95e18-168">設定名稱</span><span class="sxs-lookup"><span data-stu-id="95e18-168">Setting name</span></span> | <span data-ttu-id="95e18-169">值</span><span class="sxs-lookup"><span data-stu-id="95e18-169">Values</span></span> | <span data-ttu-id="95e18-170">推出的版本</span><span class="sxs-lookup"><span data-stu-id="95e18-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="95e18-171">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="95e18-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="95e18-172">`false` -使用 ICU 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="95e18-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="95e18-173">`true` -使用 NLS 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="95e18-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="95e18-174">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="95e18-174">.NET 5.0</span></span> |
| <span data-ttu-id="95e18-175">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="95e18-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="95e18-176">`false` -使用 ICU 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="95e18-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="95e18-177">`true` -使用 NLS 全球化 Api</span><span class="sxs-lookup"><span data-stu-id="95e18-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="95e18-178">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="95e18-178">.NET 5.0</span></span> |
