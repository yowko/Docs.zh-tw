---
title: 使用圖像清單元件添加或刪除圖像
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
ms.openlocfilehash: e045be7ea9407bc379b0c22282fcd2184ff5db51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182292"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>如何：使用 Windows Form ImageList 元件加入或移除影像
Windows 表單<xref:System.Windows.Forms.ImageList>元件通常在與控制項關聯之前填充圖像。 但是，您可以將圖像清單與控制項關聯後添加和刪除圖像。  
  
> [!NOTE]
> 刪除圖像時，請驗證任何關聯的<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>控制項的屬性是否仍然有效。  
  
### <a name="to-add-images-programmatically"></a>以程式設計方式添加圖像  
  
- 使用<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>圖像清單<xref:System.Windows.Forms.ImageList.Images%2A>屬性的方法。  
  
     在下面的代碼示例中，為圖像位置設置的路徑是 **"我的文件"** 資料夾。 使用此位置是因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此資料夾。 選擇此位置還使具有最小系統存取層級的使用者能夠更安全地運行應用程式。 以下代碼示例要求您具有已添加控制項的<xref:System.Windows.Forms.ImageList>表單。  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>添加具有鍵值的圖像。  
  
- 使用圖像清單<xref:System.Windows.Forms.ImageList.Images%2A>屬性<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>中採用鍵值的方法之一。  
  
     在下面的代碼示例中，為圖像位置設置的路徑是 **"我的文件"** 資料夾。 使用此位置是因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此資料夾。 選擇此位置還使具有最小系統存取層級的使用者能夠更安全地運行應用程式。 以下代碼示例要求您具有已添加控制項的<xref:System.Windows.Forms.ImageList>表單。  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>以程式設計方式刪除所有圖像  
  
- 使用<xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>方法刪除單個圖像  
  
     或-  
  
     使用<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>方法清除圖像清單中的所有圖像。  
  
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
  
### <a name="to-remove-images-by-key"></a>按鍵刪除圖像  
  
- 使用<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>方法按其鍵刪除單個圖像。  
  
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
