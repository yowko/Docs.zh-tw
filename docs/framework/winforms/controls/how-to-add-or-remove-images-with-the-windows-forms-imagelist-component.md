---
title: "如何：使用 Windows Form ImageList 元件加入或移除影像 | Microsoft Docs"
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
  - "ImageList 元件 [Windows Form], 加入影像"
  - "ImageList 元件 [Windows Form], 移除影像"
  - "影像 [Windows Form], 加入至 ImageList 元件"
  - "影像 [Windows Form], 與控制項一起顯示"
  - "影像 [Windows Form], 自 ImageList 元件移除"
  - "影像 [Windows Form], 儲存供控制項使用"
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 Windows Form ImageList 元件加入或移除影像
Windows Form <xref:System.Windows.Forms.ImageList> 元件在與另一控制項產生關聯之前通常會先填入 \(Populate\) 影像。  不過，在影像清單與另一控制項產生關聯後，仍可加入和移除影像。  
  
> [!NOTE]
>  當您移除影像時，請確認關聯的控制項之 <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> 屬性是否仍有效。  
  
### 若要以程式設計的方式加入影像  
  
-   使用影像清單的 <xref:System.Windows.Forms.ImageList.Images%2A> 屬性的 <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> 方法。  
  
     在下列程式碼範例中，影像的位置路徑設定為 \[**我的文件**\] 資料夾。  這個位置的使用，是因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個資料夾。  選擇這個位置也可以讓具有最基本系統存取層級的使用者，能夠更安全地執行應用程式。  下列程式碼範例假設您已經在表單中加入 <xref:System.Windows.Forms.ImageList> 控制項。  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the   
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =   
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample   
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as   
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =   
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### 若要使用機碼值加入影像  
  
-   使用影像清單的 <xref:System.Windows.Forms.ImageList.Images%2A> 屬性的其中一個 <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> 方法，該屬性採用一個機碼值。  
  
     在下列程式碼範例中，影像的位置路徑設定為 \[**我的文件**\] 資料夾。  這個位置的使用，是因為您可以假設大部分執行 Windows 作業系統的電腦都會包含這個資料夾。  選擇這個位置也可以讓具有最基本系統存取層級的使用者，能夠更安全地執行應用程式。  下列程式碼範例假設您已經在表單中加入 <xref:System.Windows.Forms.ImageList> 控制項。  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the   
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =   
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
  
```  
  
### 若要以程式設計的方式移除所有影像  
  
-   使用 <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> 方法來移除單一影像，  
  
     \-或\-  
  
     使用 <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> 方法來清除影像清單中的所有影像。  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
  
```  
  
### 若要根據機碼值移除影像  
  
-   使用 <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> 方法來根據機碼值移除單一影像。  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
  
```  
  
## 請參閱  
 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)   
 [ImageList 元件概觀](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)   
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)