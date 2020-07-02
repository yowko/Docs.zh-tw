---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619983"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>在 4.0 行為中遺漏目標 Framework Moniker 結果

#### <a name="details"></a>詳細資料

未在組件層級套用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 的應用程式將會使用 .NET Framework 4.0 的語意 (Quirks) 來自動執行。 為了確保有高品質，建議明確設定所有二進位檔的 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 屬性，以指出用來建置的 .NET Framework 版本。 請注意，在專案檔中使用目標 Framework Moniker 會使 MSBuild 自動套用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

您應該透過直接將屬性新增至組件，或藉由[在專案檔中或透過 Visual Studio 的專案屬性 GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/) 來指定目標 Framework，以提供 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.5|
|類型|執行階段|
