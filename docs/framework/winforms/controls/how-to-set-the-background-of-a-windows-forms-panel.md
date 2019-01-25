---
title: HOW TO：設定 Windows Form 面板的背景
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
ms.openlocfilehash: 1c4eadaadf561e127ac2eaa87f62aea4e1dc7ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636075"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>HOW TO：設定 Windows Form 面板的背景
Windows Form<xref:System.Windows.Forms.Panel>控制項可以顯示的背景色彩和背景影像。 <xref:System.Windows.Forms.Control.BackColor%2A>屬性會設定包含的控制項，例如標籤和選項按鈕的背景色彩。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>未設定屬性，<xref:System.Windows.Forms.Control.BackColor%2A>選取項目將會填滿整個面板。 如果<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性設定時，影像會顯示包含的控制項後面。  
  
### <a name="to-set-the-background-programmatically"></a>以程式設計方式設定背景  
  
1.  設定面板<xref:System.Windows.Forms.Control.BackColor%2A>屬性設為值型別的<xref:System.Drawing.Color?displayProperty=nameWithType>。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  設定面板<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性使用<xref:System.Drawing.Image.FromFile%2A>方法<xref:System.Drawing.Image?displayProperty=nameWithType>類別。  
  
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
- [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
