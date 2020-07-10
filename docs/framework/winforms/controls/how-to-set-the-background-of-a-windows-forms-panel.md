---
title: 設定面板背景
description: 瞭解如何使用設計工具來設定 Windows Forms 面板的背景色彩和背景影像。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173376"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="c59fc-103">如何：設定 Windows Form 面板的背景</span><span class="sxs-lookup"><span data-stu-id="c59fc-103">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="c59fc-104">Windows Forms <xref:System.Windows.Forms.Panel> 控制項可以同時顯示背景色彩和背景影像。</span><span class="sxs-lookup"><span data-stu-id="c59fc-104">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="c59fc-105"><xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含控制項的背景色彩，例如標籤和選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="c59fc-105">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="c59fc-106">如果 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 未設定屬性，則 <xref:System.Windows.Forms.Control.BackColor%2A> 選取專案將會填滿整個面板。</span><span class="sxs-lookup"><span data-stu-id="c59fc-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="c59fc-107">如果 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 已設定屬性，則影像會顯示在包含的控制項後方。</span><span class="sxs-lookup"><span data-stu-id="c59fc-107">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="c59fc-108">以程式設計方式設定背景</span><span class="sxs-lookup"><span data-stu-id="c59fc-108">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="c59fc-109">將面板的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性設定為類型的值 <xref:System.Drawing.Color?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c59fc-109">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="c59fc-110">使用類別的方法，設定面板的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性 <xref:System.Drawing.Image.FromFile%2A> <xref:System.Drawing.Image?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c59fc-110">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
    ```vb  
    ' You should replace the bolded image
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c59fc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c59fc-111">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="c59fc-112">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="c59fc-112">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="c59fc-113">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="c59fc-113">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
