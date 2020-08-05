---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556148"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="2a92f-101">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換</span><span class="sxs-lookup"><span data-stu-id="2a92f-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="2a92f-102">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.Net Core 和 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.6.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="2a92f-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2a92f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="2a92f-103">Change description</span></span>

<span data-ttu-id="2a92f-104">從 .NET Framework 4.6.1 開始，選取控制項中的<kbd>Ctrl</kbd>  +  <kbd>A</kbd>鍵，並 <xref:System.Windows.Forms.TextBox> 選取 [所有文字]。</span><span class="sxs-lookup"><span data-stu-id="2a92f-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="2a92f-105">在 .NET Framework 4.6 和之前的版本中， <kbd>Ctrl</kbd>  +  <kbd>A</kbd>如果[ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)和 <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> 屬性都設定為，選取 [Ctrl A] 快速鍵就無法選取所有文字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="2a92f-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="2a92f-106">`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET Framework 4.6.1 中引進了相容性參數，以保留原始的行為。</span><span class="sxs-lookup"><span data-stu-id="2a92f-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="2a92f-107">如需相關資訊，請參閱<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2a92f-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2a92f-108">在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 不支援參數。</span><span class="sxs-lookup"><span data-stu-id="2a92f-108">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a92f-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="2a92f-109">Version introduced</span></span>

<span data-ttu-id="2a92f-110">3.0</span><span class="sxs-lookup"><span data-stu-id="2a92f-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a92f-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2a92f-111">Recommended action</span></span>

<span data-ttu-id="2a92f-112">移除參數。</span><span class="sxs-lookup"><span data-stu-id="2a92f-112">Remove the switch.</span></span> <span data-ttu-id="2a92f-113">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="2a92f-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2a92f-114">類別</span><span class="sxs-lookup"><span data-stu-id="2a92f-114">Category</span></span>

<span data-ttu-id="2a92f-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a92f-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a92f-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2a92f-116">Affected APIs</span></span>

- <span data-ttu-id="2a92f-117">無</span><span class="sxs-lookup"><span data-stu-id="2a92f-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
