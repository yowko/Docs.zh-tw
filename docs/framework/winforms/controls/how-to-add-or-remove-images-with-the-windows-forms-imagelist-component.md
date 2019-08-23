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
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="79723-102">作法：使用 Windows Forms ImageList 元件新增或移除影像</span><span class="sxs-lookup"><span data-stu-id="79723-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="79723-103">Windows Forms <xref:System.Windows.Forms.ImageList>元件在與控制項相關聯之前, 通常會先填入影像。</span><span class="sxs-lookup"><span data-stu-id="79723-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="79723-104">不過, 您可以在將影像清單與控制項建立關聯之後, 新增和移除影像。</span><span class="sxs-lookup"><span data-stu-id="79723-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79723-105">當您移除映射時, 請確認<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>任何相關聯控制項的屬性仍然有效。</span><span class="sxs-lookup"><span data-stu-id="79723-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="79723-106">以程式設計方式新增影像</span><span class="sxs-lookup"><span data-stu-id="79723-106">To add images programmatically</span></span>  
  
- <span data-ttu-id="79723-107">使用影像清單的<xref:System.Windows.Forms.ImageList.Images%2A>屬性的方法。<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A></span><span class="sxs-lookup"><span data-stu-id="79723-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="79723-108">在下列程式碼範例中, 為影像位置設定的路徑是 [我的**文檔**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="79723-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="79723-109">因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾, 所以會使用這個位置。</span><span class="sxs-lookup"><span data-stu-id="79723-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="79723-110">選擇此位置也可讓具有最低系統存取層級的使用者更安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="79723-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="79723-111">下列程式碼範例要求您的表單<xref:System.Windows.Forms.ImageList>已經加入控制項。</span><span class="sxs-lookup"><span data-stu-id="79723-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="79723-112">新增具有金鑰值的映射。</span><span class="sxs-lookup"><span data-stu-id="79723-112">To add images with a key value.</span></span>  
  
- <span data-ttu-id="79723-113">使用影像<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> <xref:System.Windows.Forms.ImageList.Images%2A>清單屬性的其中一個方法, 以取得索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="79723-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="79723-114">在下列程式碼範例中, 為影像位置設定的路徑是 [我的**文檔**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="79723-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="79723-115">因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾, 所以會使用這個位置。</span><span class="sxs-lookup"><span data-stu-id="79723-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="79723-116">選擇此位置也可讓具有最低系統存取層級的使用者更安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="79723-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="79723-117">下列程式碼範例要求您的表單<xref:System.Windows.Forms.ImageList>已經加入控制項。</span><span class="sxs-lookup"><span data-stu-id="79723-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="79723-118">以程式設計方式移除所有影像</span><span class="sxs-lookup"><span data-stu-id="79723-118">To remove all images programmatically</span></span>  
  
- <span data-ttu-id="79723-119"><xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>使用方法來移除單一映射</span><span class="sxs-lookup"><span data-stu-id="79723-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="79723-120">、-或-</span><span class="sxs-lookup"><span data-stu-id="79723-120">,-or-</span></span>  
  
     <span data-ttu-id="79723-121"><xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>使用方法清除影像清單中的所有影像。</span><span class="sxs-lookup"><span data-stu-id="79723-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="79723-122">依索引鍵移除映射</span><span class="sxs-lookup"><span data-stu-id="79723-122">To remove images by key</span></span>  
  
- <span data-ttu-id="79723-123"><xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>使用方法, 依其索引鍵來移除單一映射。</span><span class="sxs-lookup"><span data-stu-id="79723-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="79723-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79723-124">See also</span></span>

- [<span data-ttu-id="79723-125">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="79723-125">ImageList Component</span></span>](imagelist-component-windows-forms.md)
- [<span data-ttu-id="79723-126">ImageList 元件概觀</span><span class="sxs-lookup"><span data-stu-id="79723-126">ImageList Component Overview</span></span>](imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="79723-127">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="79723-127">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
