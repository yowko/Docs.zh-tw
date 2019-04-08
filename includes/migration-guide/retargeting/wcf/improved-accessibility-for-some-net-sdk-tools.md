---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760203"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>某些 .NET SDK 工具之改善的協助工具

|   |   |
|---|---|
|詳細資料|在 .NET Framework SDK 4.7.1 中，SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具已透過修正不同的協助工具問題而得到改善。 其中大部分是小問題，例如未定義名稱，或未正確實作某些 UI 自動化模式。 雖然許多使用者並未注意到這些不正確的值，但使用螢幕助讀程式等輔助技術的客戶會發現這些 SDK 工具更易於存取。 當然，這些修正程式會變更一些先前的行為，例如鍵盤焦點順序。為了取得這些工具的所有協助工具修正程式，您可以將下列程式碼新增至 app.config 檔案：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7.1|
|類型|正在重定目標|

