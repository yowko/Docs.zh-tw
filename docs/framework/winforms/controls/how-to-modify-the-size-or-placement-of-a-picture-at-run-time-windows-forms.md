---
title: 如何：於執行階段修改圖片的大小或位置 (Windows Form)
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
ms.openlocfilehash: 9e6e114e0a9d7e5e9c17ba21ef941703cd108784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>如何：於執行階段修改圖片的大小或位置 (Windows Form)
如果您使用 Windows Form<xref:System.Windows.Forms.PictureBox>控制項在表單中，您可以設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>它的屬性：  
  
-   對齊圖片的左上的角的控制項的左上角  
  
-   在控制項中將圖片置中  
  
-   調整大小以符合它所顯示的圖片控制項  
  
-   自動縮放以符合控制項顯示的任何圖片  
  
 自動縮放的圖片 （特別是點陣圖格式） 可能會產生遺失的影像品質。 中繼檔，也就是在執行階段繪製影像的圖形指令清單，是比較適合度比點陣圖。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>若要在執行階段設定 SizeMode 屬性  
  
1.  設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>至<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>（預設）、 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>， <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>，或<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> 表示影像置於控制項的左上角。如果影像大於此控制項，其下限和右邊緣會被裁剪。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> 表示影像內置中控制項。如果影像大於此控制項，則會裁剪圖片的外緣。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> 表示控制項的大小會調整影像的大小。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 反向，表示影像的大小會調整控制項大小。  
  
     下列範例中，在映像的位置所設定的路徑會是 [我的文件] 資料夾。 這麼做，因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 以下範例假設的表單具有<xref:System.Windows.Forms.PictureBox>已經加入的控制項。  
  
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
 <xref:System.Windows.Forms.PictureBox>  
 [操作說明：使用設計工具載入圖片](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [PictureBox 控制項概觀](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [操作說明：在執行階段設定圖案](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox 控制項](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
