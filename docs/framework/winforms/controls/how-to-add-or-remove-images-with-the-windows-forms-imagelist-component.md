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
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="03e1e-102">如何：使用 Windows Form ImageList 元件加入或移除影像</span><span class="sxs-lookup"><span data-stu-id="03e1e-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="03e1e-103">Windows 表單<xref:System.Windows.Forms.ImageList>元件通常在與控制項關聯之前填充圖像。</span><span class="sxs-lookup"><span data-stu-id="03e1e-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="03e1e-104">但是，您可以將圖像清單與控制項關聯後添加和刪除圖像。</span><span class="sxs-lookup"><span data-stu-id="03e1e-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03e1e-105">刪除圖像時，請驗證任何關聯的<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>控制項的屬性是否仍然有效。</span><span class="sxs-lookup"><span data-stu-id="03e1e-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="03e1e-106">以程式設計方式添加圖像</span><span class="sxs-lookup"><span data-stu-id="03e1e-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="03e1e-107">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>圖像清單<xref:System.Windows.Forms.ImageList.Images%2A>屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="03e1e-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="03e1e-108">在下面的代碼示例中，為圖像位置設置的路徑是 **"我的文件"** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="03e1e-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="03e1e-109">使用此位置是因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此資料夾。</span><span class="sxs-lookup"><span data-stu-id="03e1e-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="03e1e-110">選擇此位置還使具有最小系統存取層級的使用者能夠更安全地運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="03e1e-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="03e1e-111">以下代碼示例要求您具有已添加控制項的<xref:System.Windows.Forms.ImageList>表單。</span><span class="sxs-lookup"><span data-stu-id="03e1e-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="03e1e-112">添加具有鍵值的圖像。</span><span class="sxs-lookup"><span data-stu-id="03e1e-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="03e1e-113">使用圖像清單<xref:System.Windows.Forms.ImageList.Images%2A>屬性<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>中採用鍵值的方法之一。</span><span class="sxs-lookup"><span data-stu-id="03e1e-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="03e1e-114">在下面的代碼示例中，為圖像位置設置的路徑是 **"我的文件"** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="03e1e-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="03e1e-115">使用此位置是因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此資料夾。</span><span class="sxs-lookup"><span data-stu-id="03e1e-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="03e1e-116">選擇此位置還使具有最小系統存取層級的使用者能夠更安全地運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="03e1e-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="03e1e-117">以下代碼示例要求您具有已添加控制項的<xref:System.Windows.Forms.ImageList>表單。</span><span class="sxs-lookup"><span data-stu-id="03e1e-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="03e1e-118">以程式設計方式刪除所有圖像</span><span class="sxs-lookup"><span data-stu-id="03e1e-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="03e1e-119">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>方法刪除單個圖像</span><span class="sxs-lookup"><span data-stu-id="03e1e-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="03e1e-120">或-</span><span class="sxs-lookup"><span data-stu-id="03e1e-120">,-or-</span></span>  
  
     <span data-ttu-id="03e1e-121">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>方法清除圖像清單中的所有圖像。</span><span class="sxs-lookup"><span data-stu-id="03e1e-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="03e1e-122">按鍵刪除圖像</span><span class="sxs-lookup"><span data-stu-id="03e1e-122">To remove images by key</span></span>  
  
- <span data-ttu-id="03e1e-123">使用<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>方法按其鍵刪除單個圖像。</span><span class="sxs-lookup"><span data-stu-id="03e1e-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="03e1e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03e1e-124">See also</span></span>

- [<span data-ttu-id="03e1e-125">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="03e1e-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="03e1e-126">ImageList 元件概觀</span><span class="sxs-lookup"><span data-stu-id="03e1e-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="03e1e-127">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="03e1e-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
