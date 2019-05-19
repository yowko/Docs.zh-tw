---
title: 作法：使用設計工具設定 Windows Forms 控制項所顯示的影像
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
- setting images [Windows Forms], Windows Forms controls
ms.assetid: ae80d07a-e469-4251-90ca-df71f5852454
ms.openlocfilehash: b914509656d3ce67d62dcd23cebdcc3b74278d72
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881999"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="a2c08-102">作法：使用設計工具設定 Windows Forms 控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="a2c08-102">How to: Set the Image Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="a2c08-103">數個 Windows Form 控制項來顯示影像。</span><span class="sxs-lookup"><span data-stu-id="a2c08-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="a2c08-104">映像可以釐清的控制項，例如磁碟圖示 按鈕，表示目的圖示**儲存**命令。</span><span class="sxs-lookup"><span data-stu-id="a2c08-104">The image can be an icon that clarifies the purpose of the control, such as a disk icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="a2c08-105">或者，圖示可以是您想要的外觀，讓控制項的背景影像。</span><span class="sxs-lookup"><span data-stu-id="a2c08-105">Alternatively, the icon can be a background image to give the control the appearance you want.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c08-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="a2c08-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a2c08-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="a2c08-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a2c08-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="a2c08-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="a2c08-109">若要設定控制項所顯示的影像</span><span class="sxs-lookup"><span data-stu-id="a2c08-109">To set the image displayed by a control</span></span>  
  
1. <span data-ttu-id="a2c08-110">在 **屬性**視窗中，選取**映像**或是**BackgroundImage**屬性的控制項，然後按一下省略符號按鈕 （</span><span class="sxs-lookup"><span data-stu-id="a2c08-110">In the **Properties** window, select the **Image** or **BackgroundImage** property of the control, then click the ellipsis button (</span></span>  
  
     ![省略符號按鈕 （...） 的 Visual Studio 的 [屬性] 視窗中。](./media/visual-studio-ellipsis-button.png)<span data-ttu-id="a2c08-112">)</span><span class="sxs-lookup"><span data-stu-id="a2c08-112">)</span></span>  
  
     <span data-ttu-id="a2c08-113">) 來顯示**選取資源** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a2c08-113">) to display the **Select Resource** dialog box.</span></span>  
  
2. <span data-ttu-id="a2c08-114">選取您想要顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="a2c08-114">Select the image you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c08-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2c08-115">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="a2c08-116">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="a2c08-116">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
