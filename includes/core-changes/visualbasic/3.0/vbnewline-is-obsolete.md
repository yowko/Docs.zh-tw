---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555902"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="e4ade-101">VbNewLine 已被淘汰</span><span class="sxs-lookup"><span data-stu-id="e4ade-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="e4ade-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>從 .Net Core 3.0 開始，常數會標示為[ \[ 過時 \] ](xref:System.ObsoleteAttribute) 。</span><span class="sxs-lookup"><span data-stu-id="e4ade-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e4ade-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e4ade-103">Version introduced</span></span>

<span data-ttu-id="e4ade-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e4ade-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="e4ade-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="e4ade-105">Change description</span></span>

<span data-ttu-id="e4ade-106">從 .NET Core 3.0 開始，已將 [過時](xref:System.ObsoleteAttribute) 的屬性套用到 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常數。</span><span class="sxs-lookup"><span data-stu-id="e4ade-106">Starting with .NET Core 3.0, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="e4ade-107">使用常數會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="e4ade-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="e4ade-108">在 .NET Framework 和舊版的 .NET Core 中，它並未標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="e4ade-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="e4ade-109">這是為了支援 Visual Basic 做為多平臺開發的語言而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="e4ade-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="e4ade-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine>常數相當於 `\r\n` Windows 上的換行字元序列。</span><span class="sxs-lookup"><span data-stu-id="e4ade-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="e4ade-111">在以 Unix 為基礎的系統上，換行字元是 `\n` 。</span><span class="sxs-lookup"><span data-stu-id="e4ade-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e4ade-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e4ade-112">Recommended action</span></span>

<span data-ttu-id="e4ade-113">的 [過時](xref:System.ObsoleteAttribute) 屬性訊息 <xref:Microsoft.VisualBasic.Constants.vbNewLine> 包含下列建議：</span><span class="sxs-lookup"><span data-stu-id="e4ade-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="e4ade-114">若為換行字元和換行字元，請使用 <xref:Microsoft.VisualBasic.Constants.vbCrLf> 。</span><span class="sxs-lookup"><span data-stu-id="e4ade-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="e4ade-115">針對目前平臺的新行，請使用 <xref:System.Environment.NewLine?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e4ade-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="e4ade-116">類別</span><span class="sxs-lookup"><span data-stu-id="e4ade-116">Category</span></span>

<span data-ttu-id="e4ade-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4ade-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e4ade-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e4ade-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
