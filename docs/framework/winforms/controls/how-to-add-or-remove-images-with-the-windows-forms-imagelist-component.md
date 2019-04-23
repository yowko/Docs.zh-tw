---
title: HOW TO：使用 Windows Forms ImageList 元件新增或移除影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: 286b56cddc18589b936a7f053a12ed44c81a32b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072970"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>HOW TO：使用 Windows Forms ImageList 元件新增或移除影像
Windows Form<xref:System.Windows.Forms.ImageList>元件通常是填入映像之前與控制項相關聯。 不過，您可以新增並移除與控制項產生關聯的影像清單後的映像。  
  
> [!NOTE]
>  當您移除映像時，請確認<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>任何的屬性相關聯的控制項是否仍然有效。  
  
### <a name="to-add-images-programmatically"></a>以程式設計方式將映像  
  
-   使用<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>影像清單的方法<xref:System.Windows.Forms.ImageList.Images%2A>屬性。  
  
     在下列程式碼範例中，將路徑設為映像的位置**我的文件**資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。 選擇此位置也可讓具有最少的系統存取層級更多安全地執行應用程式的使用者。 下列程式碼範例，您需要表單<xref:System.Windows.Forms.ImageList>已經加入的控制項。  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>若要加入具有索引鍵值的影像。  
  
-   使用其中一種<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>影像清單的方法<xref:System.Windows.Forms.ImageList.Images%2A>接受的索引鍵值的屬性。  
  
     在下列程式碼範例中，將路徑設為映像的位置**我的文件**資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。 選擇此位置也可讓具有最少的系統存取層級更多安全地執行應用程式的使用者。 下列程式碼範例，您需要表單<xref:System.Windows.Forms.ImageList>已經加入的控制項。  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>若要以程式設計方式移除所有映像  
  
-   使用<xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>方法以移除單一映像  
  
     -  
  
     使用<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>方法，以清除所有的映像清單中的影像。  
  
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
  
### <a name="to-remove-images-by-key"></a>若要移除依索引鍵的影像  
  
-   使用<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>依其索引鍵中移除單一映像的方法。  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>另請參閱

- [ImageList 元件](imagelist-component-windows-forms.md)
- [ImageList 元件概觀](imagelist-component-overview-windows-forms.md)
- [影像、點陣圖和中繼檔](../advanced/images-bitmaps-and-metafiles.md)
