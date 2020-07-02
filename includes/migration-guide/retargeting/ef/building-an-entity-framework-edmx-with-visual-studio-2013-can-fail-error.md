---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615624"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>如果使用 EntityDeploySplit 或 EntityClean 工作，以 Visual Studio 2013 建置 Entity Framework edmx 可能會失敗，並出現錯誤 MSB4062

#### <a name="details"></a>詳細資料

MSBuild 12.0 工具 (隨附於 Visual Studio 2013) 已變更 MSBuild 檔案位置，導致舊版 Entity Framework 的目標檔案無效。 結果是 `EntityDeploySplit` 和 `EntityClean` 工作會失敗，因為找不到 `Microsoft.Data.Entity.Build.Tasks.dll`。 請注意，造成此中斷的原因是工具組 (MSBuild/VS) 變更，而不是 .NET Framework 變更。 只有在升級開發人員工具時才會發生此情況，若只是升級 .NET Framework 則不會發生。

#### <a name="suggestion"></a>建議

Entity Framework 的目標檔案已修正，從 .NET Framework 4.6 開始，可搭配新的 MSBuild 配置使用。 升級至該版 Framework 將會修正此問題。 或者，您也可以使用[此因應措施](https://stackoverflow.com/a/24249247/131944)來直接修補目標檔案。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.5.1       |
| 類型    | 正在重定目標 |
