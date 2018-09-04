---
title: 如何：使用設計工具建立 Windows Form 控制項的便捷鍵
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: d077de1636888f0e3b763344206692fee2cb2296
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502967"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="b9a4f-102">如何：使用設計工具建立 Windows Form 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="b9a4f-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="b9a4f-103">*便捷鍵*是功能表、 功能表項目，或按鈕等控制項的標籤文字中加上底線的字元。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="b9a4f-104">它可讓使用者 「 按一下 」 按鈕，然後按下 ALT 鍵組合中的預先定義的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="b9a4f-105">例如，如果按鈕會執行將表單，列印程序，因此其`Text`屬性設定為"Print"，將連字號 (&)"P"會導致字母"P"會加上底線的按鈕文字在執行階段的字母前面。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="b9a4f-106">使用者可以執行命令與按鈕關聯，藉由按下 ALT + P。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="b9a4f-107">您不能有無法接收焦點的控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9a4f-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b9a4f-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b9a4f-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="b9a4f-111">若要建立控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="b9a4f-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="b9a4f-112">在 **屬性**視窗中，將`Text`屬性設為字串，包含連字號 (&) 要存取的索引鍵的字母前面。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="b9a4f-113">例如，若要設定為便捷鍵的字母"P"，輸入**列印 &** 到方格內。</span><span class="sxs-lookup"><span data-stu-id="b9a4f-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a4f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9a4f-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="b9a4f-115">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="b9a4f-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="b9a4f-116">操作說明：設定由 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="b9a4f-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="b9a4f-117">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="b9a4f-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
