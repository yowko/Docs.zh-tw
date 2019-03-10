---
title: HOW TO：在執行階段 (Windows Form) 設定的圖片
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 5afb4fe3ebef705cd0671312aacb6f9ad8219621
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711213"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>HOW TO：在執行階段 (Windows Form) 設定的圖片
您可以透過程式設計方式設定顯示 Windows Form 的影像<xref:System.Windows.Forms.PictureBox>控制項。  
  
### <a name="to-set-a-picture-programmatically"></a>以程式設計方式設定圖片  
  
-   設定<xref:System.Windows.Forms.PictureBox.Image%2A>屬性使用<xref:System.Drawing.Image.FromFile%2A>方法<xref:System.Drawing.Image>類別。  
  
     在下列範例中，映像的位置所設定的路徑會是 [我的文件] 資料夾。 這麼做，因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下列範例假設表單<xref:System.Windows.Forms.PictureBox>已經加入的控制項。  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>若要清除圖形  
  
-   首先，釋放記憶體正在使用映像，然後再清除 圖形。 記憶體回收會釋出記憶體稍後如果記憶體管理變得有問題。  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  如需有關為什麼您應該使用<xref:System.Drawing.Image.Dispose%2A>方法，如此一來，請參閱[清除 Unmanaged 資源總](../../../standard/garbage-collection/unmanaged.md)。  
  
     此程式碼將會清除映像，即使圖形在設計階段時載入控制項。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [如何：使用設計工具載入圖片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [如何：在執行階段修改的大小或位置的圖片](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)
