---
ms.openlocfilehash: d374ded6a29ce815beeb26505010563a26d978e8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803520"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost 現在會在 DPI 變更期間正確調整子 HWND 的大小

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.7.2 和更早版本中，當 WPF 在個別監視器感知模式中執行時，裝載於 <xref:System.Windows.Interop.HwndHost> 內的控制項未在 DPI 變更後正確調整大小，例如將應用程式從某個監視器移至另一個監視器時。 此修正可確保裝載的控制項適當調整大小。|
|建議|為了讓應用程式受益於這些變更，應用程式必須於 .NET Framework 4.7.2 或更新版本執行，並且必須藉由將應用程式組態檔中 <code>&lt;runtime&gt;</code> 區段的 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)設為 <code>false</code> 來選擇使用此行為，如下列範例所示。<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|主要|
|版本|4.8|
|類型|正在重定目標|

