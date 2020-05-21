---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721305"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="e9b79-101">VbNewLine 已過時。</span><span class="sxs-lookup"><span data-stu-id="e9b79-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="e9b79-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>從 .Net Core 3.0 Preview 8 開始，常數會標示為[ \[ 過時 \] ](xref:System.ObsoleteAttribute) 。</span><span class="sxs-lookup"><span data-stu-id="e9b79-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9b79-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e9b79-103">Version introduced</span></span>

<span data-ttu-id="e9b79-104">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e9b79-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="e9b79-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="e9b79-105">Change description</span></span>

<span data-ttu-id="e9b79-106">從 .NET Core 3.0 Preview 8 開始，已將[過時](xref:System.ObsoleteAttribute)屬性套用至 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數。</span><span class="sxs-lookup"><span data-stu-id="e9b79-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="e9b79-107">使用常數會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="e9b79-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="e9b79-108">在 .NET Framework 和舊版的 .NET Core 中，它未標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="e9b79-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="e9b79-109">這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="e9b79-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="e9b79-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine>常數相當於，也就是 `\r\n` Windows 上的分行符號序列。</span><span class="sxs-lookup"><span data-stu-id="e9b79-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="e9b79-111">在以 Unix 為基礎的系統上，換行字元是 `\n` 。</span><span class="sxs-lookup"><span data-stu-id="e9b79-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9b79-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e9b79-112">Recommended action</span></span>

<span data-ttu-id="e9b79-113">的[過時](xref:System.ObsoleteAttribute)屬性訊息 <xref:Microsoft.VisualBasic.Constants.vbNewLine> 包含下列建議：</span><span class="sxs-lookup"><span data-stu-id="e9b79-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="e9b79-114">若為回車和換行，請使用 <xref:Microsoft.VisualBasic.Constants.vbCrLf> 。</span><span class="sxs-lookup"><span data-stu-id="e9b79-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="e9b79-115">針對目前平臺的新行，請使用 <xref:System.Environment.NewLine?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e9b79-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="e9b79-116">類別</span><span class="sxs-lookup"><span data-stu-id="e9b79-116">Category</span></span>

<span data-ttu-id="e9b79-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9b79-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9b79-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e9b79-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
