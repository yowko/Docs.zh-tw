---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621156"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF 視窗在擴充到單一顯示器之外時呈現而不裁剪

#### <a name="details"></a>詳細資料

在 Windows 8 和更新版本中執行的 .NET Framework 4.6 多重監視器案例中，如果視窗擴充到單一顯示畫面之外，可呈現完整視窗而不會將其裁剪。 這與舊版 .NET Framework 不同，後者會在 WPF 視窗擴充到單一顯示畫面之外時裁剪該視窗。

#### <a name="suggestion"></a>建議

您可以在應用程式組態檔的 <code>&lt;appSettings&gt;</code> 中使用 <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> 項目，或在應用程式啟動時藉由設定 <code>EnableMultiMonitorDisplayClipping</code> 屬性，來明確設定這項行為 (不論是否裁剪)。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.6|
|類型|執行階段|
