---
ms.openlocfilehash: d33d75b4c2d9bc18844f66f1fcca1e2efc6f1eee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497740"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="985f0-101">XSLT 樣式表例外狀況訊息已變更</span><span class="sxs-lookup"><span data-stu-id="985f0-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="985f0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="985f0-102">Details</span></span>

<span data-ttu-id="985f0-103">在 .NET Framework 4.5 中，當 XSLT 檔太複雜時，錯誤訊息的文字是 &quot; 樣式表單太複雜。 &quot; 在先前的版本中，錯誤訊息是 &quot; XSLT 編譯錯誤。 &quot; 相依于錯誤訊息文字的應用程式程式碼將無法再運作。</span><span class="sxs-lookup"><span data-stu-id="985f0-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="985f0-104">不過，例外狀況類型會保持不變，因此這項變更應該不會產生實際影響。</span><span class="sxs-lookup"><span data-stu-id="985f0-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="985f0-105">建議</span><span class="sxs-lookup"><span data-stu-id="985f0-105">Suggestion</span></span>

<span data-ttu-id="985f0-106">請將依據此錯誤狀況之例外狀況訊息的任何應用程式程式碼更新為預期會有新訊息，或是 (甚至更佳的做法) 將程式碼更新為只依據尚未變更的例外狀況類型 (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>)。</span><span class="sxs-lookup"><span data-stu-id="985f0-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="985f0-107">名稱</span><span class="sxs-lookup"><span data-stu-id="985f0-107">Name</span></span>    | <span data-ttu-id="985f0-108">值</span><span class="sxs-lookup"><span data-stu-id="985f0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="985f0-109">範圍</span><span class="sxs-lookup"><span data-stu-id="985f0-109">Scope</span></span>   |<span data-ttu-id="985f0-110">Edge</span><span class="sxs-lookup"><span data-stu-id="985f0-110">Edge</span></span>|
|<span data-ttu-id="985f0-111">版本</span><span class="sxs-lookup"><span data-stu-id="985f0-111">Version</span></span>|<span data-ttu-id="985f0-112">4.5</span><span class="sxs-lookup"><span data-stu-id="985f0-112">4.5</span></span>|
|<span data-ttu-id="985f0-113">類型</span><span class="sxs-lookup"><span data-stu-id="985f0-113">Type</span></span>|<span data-ttu-id="985f0-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="985f0-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="985f0-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="985f0-115">Affected APIs</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`

-->
