---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496722"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>RibbonGroup 背景在當地語系化組建中設定為透明

#### <a name="details"></a>詳細資料

當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。 此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。

#### <a name="suggestion"></a>建議

升級至 .NET Framework 4.7

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.6.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
