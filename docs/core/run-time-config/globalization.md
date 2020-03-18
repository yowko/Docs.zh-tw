---
title: 全球化配置設置
description: 瞭解配置 .NET Core 應用的全球化方面的運行時設置，例如，它如何分析日語日期。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733461"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="1edde-103">全球化的運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="1edde-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="1edde-104">不變模式</span><span class="sxs-lookup"><span data-stu-id="1edde-104">Invariant mode</span></span>

- <span data-ttu-id="1edde-105">確定 .NET Core 應用是否以全球化不變模式運行，而不訪問特定于區域性的資料和行為，或者它是否有權訪問文化資料。</span><span class="sxs-lookup"><span data-stu-id="1edde-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="1edde-106">預設值：使用訪問文化資料 （）`false`運行應用。</span><span class="sxs-lookup"><span data-stu-id="1edde-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="1edde-107">有關詳細資訊，請參閱[.NET 核心全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1edde-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="1edde-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1edde-108">Setting name</span></span> | <span data-ttu-id="1edde-109">值</span><span class="sxs-lookup"><span data-stu-id="1edde-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1edde-110">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="1edde-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="1edde-111">`false`- 獲取文化資料</span><span class="sxs-lookup"><span data-stu-id="1edde-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="1edde-112">`true`- 在不變模式下運行</span><span class="sxs-lookup"><span data-stu-id="1edde-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="1edde-113">**MSBuild 屬性**</span><span class="sxs-lookup"><span data-stu-id="1edde-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="1edde-114">`false`- 獲取文化資料</span><span class="sxs-lookup"><span data-stu-id="1edde-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="1edde-115">`true`- 在不變模式下運行</span><span class="sxs-lookup"><span data-stu-id="1edde-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="1edde-116">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1edde-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="1edde-117">`0`- 獲取文化資料</span><span class="sxs-lookup"><span data-stu-id="1edde-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="1edde-118">`1`- 在不變模式下運行</span><span class="sxs-lookup"><span data-stu-id="1edde-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="1edde-119">範例</span><span class="sxs-lookup"><span data-stu-id="1edde-119">Examples</span></span>

<span data-ttu-id="1edde-120">*運行時配置.json*檔：</span><span class="sxs-lookup"><span data-stu-id="1edde-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="1edde-121">專案檔：</span><span class="sxs-lookup"><span data-stu-id="1edde-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="1edde-122">時代年份範圍</span><span class="sxs-lookup"><span data-stu-id="1edde-122">Era year ranges</span></span>

- <span data-ttu-id="1edde-123">確定是否放寬了對支援多個紀元日曆的日曆的範圍檢查，或者溢出一個時代日期範圍的日期是否引發 。 <xref:System.ArgumentOutOfRangeException></span><span class="sxs-lookup"><span data-stu-id="1edde-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="1edde-124">預設值：放寬範圍檢查 （）。`false`</span><span class="sxs-lookup"><span data-stu-id="1edde-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="1edde-125">有關詳細資訊，請參閱[日曆、時數和日期範圍：放寬範圍檢查](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)。</span><span class="sxs-lookup"><span data-stu-id="1edde-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="1edde-126">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1edde-126">Setting name</span></span> | <span data-ttu-id="1edde-127">值</span><span class="sxs-lookup"><span data-stu-id="1edde-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1edde-128">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="1edde-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="1edde-129">`false`- 輕鬆範圍檢查</span><span class="sxs-lookup"><span data-stu-id="1edde-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="1edde-130">`true`- 溢出導致異常</span><span class="sxs-lookup"><span data-stu-id="1edde-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="1edde-131">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1edde-131">**Environment variable**</span></span> | <span data-ttu-id="1edde-132">N/A</span><span class="sxs-lookup"><span data-stu-id="1edde-132">N/A</span></span> | <span data-ttu-id="1edde-133">N/A</span><span class="sxs-lookup"><span data-stu-id="1edde-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="1edde-134">日語日期解析</span><span class="sxs-lookup"><span data-stu-id="1edde-134">Japanese date parsing</span></span>

- <span data-ttu-id="1edde-135">確定在年份解析時包含"1"或"Gannen"的字串是否成功解析，或者是否僅支援"1"。</span><span class="sxs-lookup"><span data-stu-id="1edde-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="1edde-136">預設值：將包含"1"或"Gannen"作為年份 （）`false`的字串解析。</span><span class="sxs-lookup"><span data-stu-id="1edde-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="1edde-137">有關詳細資訊，請參閱[在具有多個時代曆的日曆中表示日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="1edde-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="1edde-138">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1edde-138">Setting name</span></span> | <span data-ttu-id="1edde-139">值</span><span class="sxs-lookup"><span data-stu-id="1edde-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1edde-140">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="1edde-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="1edde-141">`false`- 支援"甘甯"或"1"</span><span class="sxs-lookup"><span data-stu-id="1edde-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="1edde-142">`true`- 僅支援"1"</span><span class="sxs-lookup"><span data-stu-id="1edde-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="1edde-143">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1edde-143">**Environment variable**</span></span> | <span data-ttu-id="1edde-144">N/A</span><span class="sxs-lookup"><span data-stu-id="1edde-144">N/A</span></span> | <span data-ttu-id="1edde-145">N/A</span><span class="sxs-lookup"><span data-stu-id="1edde-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="1edde-146">日語年格式</span><span class="sxs-lookup"><span data-stu-id="1edde-146">Japanese year format</span></span>

- <span data-ttu-id="1edde-147">確定日本日曆時代的第一年是格式化為"Gannen"還是數位。</span><span class="sxs-lookup"><span data-stu-id="1edde-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="1edde-148">預設值：將第一年設置為"Gannen"`false`（） 。</span><span class="sxs-lookup"><span data-stu-id="1edde-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="1edde-149">有關詳細資訊，請參閱[在具有多個時代曆的日曆中表示日期](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)。</span><span class="sxs-lookup"><span data-stu-id="1edde-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="1edde-150">設定名稱</span><span class="sxs-lookup"><span data-stu-id="1edde-150">Setting name</span></span> | <span data-ttu-id="1edde-151">值</span><span class="sxs-lookup"><span data-stu-id="1edde-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="1edde-152">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="1edde-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="1edde-153">`false`- 格式為"甘甯"</span><span class="sxs-lookup"><span data-stu-id="1edde-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="1edde-154">`true`- 格式為數字</span><span class="sxs-lookup"><span data-stu-id="1edde-154">`true` - format as number</span></span> |
| <span data-ttu-id="1edde-155">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="1edde-155">**Environment variable**</span></span> | <span data-ttu-id="1edde-156">N/A</span><span class="sxs-lookup"><span data-stu-id="1edde-156">N/A</span></span> | <span data-ttu-id="1edde-157">N/A</span><span class="sxs-lookup"><span data-stu-id="1edde-157">N/A</span></span> |
