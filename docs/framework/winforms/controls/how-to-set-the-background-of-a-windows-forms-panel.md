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
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>如何：設定 Windows Form 面板的背景
Windows 表單<xref:System.Windows.Forms.Panel>控制項可以同時顯示背景顏色和背景圖像。 屬性<xref:System.Windows.Forms.Control.BackColor%2A>設置包含控制項（如標籤和選項按鈕）的背景顏色。 如果未設置<xref:System.Windows.Forms.Control.BackgroundImage%2A>該屬性，<xref:System.Windows.Forms.Control.BackColor%2A>則所選內容將填充整個面板。 如果設置了<xref:System.Windows.Forms.Control.BackgroundImage%2A>該屬性，則圖像將顯示在包含的控制項後面。  
  
### <a name="to-set-the-background-programmatically"></a>以程式設計方式設置背景  
  
1. 將面板的屬性<xref:System.Windows.Forms.Control.BackColor%2A>設置為 類型<xref:System.Drawing.Color?displayProperty=nameWithType>的值 。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. 使用<xref:System.Windows.Forms.Control.BackgroundImage%2A><xref:System.Drawing.Image?displayProperty=nameWithType>類<xref:System.Drawing.Image.FromFile%2A>的方法設置面板的屬性。  
  
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
