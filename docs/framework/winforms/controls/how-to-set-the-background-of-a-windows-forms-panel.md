---
title: 設定面板背景
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
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182101"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="64908-102">如何：設定 Windows Form 面板的背景</span><span class="sxs-lookup"><span data-stu-id="64908-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="64908-103">Windows 表單<xref:System.Windows.Forms.Panel>控制項可以同時顯示背景顏色和背景圖像。</span><span class="sxs-lookup"><span data-stu-id="64908-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="64908-104">屬性<xref:System.Windows.Forms.Control.BackColor%2A>設置包含控制項（如標籤和選項按鈕）的背景顏色。</span><span class="sxs-lookup"><span data-stu-id="64908-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="64908-105">如果未設置<xref:System.Windows.Forms.Control.BackgroundImage%2A>該屬性，<xref:System.Windows.Forms.Control.BackColor%2A>則所選內容將填充整個面板。</span><span class="sxs-lookup"><span data-stu-id="64908-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="64908-106">如果設置了<xref:System.Windows.Forms.Control.BackgroundImage%2A>該屬性，則圖像將顯示在包含的控制項後面。</span><span class="sxs-lookup"><span data-stu-id="64908-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="64908-107">以程式設計方式設置背景</span><span class="sxs-lookup"><span data-stu-id="64908-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="64908-108">將面板的屬性<xref:System.Windows.Forms.Control.BackColor%2A>設置為 類型<xref:System.Drawing.Color?displayProperty=nameWithType>的值 。</span><span class="sxs-lookup"><span data-stu-id="64908-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="64908-109">使用<xref:System.Windows.Forms.Control.BackgroundImage%2A><xref:System.Drawing.Image?displayProperty=nameWithType>類<xref:System.Drawing.Image.FromFile%2A>的方法設置面板的屬性。</span><span class="sxs-lookup"><span data-stu-id="64908-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64908-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64908-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="64908-111">Panel 控制項</span><span class="sxs-lookup"><span data-stu-id="64908-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="64908-112">Panel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="64908-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
