---
ms.openlocfilehash: 5c8ea3565fbe599dd53a71ba8bd339704f7d7f8a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496399"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="996f3-101">SignedXml 和 EncryptedXml 重大變更</span><span class="sxs-lookup"><span data-stu-id="996f3-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="996f3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="996f3-102">Details</span></span>

<span data-ttu-id="996f3-103">在 .NET Framework 4.6.2 中，<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> 和 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> 的安全性修正會導致不同的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="996f3-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="996f3-104">例如，</span><span class="sxs-lookup"><span data-stu-id="996f3-104">For example,</span></span><ul><li><span data-ttu-id="996f3-105">如果文件具有包含相同 <code>id</code> 屬性的多個項目，且簽章將目標設為這些項目之一以作為簽章的根項目，該文件現在會視為無效。</span><span class="sxs-lookup"><span data-stu-id="996f3-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="996f3-106">在參考中使用非標準 XPath 轉換演算法的文件現在都視為無效。</span><span class="sxs-lookup"><span data-stu-id="996f3-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="996f3-107">在參考中使用非標準 XSLT 轉換演算法的文件現在會視為無效。</span><span class="sxs-lookup"><span data-stu-id="996f3-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="996f3-108">任何使用外部資源中斷簽章的程式都無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="996f3-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="996f3-109">建議</span><span class="sxs-lookup"><span data-stu-id="996f3-109">Suggestion</span></span>

<span data-ttu-id="996f3-110">開發人員可能想要檢閱 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> 和 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>，以及衍生自 <xref:System.Security.Cryptography.Xml.Transform> 之類型的使用方式，因為文件收件者可能無法處理它。</span><span class="sxs-lookup"><span data-stu-id="996f3-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="996f3-111">名稱</span><span class="sxs-lookup"><span data-stu-id="996f3-111">Name</span></span>    | <span data-ttu-id="996f3-112">值</span><span class="sxs-lookup"><span data-stu-id="996f3-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="996f3-113">範圍</span><span class="sxs-lookup"><span data-stu-id="996f3-113">Scope</span></span>   |<span data-ttu-id="996f3-114">Minor</span><span class="sxs-lookup"><span data-stu-id="996f3-114">Minor</span></span>|
|<span data-ttu-id="996f3-115">版本</span><span class="sxs-lookup"><span data-stu-id="996f3-115">Version</span></span>|<span data-ttu-id="996f3-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="996f3-116">4.6.2</span></span>|
|<span data-ttu-id="996f3-117">類型</span><span class="sxs-lookup"><span data-stu-id="996f3-117">Type</span></span>|<span data-ttu-id="996f3-118">執行階段</span><span class="sxs-lookup"><span data-stu-id="996f3-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="996f3-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="996f3-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.Xml.Transform`
- `T:System.Security.Cryptography.Xml.XmlDsigXPathTransform`
- `T:System.Security.Cryptography.Xml.XmlDsigXsltTransform`

-->
