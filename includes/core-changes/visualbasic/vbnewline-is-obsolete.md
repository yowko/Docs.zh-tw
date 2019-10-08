---
ms.openlocfilehash: f7c13688236f3d66f3225ecf5d93b4c3284e2e71
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002863"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="31647-101">VbNewLine 已過時。</span><span class="sxs-lookup"><span data-stu-id="31647-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="31647-102">從 .NET Core 3.0 Preview 8 開始，@no__t 0 常數會標示為[過時](xref:System.ObsoleteAttribute)。</span><span class="sxs-lookup"><span data-stu-id="31647-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="31647-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="31647-103">Version introduced</span></span>

<span data-ttu-id="31647-104">3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="31647-104">3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="31647-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31647-105">Details</span></span>

<span data-ttu-id="31647-106">從 .NET Core 3.0 Preview 8 開始，已將[過時](xref:System.ObsoleteAttribute)屬性套用至 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數。</span><span class="sxs-lookup"><span data-stu-id="31647-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="31647-107">使用常數會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="31647-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="31647-108">在舊版的 .NET Core 和 .NET Framework 中，它未標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="31647-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="31647-109">這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="31647-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="31647-110">@No__t-0 常數相當於 `\r\n`，也就是 Windows 上的分行符號序列。</span><span class="sxs-lookup"><span data-stu-id="31647-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="31647-111">在以 Unix 為基礎的系統上，分行符號為 `\n`。</span><span class="sxs-lookup"><span data-stu-id="31647-111">On Unix-based systems, the newline character is `\n`.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="31647-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="31647-112">Recommended action</span></span>

<span data-ttu-id="31647-113">@No__t-1 的[過時](xref:System.ObsoleteAttribute)屬性訊息包含下列建議：</span><span class="sxs-lookup"><span data-stu-id="31647-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="31647-114">若為回車和換行，請使用[vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)。</span><span class="sxs-lookup"><span data-stu-id="31647-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="31647-115">針對目前平臺的新行，請使用 <xref:System.Environment.NewLine?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="31647-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="31647-116">Category</span><span class="sxs-lookup"><span data-stu-id="31647-116">Category</span></span>

<span data-ttu-id="31647-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31647-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31647-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="31647-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

