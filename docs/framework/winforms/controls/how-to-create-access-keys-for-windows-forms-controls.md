---
title: 作法：建立 Windows Forms 控制項的便捷鍵
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: ccec8bba9e01cbaa7bfef841af68a0fcaa720b90
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658384"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="f4cea-102">作法：建立 Windows Forms 控制項的存取金鑰</span><span class="sxs-lookup"><span data-stu-id="f4cea-102">How to: Create access keys for Windows Forms controls</span></span>

<span data-ttu-id="f4cea-103">*存取金鑰*是功能表、功能表項目或控制項標籤的文字中加底線的字元, 例如按鈕。</span><span class="sxs-lookup"><span data-stu-id="f4cea-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="f4cea-104">使用存取金鑰時, 使用者可以按下 ALT 鍵並結合預先定義的存取金鑰, 以「按一下」按鈕。</span><span class="sxs-lookup"><span data-stu-id="f4cea-104">With an access key, the user can "click" a button by pressing the Alt key in combination with the predefined access key.</span></span> <span data-ttu-id="f4cea-105">例如, 如果按鈕執行程式來列印表單, 因此其`Text`屬性設定為 "print", 則在字母 "p" 之前加入 & 會使字母 "p" 在執行時間于按鈕文字中加上底線。</span><span class="sxs-lookup"><span data-stu-id="f4cea-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="f4cea-106">使用者可以按 Alt + P, 執行與按鈕相關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="f4cea-106">The user can run the command associated with the button by pressing Alt+P.</span></span>

<span data-ttu-id="f4cea-107">無法接收焦點的控制項不能有存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="f4cea-107">Controls that cannot receive focus can't have access keys.</span></span>

## <a name="programmatic"></a><span data-ttu-id="f4cea-108">化</span><span class="sxs-lookup"><span data-stu-id="f4cea-108">Programmatic</span></span>

<span data-ttu-id="f4cea-109">`Text`將屬性設定為字串, 其中包含做為快捷方式的字母前面的連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="f4cea-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>

```vb
' Set the letter "P" as an access key.
Button1.Text = "&Print"
```

```csharp
// Set the letter "P" as an access key.
button1.Text = "&Print";
```

```cpp
// Set the letter "P" as an access key.
button1->Text = "&Print";
```

> [!NOTE]
> <span data-ttu-id="f4cea-110">若要在標題中使用連字號而不建立存取金鑰, 請包含兩個 & (& &)。</span><span class="sxs-lookup"><span data-stu-id="f4cea-110">To use an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="f4cea-111">標題中會顯示單一符號, 而且不會有任何字元加上底線。</span><span class="sxs-lookup"><span data-stu-id="f4cea-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>

## <a name="designer"></a><span data-ttu-id="f4cea-112">Designer</span><span class="sxs-lookup"><span data-stu-id="f4cea-112">Designer</span></span>

<span data-ttu-id="f4cea-113">在 Visual Studio 的 [**屬性**] 視窗中, 將 [ **Text** ] 屬性設定為包含連字號 (' & ') 的字串, 並在將成為存取金鑰的字母前面。</span><span class="sxs-lookup"><span data-stu-id="f4cea-113">In the **Properties** window of Visual Studio, set the **Text** property to a string that includes an ampersand ('&') before the letter that will be the access key.</span></span> <span data-ttu-id="f4cea-114">例如, 若要將字母 "P" 設定為存取金鑰, 請輸入 **& Print**。</span><span class="sxs-lookup"><span data-stu-id="f4cea-114">For example, to set the letter "P" as the access key, enter **&Print**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4cea-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4cea-115">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="f4cea-116">如何：回應 Windows Forms 按鈕點擊</span><span class="sxs-lookup"><span data-stu-id="f4cea-116">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="f4cea-117">如何：設定 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="f4cea-117">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="f4cea-118">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="f4cea-118">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
