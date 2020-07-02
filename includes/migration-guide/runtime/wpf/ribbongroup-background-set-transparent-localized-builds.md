---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622342"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>RibbonGroup 背景在當地語系化組建中設定為透明

#### <a name="details"></a>詳細資料

當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。 此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。

#### <a name="suggestion"></a>建議

升級至 .NET Framework 4.7

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.6.2|
|類型|執行階段|
