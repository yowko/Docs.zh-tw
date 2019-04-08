---
ms.openlocfilehash: a4f27c0b2bf95ed19e485881aba3c52073114117
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "52742385"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>邊界的 WPF 版面配置進位已變更

|   |   |
|---|---|
|詳細資料|邊界的進位方式以及邊界內部的框線和背景皆有所變更。 此變更的結果：<ul><li>項目寬度或高度的增減最多不超過一個像素。</li><li>物件的位置的位最多不超過一個像素。</li><li>置中項目的垂直或水平位移最多不超過一個像素。</li></ul>預設只有以 .NET Framework 4.6 為目標的應用程式才會啟用此新版面配置。|
|建議|由於此修改會停用高 DPI 之 WPF 控制項右側或底端的裁剪功能，因此，應用程式若是以舊版 .NET Framework 為目標，但要在 .NET Framework 4.6 上執行，可將下行加入 app.config 檔案中的 <code>&lt;runtime&gt;</code> 區段來選擇使用此新行為：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>應用程式若是以 .NET Framework 4.6 為目標，但想使用先前的配置演算法來呈現 WPF 控制項，可將下行新增至 app.config 檔案中的 <code>&lt;runtime&gt;</code> 區段，以執行此作業：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|

