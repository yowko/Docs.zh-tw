---
title: "如何：建立 Windows Form 控制項的便捷鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81aa68a65d09b073b117f4d96dfc06e614d68aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="e56af-102">如何：建立 Windows Form 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="e56af-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="e56af-103">*便捷鍵*是功能表或功能表項目，例如按鈕控制項的標籤文字中加底線的字元。</span><span class="sxs-lookup"><span data-stu-id="e56af-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="e56af-104">便捷鍵，使用者可以 「 按一下 」 按鈕，然後按下 ALT 鍵組合中的預先定義的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="e56af-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="e56af-105">例如，按鈕會執行程序來列印表單時，如果，因此其`Text`屬性設定為"Print"，將新增連字號，再字母"P"讓字母"P"會在執行階段上底線的按鈕文字。</span><span class="sxs-lookup"><span data-stu-id="e56af-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="e56af-106">使用者可以執行命令與按鈕按下 ALT + P 關聯。</span><span class="sxs-lookup"><span data-stu-id="e56af-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="e56af-107">您不能有無法接收焦點的控制項的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="e56af-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="e56af-108">若要建立控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="e56af-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="e56af-109">設定`Text`屬性為字串，包含連字號 (&) 會快顯的字母前面。</span><span class="sxs-lookup"><span data-stu-id="e56af-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
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
    >  <span data-ttu-id="e56af-110">若要包含標題中的連字號，而不需要建立便捷鍵，包含兩個連字號 (（& s) （& s))。</span><span class="sxs-lookup"><span data-stu-id="e56af-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="e56af-111">單一連字號會顯示在標題中，而且沒有字元加上底線。</span><span class="sxs-lookup"><span data-stu-id="e56af-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e56af-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e56af-112">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="e56af-113">操作說明：回應 Windows Forms Button 按一下動作</span><span class="sxs-lookup"><span data-stu-id="e56af-113">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="e56af-114">操作說明：設定由 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="e56af-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="e56af-115">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="e56af-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
