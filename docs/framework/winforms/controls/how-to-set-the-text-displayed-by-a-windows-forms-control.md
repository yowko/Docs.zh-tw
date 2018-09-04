---
title: 如何：設定由 Windows Form 控制項所顯示的文字
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
ms.openlocfilehash: d9c9bea26cfc3d5b2cfc4484173a7680ff2fc34d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525031"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="284f0-102">如何：設定由 Windows Form 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="284f0-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="284f0-103">Windows Form 控制項通常會顯示與控制項主要功能相關的一些文字。</span><span class="sxs-lookup"><span data-stu-id="284f0-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="284f0-104">例如，<xref:System.Windows.Forms.Button> 控制項通常會顯示一個標題，指出當按下按鈕時，就會執行什麼動作。</span><span class="sxs-lookup"><span data-stu-id="284f0-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="284f0-105">針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="284f0-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="284f0-106">您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。</span><span class="sxs-lookup"><span data-stu-id="284f0-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="284f0-107">您也可以使用設計工具來設定文字。</span><span class="sxs-lookup"><span data-stu-id="284f0-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="284f0-108">另請參閱[如何： 建立存取金鑰的 Windows Form 控制項使用設計工具](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md)，[如何： 設定 Windows Form 控制項使用的文字顯示設計工具](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md)， [How to： 設定映像顯示 Windows Form 控制項使用設計工具](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="284f0-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="284f0-109">以程式設計方式來設定控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="284f0-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="284f0-110">將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為字串。</span><span class="sxs-lookup"><span data-stu-id="284f0-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="284f0-111">若要建立加上底線的便捷鍵，請在要成為便捷鍵的字母前面加上連字號 (&) 字元。</span><span class="sxs-lookup"><span data-stu-id="284f0-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="284f0-112">將 <xref:System.Windows.Forms.Control.Font%2A> 屬性設為 <xref:System.Drawing.Font> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="284f0-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
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
    >  <span data-ttu-id="284f0-113">您可以在使用者介面項目中使用逸出字元來顯示特殊字元，這些使用者介面項目 (例如功能表項目) 通常會以不同方式來解譯該字元。</span><span class="sxs-lookup"><span data-stu-id="284f0-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="284f0-114">例如，下列程式碼字行會設定功能表項目的文字來讀取 "& Now For Something Completely Different"：</span><span class="sxs-lookup"><span data-stu-id="284f0-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="284f0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="284f0-115">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="284f0-116">操作說明：建立 Windows Forms 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="284f0-116">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [<span data-ttu-id="284f0-117">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="284f0-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
