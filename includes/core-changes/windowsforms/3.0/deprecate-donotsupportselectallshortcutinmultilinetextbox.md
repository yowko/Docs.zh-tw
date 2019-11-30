---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643988"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="0fc05-101">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數</span><span class="sxs-lookup"><span data-stu-id="0fc05-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="0fc05-102">在 .NET Framework 4.6.1 中引進的 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 相容性參數，在 .NET Core 3.0 的 Windows Forms 中不受支援。</span><span class="sxs-lookup"><span data-stu-id="0fc05-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0fc05-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0fc05-103">Change description</span></span>

<span data-ttu-id="0fc05-104">從 .NET Framework 4.6.1 開始，選取<kbd>Ctrl</kbd> + <xref:System.Windows.Forms.TextBox> 控制項中<kbd>的</kbd>快速鍵選取所有文字。</span><span class="sxs-lookup"><span data-stu-id="0fc05-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="0fc05-105">在 .NET Framework 4.6 和舊版中，如果[ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)和 <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> 屬性都設定為 `true`，則選取<kbd>Ctrl</kbd> <kbd> + 快速鍵</kbd>無法選取所有文字。</span><span class="sxs-lookup"><span data-stu-id="0fc05-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="0fc05-106">.NET Framework 4.6.1 中引進了 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 相容性參數，以保留原始的行為。</span><span class="sxs-lookup"><span data-stu-id="0fc05-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="0fc05-107">如需詳細資訊，請參閱＜<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>＞。</span><span class="sxs-lookup"><span data-stu-id="0fc05-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0fc05-108">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 參數。</span><span class="sxs-lookup"><span data-stu-id="0fc05-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0fc05-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0fc05-109">Version introduced</span></span>

<span data-ttu-id="0fc05-110">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="0fc05-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0fc05-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0fc05-111">Recommended action</span></span>

<span data-ttu-id="0fc05-112">移除參數。</span><span class="sxs-lookup"><span data-stu-id="0fc05-112">Remove the switch.</span></span> <span data-ttu-id="0fc05-113">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="0fc05-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="0fc05-114">Category</span><span class="sxs-lookup"><span data-stu-id="0fc05-114">Category</span></span>

<span data-ttu-id="0fc05-115">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="0fc05-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0fc05-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0fc05-116">Affected APIs</span></span>

- <span data-ttu-id="0fc05-117">None</span><span class="sxs-lookup"><span data-stu-id="0fc05-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
