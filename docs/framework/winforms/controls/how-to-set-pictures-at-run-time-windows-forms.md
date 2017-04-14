---
title: "如何：在執行階段設定圖片 (Windows Form) | Microsoft Docs"
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
  - "點陣圖 [Windows Form], 在 PictureBox 控制項中顯示 [Windows Form]"
  - "範例 [Windows Form], PictureBox 控制項"
  - "影像 [Windows Form], adding with PictureBox 控制項 [Windows Form]"
  - "PictureBox 控制項 [Windows Form], 加入影像"
  - "PictureBox 控制項 [Windows Form], 加入圖片"
  - "圖片, 設定顯示"
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：在執行階段設定圖片 (Windows Form)
您可以程式設計的方式，設定 Windows Form <xref:System.Windows.Forms.PictureBox> 控制項所顯示的影像。  
  
### 若要以程式設計的方式設定圖片  
  
-   使用 <xref:System.Drawing.Image> 類別的 <xref:System.Drawing.Image.FromFile%2A> 方法，設定 <xref:System.Windows.Forms.PictureBox.Image%2A> 屬性。  
  
     在下列範例中，為影像位置所設定的路徑為 \[我的文件\] 資料夾。  這是可以做到的，因為您可假設大部分執行 Windows 作業系統的電腦都會包含這個目錄。  這也可讓使用者以最基本的系統存取層級，便可安全執行應用程式。  下列範例假設已將 <xref:System.Windows.Forms.PictureBox> 控制項加入表單。  
  
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
  
### 若要清除圖形  
  
-   首先，釋放正由影像使用的記憶體，然後再清除圖形。  如果記憶體管理成為問題，則記憶體回收稍後將會釋放記憶體。  
  
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
    >  如需為何要以這種方式使用 <xref:System.Drawing.Image.Dispose%2A> 方法的詳細資訊，請參閱[Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md)。  
  
     即使圖形是在設計階段時載入控制項，此程式碼也會清除影像。  
  
## 請參閱  
 <xref:System.Windows.Forms.PictureBox>   
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>   
 [PictureBox 控制項概觀](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [如何：使用設計工具載入圖片](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)   
 [如何：於執行階段修改圖片的大小或位置](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)   
 [PictureBox 控制項](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)