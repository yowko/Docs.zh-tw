---
ms.openlocfilehash: 2413e1997b6e729b9d5889677e25254aaa24afea
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859260"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor.Equals 的實作不正確

|   |   |
|---|---|
|詳細資料|<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 方法的原始實作會比較正在比較之物件的兩個不同字串屬性：分類名稱與描述字串。 修正方法是比較第一個物件的 <xref:System.ComponentModel.MemberDescriptor.Category> 和第二個物件的 <xref:System.ComponentModel.MemberDescriptor.Category>，比較第一個物件的 <xref:System.ComponentModel.MemberDescriptor.Description> 和第二個物件的 <xref:System.ComponentModel.MemberDescriptor.Description>。|
|建議|如果您的應用程式相依於當描述項相等時有時會傳回 <code>false</code> 的 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>，而且您的目標是 .NET Framework 4.6.2 版或更新版本，則有數個選項：<ol><li>變更程式碼以在呼叫 <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> 方法之外，手動比較 <xref:System.ComponentModel.MemberDescriptor.Category> 和 <xref:System.ComponentModel.MemberDescriptor.Description> 欄位。</li><li>在 app.config 檔案中新增下列值，選擇不進行這項變更：</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>如果您的應用程式目標設為 .NET Framework 4.6.1 或較舊版本，但在 .NET Framework 4.6.2 或更新版本上執行，而您想要啟用這項變更，您可以在 app.config 檔案中新增下列值，將相容性參數設為 <code>false</code>：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.6.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

