---
title: HOW TO：使用設計工具建立 Windows Forms 控制項的便捷鍵
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
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039513"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="de78a-102">HOW TO：使用設計工具建立 Windows Forms 控制項的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="de78a-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="de78a-103">*存取金鑰*是功能表、功能表項目或控制項標籤的文字中加底線的字元, 例如按鈕。</span><span class="sxs-lookup"><span data-stu-id="de78a-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="de78a-104">它可讓使用者按下 ALT 鍵並結合預先定義的存取金鑰, 以「按一下」按鈕。</span><span class="sxs-lookup"><span data-stu-id="de78a-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="de78a-105">例如, 如果按鈕執行程式來列印表單, 因此其`Text`屬性設定為 "print", 則在字母 "p" 之前加上連字號 (&) 會在執行時間的按鈕文字中加上底線。</span><span class="sxs-lookup"><span data-stu-id="de78a-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="de78a-106">使用者可以按 ALT + P, 執行與按鈕相關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="de78a-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="de78a-107">您不能擁有無法接收焦點之控制項的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="de78a-107">You cannot have an access key for a control that cannot receive focus.</span></span>

## <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="de78a-108">建立控制項的存取金鑰</span><span class="sxs-lookup"><span data-stu-id="de78a-108">To create an access key for a control</span></span>

1. <span data-ttu-id="de78a-109">在 [**屬性**] 視窗中, `Text`將屬性設定為字串, 在將成為存取金鑰的字母之前包含連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="de78a-109">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="de78a-110">例如, 若要將字母 "P" 設定為存取金鑰, 請在方格中輸入 **& 列印**。</span><span class="sxs-lookup"><span data-stu-id="de78a-110">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>

## <a name="see-also"></a><span data-ttu-id="de78a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de78a-111">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="de78a-112">如何：回應 Windows Forms 按鈕點擊</span><span class="sxs-lookup"><span data-stu-id="de78a-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="de78a-113">如何：設定 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="de78a-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="de78a-114">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="de78a-114">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
