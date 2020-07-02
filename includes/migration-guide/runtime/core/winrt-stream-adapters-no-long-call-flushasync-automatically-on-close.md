---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619995"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT 資料流配接器不會再於關閉時自動呼叫 FlushAsync

#### <a name="details"></a>詳細資料

在 Windows 市集應用程式中，Windows 執行階段資料流配接器不會再從 Dispose 方法呼叫 FlushAsync 方法。

#### <a name="suggestion"></a>建議

這項變更應該是透明的。 開發人員可以撰寫下列程式碼來還原舊有行為：<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |透明|
|版本|4.5.1|
|類型|執行階段|
