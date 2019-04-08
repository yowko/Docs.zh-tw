---
ms.openlocfilehash: 63a38f33fef09577c5ed621727b8c38e4c7e1bdf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760803"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>現在，WPF 標記編譯器的預設雜湊演算法是 SHA256

|   |   |
|---|---|
|詳細資料|WPF 標記編譯器提供 XAML 標記檔案的編譯服務。  在 .NET Framework 4.7.1 和舊版本中，用於總和檢查碼的預設演算法是 SHA1。 但由於最近對 SHA1 產生的安全性顧慮，因此從 .NET Framework 4.7.2 開始，這個預設已變更為 SHA256。  這項變更會影響標記檔案在編譯期間產生的所有總和檢查碼。|
|建議|如果開發人員是以 .NET Framework 4.7.2 或更新版本為目標，並想還原到 SHA1 雜湊行為，則必須設定下列 AppContext 旗標。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>如果開發人員想要利用 SHA256 雜湊，同時以 .NET 4.7.2 以下的 Framework 版本為目標，則必須設定下列 AppContext 旗標。  請注意，安裝的 .NET Framework 版本必須為 4.7.2 或更新版本。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|透明|
|版本|4.7.2|
|類型|正在重定目標|

