---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937113"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="7f1b7-101">不支援選擇全選件多行文本盒相容性開關</span><span class="sxs-lookup"><span data-stu-id="7f1b7-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="7f1b7-102">.NET 框架 4.6.1 中引入的`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7f1b7-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="7f1b7-103">Change description</span></span>

<span data-ttu-id="7f1b7-104">從 .NET 框架 4.6.1 開始，<xref:System.Windows.Forms.TextBox>在控制項中選擇<kbd>Ctrl</kbd> + <kbd>A</kbd>快速鍵選擇了所有文本。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="7f1b7-105">在 .NET 框架 4.6 和早期版本中，如果[Textbox.快捷方式啟用](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled)<xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType>和屬性都`true`設置為 ，則選擇<kbd>Ctrl</kbd> + <kbd>快捷</kbd>鍵無法選擇所有文本。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="7f1b7-106">在`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`.NET 框架 4.6.1 中引入了相容性開關，以保留原始行為。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="7f1b7-107">如需相關資訊，請參閱<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="7f1b7-108">在 .NET 內核`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7f1b7-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="7f1b7-109">Version introduced</span></span>

<span data-ttu-id="7f1b7-110">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="7f1b7-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7f1b7-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7f1b7-111">Recommended action</span></span>

<span data-ttu-id="7f1b7-112">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-112">Remove the switch.</span></span> <span data-ttu-id="7f1b7-113">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="7f1b7-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="7f1b7-114">類別</span><span class="sxs-lookup"><span data-stu-id="7f1b7-114">Category</span></span>

<span data-ttu-id="7f1b7-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f1b7-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f1b7-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7f1b7-116">Affected APIs</span></span>

- <span data-ttu-id="7f1b7-117">None</span><span class="sxs-lookup"><span data-stu-id="7f1b7-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
