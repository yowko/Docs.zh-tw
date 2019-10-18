---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522660"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="f3086-101">VbNewLine 已過時。</span><span class="sxs-lookup"><span data-stu-id="f3086-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="f3086-102">從 .NET Core 3.0 Preview 8 開始，<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數已標記為[過時](xref:System.ObsoleteAttribute)。</span><span class="sxs-lookup"><span data-stu-id="f3086-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f3086-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f3086-103">Version introduced</span></span>

<span data-ttu-id="f3086-104">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f3086-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="f3086-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="f3086-105">Change description</span></span>

<span data-ttu-id="f3086-106">從 .NET Core 3.0 Preview 8 開始，已將[過時](xref:System.ObsoleteAttribute)屬性套用至 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數。</span><span class="sxs-lookup"><span data-stu-id="f3086-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="f3086-107">使用常數會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="f3086-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="f3086-108">在舊版的 .NET Core 和 .NET Framework 中，它未標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="f3086-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="f3086-109">這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="f3086-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="f3086-110">@No__t_0 常數相當於 `\r\n`，也就是 Windows 上的分行符號序列。</span><span class="sxs-lookup"><span data-stu-id="f3086-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="f3086-111">在以 Unix 為基礎的系統上，換行字元是 `\n`。</span><span class="sxs-lookup"><span data-stu-id="f3086-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f3086-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f3086-112">Recommended action</span></span>

<span data-ttu-id="f3086-113">@No__t_1 的[過時](xref:System.ObsoleteAttribute)屬性訊息包含下列建議：</span><span class="sxs-lookup"><span data-stu-id="f3086-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="f3086-114">若為回車和換行，請使用[vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)。</span><span class="sxs-lookup"><span data-stu-id="f3086-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="f3086-115">針對目前平臺的新行，請使用 <xref:System.Environment.NewLine?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f3086-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="f3086-116">Category</span><span class="sxs-lookup"><span data-stu-id="f3086-116">Category</span></span>

<span data-ttu-id="f3086-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3086-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f3086-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f3086-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
