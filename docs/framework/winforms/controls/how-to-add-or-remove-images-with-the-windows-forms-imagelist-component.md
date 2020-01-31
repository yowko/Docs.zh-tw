---
title: 使用 ImageList 元件新增或移除映射
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
ms.openlocfilehash: f531003377395bf219775e5ddb48ceb0822ff0ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741509"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>如何：使用 Windows Form ImageList 元件加入或移除影像
Windows Forms <xref:System.Windows.Forms.ImageList> 元件在與控制項相關聯之前，通常會先填入影像。 不過，您可以在將影像清單與控制項建立關聯之後，新增和移除影像。  
  
> [!NOTE]
> 當您移除映射時，請確認任何相關聯控制項的 <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> 屬性仍然有效。  
  
### <a name="to-add-images-programmatically"></a>以程式設計方式新增影像  
  
- 使用影像清單的 <xref:System.Windows.Forms.ImageList.Images%2A> 屬性的 <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> 方法。  
  
     在下列程式碼範例中，為影像位置設定的路徑是 [我的**文檔**] 資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾，所以會使用這個位置。 選擇此位置也可讓具有最低系統存取層級的使用者更安全地執行應用程式。 下列程式碼範例要求您必須有已加入 <xref:System.Windows.Forms.ImageList> 控制項的表單。  
  
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
  
- 使用影像清單的其中一個 <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> 方法，其 <xref:System.Windows.Forms.ImageList.Images%2A> 屬性會接受索引鍵值。  
  
     在下列程式碼範例中，為影像位置設定的路徑是 [我的**文檔**] 資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾，所以會使用這個位置。 選擇此位置也可讓具有最低系統存取層級的使用者更安全地執行應用程式。 下列程式碼範例要求您必須有已加入 <xref:System.Windows.Forms.ImageList> 控制項的表單。  
  
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
  
- 使用 <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> 方法來移除單一映射  
  
     、-或-  
  
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
  
### <a name="to-remove-images-by-key"></a>依索引鍵移除映射  
  
- 使用 <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> 方法，依其索引鍵移除單一映射。  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>請參閱

- [ImageList 元件](imagelist-component-windows-forms.md)
- [ImageList 元件概觀](imagelist-component-overview-windows-forms.md)
- [影像、點陣圖和中繼檔](../advanced/images-bitmaps-and-metafiles.md)
