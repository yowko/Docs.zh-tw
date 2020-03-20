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
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182122"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>如何：在執行階段設定圖片 (Windows Form)
您可以以程式設計方式設置 Windows 表單<xref:System.Windows.Forms.PictureBox>控制項顯示的圖像。  
  
### <a name="to-set-a-picture-programmatically"></a>以程式設計方式設置圖片  
  
- 使用<xref:System.Windows.Forms.PictureBox.Image%2A><xref:System.Drawing.Image.FromFile%2A><xref:System.Drawing.Image>類的方法設置屬性。  
  
     在下面的示例中，為圖像位置設置的路徑是"我的文件"資料夾。 此操作已完成，因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此目錄。 也可讓具備最小系統存取層級的使用者安全地執行應用程式。 下面的示例假定已添加控制項的<xref:System.Windows.Forms.PictureBox>表單。  
  
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
  
### <a name="to-clear-a-graphic"></a>清除圖形  
  
- 首先，釋放圖像正在使用的記憶體，然後清除圖形。 如果記憶體管理成為問題，垃圾回收稍後將釋放記憶體。  
  
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
    > 有關為什麼要以這種方式使用<xref:System.Drawing.Image.Dispose%2A>方法的詳細資訊，請參閱[清理非託管資源](../../../standard/garbage-collection/unmanaged.md)。  
  
     即使圖形在設計時載入到控制項中，此代碼也會清除圖像。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox 控制項概觀](picturebox-control-overview-windows-forms.md)
- [如何：使用設計工具載入圖片](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [操作說明：於執行階段修改圖片的大小或位置](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox 控制項](picturebox-control-windows-forms.md)
