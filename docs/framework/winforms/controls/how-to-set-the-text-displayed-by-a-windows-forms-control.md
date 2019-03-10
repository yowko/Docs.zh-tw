---
title: HOW TO：設定所顯示之文字的 Windows Form 控制項
ms.date: 03/30/2017
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
ms.openlocfilehash: 8ebb39e4e9337ede0dc8c7f5569ea27d8cfafd26
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716903"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="b7492-102">HOW TO：設定所顯示之文字的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="b7492-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="b7492-103">Windows Form 控制項通常會顯示與控制項主要功能相關的一些文字。</span><span class="sxs-lookup"><span data-stu-id="b7492-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="b7492-104">例如，<xref:System.Windows.Forms.Button> 控制項通常會顯示一個標題，指出當按下按鈕時，就會執行什麼動作。</span><span class="sxs-lookup"><span data-stu-id="b7492-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="b7492-105">針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="b7492-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="b7492-106">您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。</span><span class="sxs-lookup"><span data-stu-id="b7492-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="b7492-107">您也可以使用設計工具來設定文字。</span><span class="sxs-lookup"><span data-stu-id="b7492-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="b7492-108">另請參閱[How to:建立 Windows form 控制項使用設計工具的便捷鍵](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md)， [How to:設定所顯示之文字的 Windows Form 控制項使用設計工具](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md)， [How to:設定所顯示的映像的 Windows Form 控制項使用設計工具](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="b7492-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="b7492-109">以程式設計方式來設定控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="b7492-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="b7492-110">將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為字串。</span><span class="sxs-lookup"><span data-stu-id="b7492-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="b7492-111">若要建立加上底線的便捷鍵，請在要成為便捷鍵的字母前面加上連字號 (&) 字元。</span><span class="sxs-lookup"><span data-stu-id="b7492-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="b7492-112">將 <xref:System.Windows.Forms.Control.Font%2A> 屬性設為 <xref:System.Drawing.Font> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="b7492-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b7492-113">您可以在使用者介面項目中使用逸出字元來顯示特殊字元，這些使用者介面項目 (例如功能表項目) 通常會以不同方式來解譯該字元。</span><span class="sxs-lookup"><span data-stu-id="b7492-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="b7492-114">例如，下列程式碼字行會設定功能表項目的文字來讀取 "& Now For Something Completely Different"：</span><span class="sxs-lookup"><span data-stu-id="b7492-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b7492-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7492-115">See also</span></span>
- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b7492-116">如何：建立 Windows Form 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="b7492-116">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="b7492-117">如何：回應 Windows Form Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="b7492-117">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
