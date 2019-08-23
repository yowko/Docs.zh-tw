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
ms.openlocfilehash: 430b7f573b115c21b9e2fa87f0ace74205717285
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925125"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>作法：使用 Windows Forms ImageList 元件新增或移除影像
Windows Forms <xref:System.Windows.Forms.ImageList>元件在與控制項相關聯之前, 通常會先填入影像。 不過, 您可以在將影像清單與控制項建立關聯之後, 新增和移除影像。  
  
> [!NOTE]
> 當您移除映射時, 請確認<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>任何相關聯控制項的屬性仍然有效。  
  
### <a name="to-add-images-programmatically"></a>以程式設計方式新增影像  
  
- 使用影像清單的<xref:System.Windows.Forms.ImageList.Images%2A>屬性的方法。<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>  
  
     在下列程式碼範例中, 為影像位置設定的路徑是 [我的**文檔**] 資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾, 所以會使用這個位置。 選擇此位置也可讓具有最低系統存取層級的使用者更安全地執行應用程式。 下列程式碼範例要求您的表單<xref:System.Windows.Forms.ImageList>已經加入控制項。  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>新增具有金鑰值的映射。  
  
- 使用影像<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> <xref:System.Windows.Forms.ImageList.Images%2A>清單屬性的其中一個方法, 以取得索引鍵值。  
  
     在下列程式碼範例中, 為影像位置設定的路徑是 [我的**文檔**] 資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾, 所以會使用這個位置。 選擇此位置也可讓具有最低系統存取層級的使用者更安全地執行應用程式。 下列程式碼範例要求您的表單<xref:System.Windows.Forms.ImageList>已經加入控制項。  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>以程式設計方式移除所有影像  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>使用方法來移除單一映射  
  
     、-或-  
  
     <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>使用方法清除影像清單中的所有影像。  
  
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
  
### <a name="to-remove-images-by-key"></a>依索引鍵移除映射  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>使用方法, 依其索引鍵來移除單一映射。  
  
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
