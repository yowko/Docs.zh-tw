---
title: 變更表單框線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739561"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="2ee5b-102">如何：變更 Windows Form 的框線</span><span class="sxs-lookup"><span data-stu-id="2ee5b-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="2ee5b-103">在決定 Windows Form 的外觀和行為時，您有幾種框線樣式可以選擇。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="2ee5b-104">藉由變更 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性，您可以控制表單的調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="2ee5b-105">此外，設定 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 也會影響標題列的顯示方式，以及所出現在標題列上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="2ee5b-106">如需詳細資訊，請參閱 <xref:System.Windows.Forms.FormBorderStyle>。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="2ee5b-107">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="2ee5b-108">另請參閱[如何：使用設計工具變更 Windows Forms 的框線](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="2ee5b-109">以程式設計方式設定 Windows Form 的框線樣式</span><span class="sxs-lookup"><span data-stu-id="2ee5b-109">To set the border style of Windows Forms programmatically</span></span>  
  
- <span data-ttu-id="2ee5b-110">將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為您想要的樣式。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="2ee5b-111">下列程式碼範例會將表單 `DlgBx1` 的框線樣式設定為 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="2ee5b-112">另請參閱[如何：在設計階段建立對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-112">Also see [How to: Create Dialog Boxes at Design Time](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span></span>  
  
     <span data-ttu-id="2ee5b-113">此外，如果您已選擇提供選擇性**最小化**和**最大化**按鈕之表單的框線樣式，您可以指定是否要讓這兩個按鈕或兩者都正常運作。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="2ee5b-114">當您想要密切控制使用者經驗時，這些按鈕會很有用。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="2ee5b-115">預設會啟用 [**最小化**] 和 [**最大化**] 按鈕，而且其功能會透過 [**屬性**] 視窗來操作。</span><span class="sxs-lookup"><span data-stu-id="2ee5b-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee5b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ee5b-116">See also</span></span>

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [<span data-ttu-id="2ee5b-117">Windows Forms 使用者入門</span><span class="sxs-lookup"><span data-stu-id="2ee5b-117">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
