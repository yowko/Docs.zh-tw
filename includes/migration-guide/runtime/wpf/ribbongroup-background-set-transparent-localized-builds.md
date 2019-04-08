---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760611"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>RibbonGroup 背景在當地語系化組建中設定為透明

|   |   |
|---|---|
|詳細資料|當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。 此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。|
|建議|升級至 .NET Framework 4.7|
|範圍|Edge|
|版本|4.6.2|
|類型|執行階段|

