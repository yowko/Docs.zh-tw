---
title: "如何：設定由 Windows Form 控制項所顯示的影像 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Button 控制項 [Windows Form], 影像"
  - "控制項 [Windows Form], 影像"
  - "範例 [Windows Form], 控制項"
  - "影像 [Windows Form], Windows Form 控制項"
  - "Windows Form 控制項, 影像"
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：設定由 Windows Form 控制項所顯示的影像
有幾個 Windows Form 控制項可顯示影像。  這些影像可以是表明控制項用途的圖示，例如按鈕上的磁碟片圖示代表**儲存**命令。  或者，圖示可以是背景影像，用來提供想要的控制項外觀和行為。  
  
### 若要設定控制項顯示的影像  
  
1.  將控制項的 `Image` 或 `BackgroundImage` 屬性設為 <xref:System.Drawing.Image> 型別的物件。  一般而言，使用 <xref:System.Drawing.Image.FromFile%2A> 方法，會讓您從檔案載入影像。  
  
     在下列程式碼範例中，圖示的位置路徑設定為 \[**我的圖片**\] 資料夾。  大部分執行 Windows 作業系統的電腦都有這個目錄。  這也可讓使用者只需最基本的系統存取層級，即可安全地執行應用程式。  下列程式碼範例假設已將 <xref:System.Windows.Forms.PictureBox> 控制項加入表單。  
  
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
  
## 請參閱  
 <xref:System.Drawing.Image.FromFile%2A>   
 <xref:System.Drawing.Image>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>