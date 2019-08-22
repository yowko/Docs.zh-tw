---
title: HOW TO：設定 Windows Forms 控制項所顯示的文字
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 887aa5ec9b97770903cd87459d6df5adc3f7ddf0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666146"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="3d084-102">作法：設定 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="3d084-102">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="3d084-103">Windows Forms 控制項通常會顯示一些與控制項主要功能相關的文字。</span><span class="sxs-lookup"><span data-stu-id="3d084-103">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="3d084-104">例如, <xref:System.Windows.Forms.Button>控制項通常會顯示一個標題, 指出按一下按鈕時將執行的動作。</span><span class="sxs-lookup"><span data-stu-id="3d084-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="3d084-105">針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="3d084-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="3d084-106">您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。</span><span class="sxs-lookup"><span data-stu-id="3d084-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="3d084-107">您也可以使用[設計](#designer)工具來設定文字。</span><span class="sxs-lookup"><span data-stu-id="3d084-107">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="3d084-108">化</span><span class="sxs-lookup"><span data-stu-id="3d084-108">Programmatic</span></span>

1. <span data-ttu-id="3d084-109">將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為字串。</span><span class="sxs-lookup"><span data-stu-id="3d084-109">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="3d084-110">若要建立加底線的存取金鑰, 請在將成為存取金鑰的字母之前包含連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="3d084-110">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="3d084-111">將 <xref:System.Windows.Forms.Control.Font%2A> 屬性設為 <xref:System.Drawing.Font> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="3d084-111">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > <span data-ttu-id="3d084-112">您可以在使用者介面項目中使用逸出字元來顯示特殊字元，這些使用者介面項目 (例如功能表項目) 通常會以不同方式來解譯該字元。</span><span class="sxs-lookup"><span data-stu-id="3d084-112">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="3d084-113">例如, 下面這行程式碼會將功能表項目的文字設定為「立即 & 完全不同」的內容:</span><span class="sxs-lookup"><span data-stu-id="3d084-113">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="3d084-114">Designer</span><span class="sxs-lookup"><span data-stu-id="3d084-114">Designer</span></span>

1. <span data-ttu-id="3d084-115">在 Visual Studio 的 [**屬性**] 視窗中, 將控制項的 [ **Text** ] 屬性設定為適當的字串。</span><span class="sxs-lookup"><span data-stu-id="3d084-115">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="3d084-116">若要建立加底線的快速鍵, 請在將做為快速鍵的字母之前包含連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="3d084-116">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="3d084-117">在 **屬性**] 視窗中, 選取 [![**字型**] 屬性旁邊的省略號按鈕 ([Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...))。</span><span class="sxs-lookup"><span data-stu-id="3d084-117">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="3d084-118">在 [標準字型] 對話方塊中, 選取字型、字型樣式、大小、效果 (例如刪除線或底線), 以及您想要的腳本。</span><span class="sxs-lookup"><span data-stu-id="3d084-118">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d084-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d084-119">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3d084-120">如何：建立 Windows Forms 控制項的存取金鑰</span><span class="sxs-lookup"><span data-stu-id="3d084-120">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="3d084-121">如何：回應 Windows Forms 按鈕點擊</span><span class="sxs-lookup"><span data-stu-id="3d084-121">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
