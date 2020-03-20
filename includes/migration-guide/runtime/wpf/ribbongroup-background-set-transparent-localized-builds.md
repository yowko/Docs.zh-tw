---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802533"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>RibbonGroup 背景在當地語系化組建中設定為透明

|   |   |
|---|---|
|詳細資料|當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。 此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。|
|建議|升級至 .NET Framework 4.7|
|影響範圍|Edge|
|版本|4.6.2|
|類型|執行階段|
