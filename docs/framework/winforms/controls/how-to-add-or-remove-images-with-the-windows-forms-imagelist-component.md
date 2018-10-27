---
title: 如何：使用 Windows Form ImageList 元件加入或移除影像
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
ms.openlocfilehash: 28dce033064517a427750ef99b1cd4f8bccaaf09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182966"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="e9d87-102">如何：使用 Windows Form ImageList 元件加入或移除影像</span><span class="sxs-lookup"><span data-stu-id="e9d87-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="e9d87-103">Windows Form<xref:System.Windows.Forms.ImageList>元件通常是填入映像之前與控制項相關聯。</span><span class="sxs-lookup"><span data-stu-id="e9d87-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="e9d87-104">不過，您可以新增並移除與控制項產生關聯的影像清單後的映像。</span><span class="sxs-lookup"><span data-stu-id="e9d87-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9d87-105">當您移除映像時，請確認<xref:System.Windows.Forms.ButtonBase.ImageIndex%2A>任何的屬性相關聯的控制項是否仍然有效。</span><span class="sxs-lookup"><span data-stu-id="e9d87-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="e9d87-106">以程式設計方式將映像</span><span class="sxs-lookup"><span data-stu-id="e9d87-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="e9d87-107">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>影像清單的方法<xref:System.Windows.Forms.ImageList.Images%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e9d87-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="e9d87-108">在下列程式碼範例中，將路徑設為映像的位置**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9d87-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="e9d87-109">因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。</span><span class="sxs-lookup"><span data-stu-id="e9d87-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="e9d87-110">選擇此位置也可讓具有最少的系統存取層級更多安全地執行應用程式的使用者。</span><span class="sxs-lookup"><span data-stu-id="e9d87-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="e9d87-111">下列程式碼範例，您需要表單<xref:System.Windows.Forms.ImageList>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="e9d87-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="e9d87-112">若要加入具有索引鍵值的影像。</span><span class="sxs-lookup"><span data-stu-id="e9d87-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="e9d87-113">使用其中一種<xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A>影像清單的方法<xref:System.Windows.Forms.ImageList.Images%2A>接受的索引鍵值的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9d87-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="e9d87-114">在下列程式碼範例中，將路徑設為映像的位置**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e9d87-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="e9d87-115">因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。</span><span class="sxs-lookup"><span data-stu-id="e9d87-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="e9d87-116">選擇此位置也可讓具有最少的系統存取層級更多安全地執行應用程式的使用者。</span><span class="sxs-lookup"><span data-stu-id="e9d87-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="e9d87-117">下列程式碼範例，您需要表單<xref:System.Windows.Forms.ImageList>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="e9d87-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="e9d87-118">若要以程式設計方式移除所有映像</span><span class="sxs-lookup"><span data-stu-id="e9d87-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="e9d87-119">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A>方法以移除單一映像</span><span class="sxs-lookup"><span data-stu-id="e9d87-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="e9d87-120">-</span><span class="sxs-lookup"><span data-stu-id="e9d87-120">,-or-</span></span>  
  
     <span data-ttu-id="e9d87-121">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A>方法，以清除所有的映像清單中的影像。</span><span class="sxs-lookup"><span data-stu-id="e9d87-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="e9d87-122">若要移除依索引鍵的影像</span><span class="sxs-lookup"><span data-stu-id="e9d87-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="e9d87-123">使用<xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A>依其索引鍵中移除單一映像的方法。</span><span class="sxs-lookup"><span data-stu-id="e9d87-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9d87-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9d87-124">See Also</span></span>  
- [<span data-ttu-id="e9d87-125">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="e9d87-125">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
- [<span data-ttu-id="e9d87-126">ImageList 元件概觀</span><span class="sxs-lookup"><span data-stu-id="e9d87-126">ImageList Component Overview</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)
- [<span data-ttu-id="e9d87-127">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="e9d87-127">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
