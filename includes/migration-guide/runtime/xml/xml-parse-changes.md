---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009045"
---
### <a name="xml-parsing-changes"></a><span data-ttu-id="9b8d2-101">XML 剖析變更</span><span class="sxs-lookup"><span data-stu-id="9b8d2-101">XML parsing changes</span></span>

| <span data-ttu-id="9b8d2-102">名稱</span><span class="sxs-lookup"><span data-stu-id="9b8d2-102">Name</span></span>    | <span data-ttu-id="9b8d2-103">值</span><span class="sxs-lookup"><span data-stu-id="9b8d2-103">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="9b8d2-104">範圍</span><span class="sxs-lookup"><span data-stu-id="9b8d2-104">Scope</span></span>   | <span data-ttu-id="9b8d2-105">Minor</span><span class="sxs-lookup"><span data-stu-id="9b8d2-105">Minor</span></span>   |
| <span data-ttu-id="9b8d2-106">版本</span><span class="sxs-lookup"><span data-stu-id="9b8d2-106">Version</span></span> | <span data-ttu-id="9b8d2-107">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9b8d2-107">4.5.2</span></span>   |
| <span data-ttu-id="9b8d2-108">類型</span><span class="sxs-lookup"><span data-stu-id="9b8d2-108">Type</span></span>    | <span data-ttu-id="9b8d2-109">執行階段</span><span class="sxs-lookup"><span data-stu-id="9b8d2-109">Runtime</span></span> |

#### <a name="details"></a><span data-ttu-id="9b8d2-110">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9b8d2-110">Details</span></span>

<span data-ttu-id="9b8d2-111">基於安全性考慮，下列變更已引入 XML 剖析 API：</span><span class="sxs-lookup"><span data-stu-id="9b8d2-111">For security reasons, the following changes were introduced into XML parsing APIS:</span></span>

- <span data-ttu-id="9b8d2-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> 當初始化時，會設定為 10000000 <xref:System.Xml.XmlReaderSettings> 。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> is set to 10 million when <xref:System.Xml.XmlReaderSettings> is initialized.</span></span>
- <span data-ttu-id="9b8d2-113">根據預設，<xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> 是設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> is set to `null` by default.</span></span>

> [!NOTE]
> <span data-ttu-id="9b8d2-114"><xref:System.Xml.XmlReaderSettings> 所有 XML 剖析器都會使用，因此雖然這項變更有助於這 <xref:System.Xml.XmlReader> 種情況，但它也會影響其他案例。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-114"><xref:System.Xml.XmlReaderSettings> is used by all XML parsers, so while this change helps the <xref:System.Xml.XmlReader> case, it also affects other scenarios.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9b8d2-115">建議</span><span class="sxs-lookup"><span data-stu-id="9b8d2-115">Suggestion</span></span>

<span data-ttu-id="9b8d2-116">若要還原為先前的行為，您可以在登錄中設定值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-116">To revert to the previous behavior, you can set a value in the registry.</span></span> <span data-ttu-id="9b8d2-117">將名為的 DWORD 值新增至登錄機 `EnableLegacyXmlSettings` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` 碼，並將其值設定為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-117">Add a DWORD value named `EnableLegacyXmlSettings` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` registry key, and set its value to `1`.</span></span> <span data-ttu-id="9b8d2-118">您也可以改為在 HKEY_CURRENT_USER hive 中新增登錄值。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-118">You can also add the registry value in the HKEY_CURRENT_USER hive instead.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b8d2-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9b8d2-119">Affected APIs</span></span>

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

<span data-ttu-id="9b8d2-120">此外，任何相依于 <xref:System.Xml.XmlResolver> （直接或間接）的 XML API 都會受到影響。</span><span class="sxs-lookup"><span data-stu-id="9b8d2-120">In addition, any XML API that depends on <xref:System.Xml.XmlResolver>, either directly or indirectly, is affected.</span></span>

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
