---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181719"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="5aa9d-101">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數</span><span class="sxs-lookup"><span data-stu-id="5aa9d-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="5aa9d-102">.Net `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.6.1 中引進的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5aa9d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="5aa9d-103">Change description</span></span>

<span data-ttu-id="5aa9d-104">從 .NET Framework 4.6.1 開始，選取<xref:System.Windows.Forms.TextBox>控制項<kbd>中的</kbd> <kbd>Ctrl</kbd>  + 鍵，並選取 [所有文字]。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="5aa9d-105">在 .NET Framework 4.6 和之前的版本中，如果[ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)和<xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType>屬性都設定為`true`，選取 [ <kbd>Ctrl</kbd>  +  <kbd>A</kbd> ] 快速鍵就無法選取所有文字。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="5aa9d-106">.NET Framework `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 4.6.1 中引進了相容性參數，以保留原始的行為。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="5aa9d-107">如需詳細資訊，請參閱<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5aa9d-108">在 .net Core 中， `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`不支援參數。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5aa9d-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5aa9d-109">Version introduced</span></span>

<span data-ttu-id="5aa9d-110">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="5aa9d-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5aa9d-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5aa9d-111">Recommended action</span></span>

<span data-ttu-id="5aa9d-112">移除參數。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-112">Remove the switch.</span></span> <span data-ttu-id="5aa9d-113">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="5aa9d-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="5aa9d-114">分類</span><span class="sxs-lookup"><span data-stu-id="5aa9d-114">Category</span></span>

<span data-ttu-id="5aa9d-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5aa9d-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5aa9d-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5aa9d-116">Affected APIs</span></span>

- <span data-ttu-id="5aa9d-117">None</span><span class="sxs-lookup"><span data-stu-id="5aa9d-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
