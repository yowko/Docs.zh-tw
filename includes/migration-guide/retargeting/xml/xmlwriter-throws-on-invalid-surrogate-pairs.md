---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615631"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="06c6c-101">無效的代理字組會擲回 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="06c6c-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="06c6c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="06c6c-102">Details</span></span>

<span data-ttu-id="06c6c-103">針對以 .NET Framework 4.5.2 或之前版本為目標的應用程式，使用例外狀況後援處理寫入無效的 Surrogate 字組時不一定每次都會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="06c6c-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="06c6c-104">針對以 .NET Framework 4.6 為目標的應用程式，嘗試寫入無效的代理字組會擲回 <xref:System.ArgumentException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="06c6c-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="06c6c-105">建議</span><span class="sxs-lookup"><span data-stu-id="06c6c-105">Suggestion</span></span>

<span data-ttu-id="06c6c-106">如有必要，可以將目標設為 .NET Framework 4.5.2 或更早版本以避免這項中斷。</span><span class="sxs-lookup"><span data-stu-id="06c6c-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="06c6c-107">或者，可以將無效的代理字組字組預先處理成有效的 XML，再寫入它們。</span><span class="sxs-lookup"><span data-stu-id="06c6c-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="06c6c-108">名稱</span><span class="sxs-lookup"><span data-stu-id="06c6c-108">Name</span></span>    | <span data-ttu-id="06c6c-109">值</span><span class="sxs-lookup"><span data-stu-id="06c6c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="06c6c-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="06c6c-110">Scope</span></span>   | <span data-ttu-id="06c6c-111">Edge</span><span class="sxs-lookup"><span data-stu-id="06c6c-111">Edge</span></span>        |
| <span data-ttu-id="06c6c-112">版本</span><span class="sxs-lookup"><span data-stu-id="06c6c-112">Version</span></span> | <span data-ttu-id="06c6c-113">4.6</span><span class="sxs-lookup"><span data-stu-id="06c6c-113">4.6</span></span>         |
| <span data-ttu-id="06c6c-114">類型</span><span class="sxs-lookup"><span data-stu-id="06c6c-114">Type</span></span>    | <span data-ttu-id="06c6c-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="06c6c-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="06c6c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="06c6c-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
