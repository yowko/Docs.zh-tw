---
ms.openlocfilehash: c3114277445daaae988b41782721c443c1e780d1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496158"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF 會繁衍可以凍結滑鼠的 wisptis.exe 處理序

#### <a name="details"></a>詳細資料

在 4.5.2 中產生了一個問題，導致繁衍可凍結滑鼠輸入的 <code>wisptis.exe</code>。

#### <a name="suggestion"></a>建議

解決此問題的修正程式可在 .NET Framework 4.5.2 的服務版本 (Hotfix 彙總套件 3026376) 中取得，或藉由升級至 .NET Framework 4.6 取得

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |主要|
|版本|4.5.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
