---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400628"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="05f46-101">TextFormatFlags. ModifyString 已淘汰</span><span class="sxs-lookup"><span data-stu-id="05f46-101">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="05f46-102">此 <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 欄位已淘汰，以警告形式出現，而且可能會在未來的 .net 版本中移除。</span><span class="sxs-lookup"><span data-stu-id="05f46-102">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="05f46-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="05f46-103">Change description</span></span>

<span data-ttu-id="05f46-104">在先前的 .NET 版本中， <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列舉欄位未標示為過時。</span><span class="sxs-lookup"><span data-stu-id="05f46-104">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="05f46-105">在 .NET 5.0 和更新版本中，它會標示為「已淘汰」為警告。</span><span class="sxs-lookup"><span data-stu-id="05f46-105">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="05f46-106">這個欄位可能會在未來的 .NET 版本中移除。</span><span class="sxs-lookup"><span data-stu-id="05f46-106">This field may be removed in a future .NET version.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="05f46-107">變更的原因</span><span class="sxs-lookup"><span data-stu-id="05f46-107">Reason for change</span></span>

<span data-ttu-id="05f46-108">在某些情況下，將字串傳遞至會 <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 改變字串。</span><span class="sxs-lookup"><span data-stu-id="05f46-108">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="05f46-109">此行為會中斷字串的永久性保證，且可能會導致嚴重的 .NET 執行時間狀態損毀。</span><span class="sxs-lookup"><span data-stu-id="05f46-109">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="05f46-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="05f46-110">Version introduced</span></span>

<span data-ttu-id="05f46-111">.NET 5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="05f46-111">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="05f46-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="05f46-112">Recommended action</span></span>

<span data-ttu-id="05f46-113">更新依賴的任何程式碼 <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="05f46-113">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="05f46-114">類別</span><span class="sxs-lookup"><span data-stu-id="05f46-114">Category</span></span>

<span data-ttu-id="05f46-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05f46-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="05f46-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="05f46-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
