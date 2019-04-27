---
title: HOW TO：設定 Windows Forms 控制項所顯示的影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 1de835bda5ac906837ac3fbd97b87f68f14d1953
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013136"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>HOW TO：設定 Windows Forms 控制項所顯示的影像
數個 Windows Form 控制項來顯示影像。 這些映像可以是用途的控制項，例如按鈕，表示磁碟片圖示的圖示**儲存**命令。 或者，圖示可以提供給控制項的外觀和行為，您想要的背景影像。  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>若要設定控制項所顯示的影像  
  
1. 將控制項的`Image`或是`BackgroundImage`型別的物件的屬性<xref:System.Drawing.Image>。 一般而言，您將會載入映像從檔案使用<xref:System.Drawing.Image.FromFile%2A>方法。  
  
     在下列程式碼範例中，將路徑設為映像的位置**My Pictures**資料夾。 執行 Windows 作業系統的大部分電腦都會包含此目錄。 這也可讓具有最少的系統存取層級的使用者安全地執行應用程式。 下列程式碼範例需要您已有表單<xref:System.Windows.Forms.PictureBox>加入控制項。  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
