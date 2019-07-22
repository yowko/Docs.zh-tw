---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235535"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>ImageSourceConverter.ConvertFrom 之例外狀況處理程式碼中的 NullReferenceException

|   |   |
|---|---|
|詳細資料|<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> 的例外狀況處理程式碼錯誤已導致擲回不正確的 <xref:System.NullReferenceException?displayProperty=name>，而不是預期的例外狀況 (<xref:System.IO.DirectoryNotFoundException?displayProperty=name> 或 <xref:System.IO.FileNotFoundException?displayProperty=name>)。 這項變更會修正該錯誤，讓該方法現在擲回正確的例外狀況。 <p/>根據預設，所有以 .NET Framework 4.6.2 和更早版本為目標的應用程式會繼續擲回 <xref:System.NullReferenceException?displayProperty=name> 以提供相容性。 以 .NET Framework 4.7 和以上版本為目標的開發人員應該會看到正確的例外狀況。|
|建議|開發人員若想要在以 .NET Framework 4.7 或更新版本為目標時還原成取得 <xref:System.NullReferenceException?displayProperty=name>，可以在其應用程式的 App.config 檔案中新增/合併下列程式碼：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
