---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116332"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="7b72c-101">微軟.VisualBasic.Constants.vbNewline已經過時</span><span class="sxs-lookup"><span data-stu-id="7b72c-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="7b72c-102">常<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>量標記為[\[從\]](xref:System.ObsoleteAttribute).NET 核心 3.0 預覽 8 開始的過時。</span><span class="sxs-lookup"><span data-stu-id="7b72c-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7b72c-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="7b72c-103">Version introduced</span></span>

<span data-ttu-id="7b72c-104">3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="7b72c-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="7b72c-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="7b72c-105">Change description</span></span>

<span data-ttu-id="7b72c-106">從 .NET Core 3.0 預覽 8 開始，已將<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>["過時"](xref:System.ObsoleteAttribute)屬性應用於常量。</span><span class="sxs-lookup"><span data-stu-id="7b72c-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="7b72c-107">使用常量會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="7b72c-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="7b72c-108">在 .NET 框架和 .NET Core 的早期版本中，它未標記為過時。</span><span class="sxs-lookup"><span data-stu-id="7b72c-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="7b72c-109">進行此更改是為了支援 Visual Basic 作為多平臺開發語言。</span><span class="sxs-lookup"><span data-stu-id="7b72c-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="7b72c-110">常<xref:Microsoft.VisualBasic.Constants.vbNewLine>量等效于`\r\n`Windows 上的折線字元序列。</span><span class="sxs-lookup"><span data-stu-id="7b72c-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="7b72c-111">在基於 Unix 的系統上，新線字元`\n`為 。</span><span class="sxs-lookup"><span data-stu-id="7b72c-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7b72c-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7b72c-112">Recommended action</span></span>

<span data-ttu-id="7b72c-113"><xref:Microsoft.VisualBasic.Constants.vbNewLine>的["過時](xref:System.ObsoleteAttribute)屬性"消息包括以下建議：</span><span class="sxs-lookup"><span data-stu-id="7b72c-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="7b72c-114">對於回車和換行，請使用<xref:Microsoft.VisualBasic.Constants.vbCrLf>。</span><span class="sxs-lookup"><span data-stu-id="7b72c-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="7b72c-115">對於當前平臺的新線，請使用<xref:System.Environment.NewLine?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7b72c-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="7b72c-116">類別</span><span class="sxs-lookup"><span data-stu-id="7b72c-116">Category</span></span>

<span data-ttu-id="7b72c-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b72c-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7b72c-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7b72c-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
