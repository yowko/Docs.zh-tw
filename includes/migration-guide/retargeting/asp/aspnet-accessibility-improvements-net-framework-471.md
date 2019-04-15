---
ms.openlocfilehash: 347b6ccb3e986d820514159179c824c28907fc62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236409"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1 中的 ASP.NET 協助工具改進功能

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.7.1 開始，ASP.NET 已經改善 ASP.NET Web 控制項如何搭配 Visual Studio 中的協助工具技術，來更妥善支援 ASP.NET 客戶。  這些包括下列變更：<ul><li>在控制項中，實作遺漏 UI 協助工具模式的變更，例如在 [詳細資料檢視精靈] 的 [新增欄位] 對話方塊或 ListView 精靈的 [設定 ListView] 對話方塊。</li><li>改善高對比模式顯示的變更，例如資料頁面巡覽區欄位編輯器。</li><li>改善控制項鍵盤瀏覽體驗的變更，例如 DataPager 控制項 [編輯頁面巡覽區欄位精靈] 的 [欄位] 對話方塊、[設定 ObjectContext] 對話方塊，或 [設定資料來源精靈] 的 [設定資料選取項目] 對話方塊。</li></ul>|
|建議|<strong>如何選擇加入或退出這些變更</strong>為了讓 Visual Studio 設計工具可受益於這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。 Web 應用程式可以由下列任一種方式受益於這些變更：<ul><li>安裝 Visual Studio 2017 15.3 或更新版本中，依預設它會以下列 AppContext 參數支援新的協助工具功能。</li><li>藉由將 <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext 參數新增到 devenv.exe.config 檔案中的 <code>&lt;runtime&gt;</code> 區段，並將它設定為 <code>false</code>，選擇退出舊版協助工具行為，如下列範例所示。</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 <code>true</code>，選擇使用舊版的協助工具功能。|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
