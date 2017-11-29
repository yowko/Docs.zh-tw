---
title: "如何：設定由 Windows Form 控制項所顯示的影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d9f4d806b39e6e1272ddbb60befdaf8c76e46b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>如何：設定由 Windows Form 控制項所顯示的影像
數個 Windows Form 控制項可以顯示影像。 這些映像可以是用途的控制項，例如按鈕，表示磁碟片圖示的圖示**儲存**命令。 或者，圖示可以提供控制項的外觀和行為，您想要的背景影像。  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>若要設定控制項所顯示的影像  
  
1.  將控制項的`Image`或`BackgroundImage`屬性型別的物件<xref:System.Drawing.Image>。 一般而言，您將會映像從檔案載入使用<xref:System.Drawing.Image.FromFile%2A>方法。  
  
     在下列程式碼範例中，設定路徑的映像的位置是**我的圖片**資料夾。 執行 Windows 作業系統的大部分電腦都會包含此目錄。 這也讓使用者以最少的系統存取層級可安全地執行應用程式。 下列程式碼範例需要您已經有的表單具有<xref:System.Windows.Forms.PictureBox>加入控制項。  
  
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
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
