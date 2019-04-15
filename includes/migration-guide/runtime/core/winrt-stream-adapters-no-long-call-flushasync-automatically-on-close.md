---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235309"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT 資料流配接器不會再於關閉時自動呼叫 FlushAsync

|   |   |
|---|---|
|詳細資料|在 Windows 市集應用程式中，Windows 執行階段資料流配接器不會再從 Dispose 方法呼叫 FlushAsync 方法。|
|建議|這項變更應該是透明的。 開發人員可以撰寫下列程式碼來還原舊有行為：<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|範圍|透明|
|版本|4.5.1|
|類型|執行階段|
