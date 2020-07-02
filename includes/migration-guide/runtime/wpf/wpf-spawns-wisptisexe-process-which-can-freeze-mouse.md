---
ms.openlocfilehash: e0f72d19a884087b1f0f6ebd1b6baea75bc37af4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620104"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF 會繁衍可以凍結滑鼠的 wisptis.exe 處理序

#### <a name="details"></a>詳細資料

在 4.5.2 中產生了一個問題，導致繁衍可凍結滑鼠輸入的 <code>wisptis.exe</code>。

#### <a name="suggestion"></a>建議

解決此問題的修正程式可在 .NET Framework 4.5.2 的服務版本 (Hotfix 彙總套件 3026376) 中取得，或藉由升級至 .NET Framework 4.6 取得

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.5.2|
|類型|執行階段|
