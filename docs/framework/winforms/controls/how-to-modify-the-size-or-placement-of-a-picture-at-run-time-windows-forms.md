---
title: HOW TO：修改的大小或位置的圖片，在執行階段 (Windows Form)
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
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328331"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>HOW TO：修改的大小或位置的圖片，在執行階段 (Windows Form)
如果您使用 Windows Form<xref:System.Windows.Forms.PictureBox>控制項在表單中，您可以設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>上它的屬性：  
  
-   對齊圖片的左上的角的控制項的左上角  
  
-   在控制項中將圖片置中  
  
-   調整以符合它顯示的圖片控制項的大小  
  
-   自動縮放以符合控制項顯示的任何圖片  
  
 自動縮放的圖片 （尤其是一個以點陣圖格式），可以產生遺失的影像品質。 中繼檔，也就是在執行階段繪製影像的圖形指示清單、 計較適合用來自動縮放比點陣圖。  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>若要在執行階段設定的大小模式屬性  
  
1. 設定<xref:System.Windows.Forms.PictureBox.SizeMode%2A>要<xref:System.Windows.Forms.PictureBoxSizeMode.Normal>（預設值）， <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>， <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>，或<xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>。 <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> 表示影像置於控制項的左上角。如果影像大於此控制項，其低和右緣被裁剪。 <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> 表示影像置於控制項中，如果影像大於此控制項，則會裁剪圖片的外邊緣。 <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> 表示控制項的大小會調整為影像的大小。 <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> 相反地，，表示影像的大小調整控制項大小的。  
  
     在下列範例中，映像的位置所設定的路徑會是 [我的文件] 資料夾。 這麼做，因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下列範例假設表單<xref:System.Windows.Forms.PictureBox>已經加入的控制項。  
  
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
- [如何：在執行階段設定圖案](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)
