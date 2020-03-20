---
title: 如何：於執行階段修改圖片的大小或位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141962"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>如何：於執行階段修改圖片的大小或位置 (Windows Form)
如果在表單上使用 Windows<xref:System.Windows.Forms.PictureBox>表單控制項，則可以將表單上<xref:System.Windows.Forms.PictureBox.SizeMode%2A>的屬性設置為：  
  
- 將圖片的左上角與控制項的左上角對齊  
  
- 將圖片居中  
  
- 調整控制項的大小以適合顯示的圖片  
  
- 拉伸它顯示的任何圖片以適合控制項  
  
 拉伸圖片（尤其是點陣圖格式）可能會損失圖像品質。 中繼檔是運行時繪製圖像的圖形說明清單，比點陣圖更適合拉伸。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>在運行時設置 SizeMode 屬性  
  
1. 設置為<xref:System.Windows.Forms.PictureBox.SizeMode%2A><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>（預設值）、<xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>或<xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>表示圖像放置在控制項的左上角;如果圖像大於控制項，則其下邊緣和右邊緣將剪切。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>表示圖像居中，在控制項中居中;如果圖像大於控制項，則剪切圖片的外邊緣。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>表示控制項的大小會調整為圖像的大小。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>是相反的，表示圖像的大小會調整到控制項的大小。  
  
     在下面的示例中，為圖像位置設置的路徑是"我的文件"資料夾。 此操作已完成，因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下面的示例假定已添加控制項的<xref:System.Windows.Forms.PictureBox>表單。  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PictureBox>
- [如何：使用設計工具載入圖片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [操作說明：在執行階段設定圖案](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)
