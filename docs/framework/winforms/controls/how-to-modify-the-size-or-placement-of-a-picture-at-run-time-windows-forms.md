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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736032"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>如何：於執行階段修改圖片的大小或位置 (Windows Form)
如果您在表單上使用 [Windows Forms <xref:System.Windows.Forms.PictureBox>] 控制項，您可以將其上的 <xref:System.Windows.Forms.PictureBox.SizeMode%2A> 屬性設定為：  
  
- 將圖片的左上角對齊控制項的左上角  
  
- 在控制項中將圖片置中  
  
- 調整控制項的大小以符合它所顯示的圖片  
  
- 延展顯示的任何圖片以符合控制項  
  
 延展圖片（尤其是點陣圖格式的圖片）可能會導致影像品質遺失。 中繼檔，這是在執行時間繪製影像的圖形指示清單，較適合用來延展，而不是點陣圖。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>若要在執行時間設定 SizeMode 屬性  
  
1. 將 <xref:System.Windows.Forms.PictureBox.SizeMode%2A> 設定為 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> （預設值）、<xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>、<xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>或 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> 表示影像放在控制項的左上角;如果影像大於控制項，則會裁剪其較低和右邊緣。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> 表示影像置中在控制項內;如果影像大於控制項，則會裁剪圖片的外部邊緣。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> 表示控制項的大小會調整為影像的大小。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 是相反的，這表示影像大小會調整為控制項的大小。  
  
     在下列範例中，為影像的位置設定的路徑是 [我的文件] 資料夾。 這是因為您可以假設大部分執行 Windows 作業系統的電腦都包含此目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下列範例假設已加入 <xref:System.Windows.Forms.PictureBox> 控制項的表單。  
  
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
- [操作說明：使用設計工具載入圖片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [操作說明：在執行階段設定圖案](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)
