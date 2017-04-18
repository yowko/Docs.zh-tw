---
title: "如何：於執行階段修改圖片的大小或位置 (Windows Form) | Microsoft Docs"
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
  - "範例 [Windows Form], PictureBox 控制項"
  - "影像 [Windows Form], 在 PictureBox 控制項中控制放置位置 [Windows Form]"
  - "PictureBox 控制項 [Windows Form], 圖片的大小和對齊方式"
  - "圖片, 在 PictureBox 控制項中控制放置位置 [Windows Form]"
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：於執行階段修改圖片的大小或位置 (Windows Form)
如果您在表單上使用 Windows Form <xref:System.Windows.Forms.PictureBox> 控制項，可以將控制項的 <xref:System.Windows.Forms.PictureBox.SizeMode%2A> 屬性設定為：  
  
-   將圖片的左上角對齊控制項的左上角  
  
-   置中控制項內的圖片  
  
-   調整控制項的大小以容納它顯示的圖片  
  
-   自動縮放所顯示的任何圖片以符合控制項  
  
 自動縮放圖片 \(特別是點陣圖格式的圖片\) 可能會降低影像品質。  中繼檔是圖形指令清單，可在執行階段繪製影像，它與自動縮放的配合度比點陣圖還好。  
  
### 若要在執行階段設定 SizeMode 屬性  
  
1.  將 <xref:System.Windows.Forms.PictureBox.SizeMode%2A> 設為 <xref:System.Windows.Forms.PictureBoxSizeMode> \(預設值\)、<xref:System.Windows.Forms.PictureBoxSizeMode>、<xref:System.Windows.Forms.PictureBoxSizeMode> 或 <xref:System.Windows.Forms.PictureBoxSizeMode>。  <xref:System.Windows.Forms.PictureBoxSizeMode> 表示影像是放置在控制項的左上角；如果影像大於控制項，便會裁剪影像的右下邊緣。  <xref:System.Windows.Forms.PictureBoxSizeMode> 表示將影像置中於控制項；若影像大於控制項，就會裁剪圖片的外側邊緣。  <xref:System.Windows.Forms.PictureBoxSizeMode> 表示控制項的大小會調整成影像的大小。  <xref:System.Windows.Forms.PictureBoxSizeMode> 則是相反，表示影像大小會調整成控制項的大小。  
  
     在下列範例中，為影像位置所設定的路徑為 \[我的文件\] 資料夾。  這是可以做到的，因為您可假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。  這也可讓使用者以最基本的系統存取層級，便可安全執行應用程式。  下列範例假設已將 <xref:System.Windows.Forms.PictureBox> 控制項加入表單。  
  
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
  
## 請參閱  
 <xref:System.Windows.Forms.PictureBox>   
 [如何：使用設計工具載入圖片](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)   
 [PictureBox 控制項概觀](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [如何：在執行階段設定圖案](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)   
 [PictureBox 控制項](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)