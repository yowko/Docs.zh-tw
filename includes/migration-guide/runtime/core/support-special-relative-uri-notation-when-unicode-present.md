---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621071"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode 存在時，支援特殊的相對 URI 標記法

#### <a name="details"></a>詳細資料

<xref:System.Uri>在 <xref:System.NullReferenceException> <xref:System.Uri.TryCreate%2A> 包含 Unicode 的某些相對 uri 上呼叫時，不會再擲回。 下面是最簡單的複製 <xref:System.NullReferenceException> ，其中兩個語句是相等的：<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>若要重現 <xref:System.NullReferenceException>，必須符合下列項目：<ul><li>URI 前面必須加上 ‘http:’，且不是後面加上 ‘//’ 來指定為相對的。</li><li>URI 必須包含百分比編碼的 Unicode 或未保留的符號。</li></ul>

#### <a name="suggestion"></a>建議

根據此行為不允許相對 URI 的使用者，在建立 URI 時應該改指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.7.2|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
