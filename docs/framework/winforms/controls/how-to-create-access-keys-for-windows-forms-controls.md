---
title: 如何：建立 Windows Form 控制項的便捷鍵
ms.date: 03/30/2017
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
ms.openlocfilehash: 53ffd3632ff3e1179a72f1e2bfe4ea366e28b0f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530945"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="de92f-102">如何：建立 Windows Form 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="de92f-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="de92f-103">*便捷鍵*是功能表或功能表項目，例如按鈕控制項的標籤文字中加底線的字元。</span><span class="sxs-lookup"><span data-stu-id="de92f-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="de92f-104">便捷鍵，使用者可以 「 按一下 」 按鈕，然後按下 ALT 鍵組合中的預先定義的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="de92f-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="de92f-105">例如，按鈕會執行程序來列印表單時，如果，因此其`Text`屬性設定為"Print"，將新增連字號，再字母"P"讓字母"P"會在執行階段上底線的按鈕文字。</span><span class="sxs-lookup"><span data-stu-id="de92f-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="de92f-106">使用者可以執行命令與按鈕按下 ALT + P 關聯。</span><span class="sxs-lookup"><span data-stu-id="de92f-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="de92f-107">您不能有無法接收焦點的控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="de92f-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="de92f-108">若要建立控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="de92f-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="de92f-109">設定`Text`屬性為字串，包含連字號 (&) 會快顯的字母前面。</span><span class="sxs-lookup"><span data-stu-id="de92f-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
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
    >  <span data-ttu-id="de92f-110">若要包含標題中的連字號，而不需要建立便捷鍵，包含兩個連字號 (（& s) （& s))。</span><span class="sxs-lookup"><span data-stu-id="de92f-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="de92f-111">單一連字號會顯示在標題中，而且沒有字元加上底線。</span><span class="sxs-lookup"><span data-stu-id="de92f-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de92f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de92f-112">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="de92f-113">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="de92f-113">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="de92f-114">操作說明：設定由 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="de92f-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="de92f-115">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="de92f-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
