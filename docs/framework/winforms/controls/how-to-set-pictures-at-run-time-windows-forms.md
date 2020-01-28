---
title: 如何：在執行階段設定圖案
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
ms.openlocfilehash: bd0509c05fd9c1cfc0c631fcd613c64d20296f6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746744"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>如何：在執行階段設定圖片 (Windows Form)
您可以透過程式設計方式設定 Windows Forms <xref:System.Windows.Forms.PictureBox> 控制項所顯示的影像。  
  
### <a name="to-set-a-picture-programmatically"></a>以程式設計方式設定圖片  
  
- 使用 <xref:System.Drawing.Image> 類別的 <xref:System.Drawing.Image.FromFile%2A> 方法，設定 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性。  
  
     在下列範例中，為影像的位置設定的路徑是 [我的文件] 資料夾。 這是因為您可以假設大部分執行 Windows 作業系統的電腦都包含此目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下列範例假設已加入 <xref:System.Windows.Forms.PictureBox> 控制項的表單。  
  
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
  
- 首先，釋放影像所使用的記憶體，然後清除圖形。 如果記憶體管理變成問題，垃圾收集將會在稍後釋放記憶體。  
  
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
    > 如需有關為何應該以這種方式使用 <xref:System.Drawing.Image.Dispose%2A> 方法的詳細資訊，請參閱[清除非受控資源](../../../standard/garbage-collection/unmanaged.md)。  
  
     即使在設計階段將圖形載入至控制項，此程式碼也會清除影像。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [操作說明：使用設計工具載入圖片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [操作說明：於執行階段修改圖片的大小或位置](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)
