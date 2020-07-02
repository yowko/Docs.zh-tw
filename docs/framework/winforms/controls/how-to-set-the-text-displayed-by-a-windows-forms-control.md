---
title: 設定控制項所顯示的文字
description: 瞭解如何設定 Windows Forms 控制項所顯示的文字。 使用 [Text] 屬性來設定或傳回文字，或使用 [字型] 屬性來變更字型。
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
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622844"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="667b6-104">如何：設定 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="667b6-104">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="667b6-105">Windows Forms 控制項通常會顯示一些與控制項主要功能相關的文字。</span><span class="sxs-lookup"><span data-stu-id="667b6-105">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="667b6-106">例如， <xref:System.Windows.Forms.Button> 控制項通常會顯示一個標題，指出按一下按鈕時將執行的動作。</span><span class="sxs-lookup"><span data-stu-id="667b6-106">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="667b6-107">針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="667b6-107">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="667b6-108">您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。</span><span class="sxs-lookup"><span data-stu-id="667b6-108">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="667b6-109">您也可以使用[設計](#designer)工具來設定文字。</span><span class="sxs-lookup"><span data-stu-id="667b6-109">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="667b6-110">程式設計</span><span class="sxs-lookup"><span data-stu-id="667b6-110">Programmatic</span></span>

1. <span data-ttu-id="667b6-111">將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為字串。</span><span class="sxs-lookup"><span data-stu-id="667b6-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="667b6-112">若要建立加底線的存取金鑰，請在將成為存取金鑰的字母之前包含連字號（&）。</span><span class="sxs-lookup"><span data-stu-id="667b6-112">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="667b6-113">將 <xref:System.Windows.Forms.Control.Font%2A> 屬性設為 <xref:System.Drawing.Font> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="667b6-113">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

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
    > <span data-ttu-id="667b6-114">您可以在使用者介面項目中使用逸出字元來顯示特殊字元，這些使用者介面項目 (例如功能表項目) 通常會以不同方式來解譯該字元。</span><span class="sxs-lookup"><span data-stu-id="667b6-114">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="667b6-115">例如，下面這行程式碼會將功能表項目的文字設定為「立即 & 完全不同」的內容：</span><span class="sxs-lookup"><span data-stu-id="667b6-115">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="667b6-116">設計師</span><span class="sxs-lookup"><span data-stu-id="667b6-116">Designer</span></span>

1. <span data-ttu-id="667b6-117">在 Visual Studio 的 [**屬性**] 視窗中，將控制項的 [ **Text** ] 屬性設定為適當的字串。</span><span class="sxs-lookup"><span data-stu-id="667b6-117">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="667b6-118">若要建立加底線的快速鍵，請在將做為快速鍵的字母之前包含連字號（&）。</span><span class="sxs-lookup"><span data-stu-id="667b6-118">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="667b6-119">在 [**屬性**] 視窗中，選取 ![ ](./media/visual-studio-ellipsis-button.png) [**字型**] 屬性旁邊的省略號按鈕（[Visual Studio 的屬性視窗中的省略號按鈕（...））。</span><span class="sxs-lookup"><span data-stu-id="667b6-119">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="667b6-120">在 [標準字型] 對話方塊中，選取字型、字型樣式、大小、效果（例如刪除線或底線），以及您想要的腳本。</span><span class="sxs-lookup"><span data-stu-id="667b6-120">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="667b6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="667b6-121">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="667b6-122">操作說明：建立 Windows Forms 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="667b6-122">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="667b6-123">如何：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="667b6-123">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
