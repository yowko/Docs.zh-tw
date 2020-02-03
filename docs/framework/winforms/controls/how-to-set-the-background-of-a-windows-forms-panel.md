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
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744738"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>如何：設定 Windows Form 面板的背景
Windows Forms <xref:System.Windows.Forms.Panel> 控制項可以同時顯示背景色彩和背景影像。 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性會設定包含控制項的背景色彩，例如標籤和選項按鈕。 如果未設定 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性，<xref:System.Windows.Forms.Control.BackColor%2A> 選取專案就會填滿整個面板。 如果已設定 [<xref:System.Windows.Forms.Control.BackgroundImage%2A>] 屬性，則影像會顯示在包含的控制項後方。  
  
### <a name="to-set-the-background-programmatically"></a>以程式設計方式設定背景  
  
1. 將面板的 [<xref:System.Windows.Forms.Control.BackColor%2A>] 屬性設定為 [<xref:System.Drawing.Color?displayProperty=nameWithType>類型] 的值。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. 使用 <xref:System.Drawing.Image?displayProperty=nameWithType> 類別的 <xref:System.Drawing.Image.FromFile%2A> 方法，設定面板的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel 控制項](panel-control-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
