---
title: 如何：使用 GDI+ 呈現影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182508"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="b244e-102">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="b244e-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="b244e-103">您可以使用 GDI+ 來渲染應用程式中作為檔存在的圖像。</span><span class="sxs-lookup"><span data-stu-id="b244e-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="b244e-104">為此，<xref:System.Drawing.Image>方法是創建類的新物件（如<xref:System.Drawing.Bitmap>），創建引用要使用的繪圖表面<xref:System.Drawing.Graphics>的物件，並調用<xref:System.Drawing.Graphics.DrawImage%2A><xref:System.Drawing.Graphics>物件的方法。</span><span class="sxs-lookup"><span data-stu-id="b244e-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="b244e-105">影像將繪製於此圖形類別所代表的繪圖介面上。</span><span class="sxs-lookup"><span data-stu-id="b244e-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="b244e-106">您可以使用影像編輯器在設計時創建和編輯影像檔，並在運行時使用 GDI+ 呈現它們。</span><span class="sxs-lookup"><span data-stu-id="b244e-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="b244e-107">如需詳細資訊，請參閱[圖示的影像編輯器](/cpp/windows/image-editor-for-icons)。</span><span class="sxs-lookup"><span data-stu-id="b244e-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="b244e-108">使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="b244e-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="b244e-109">建立物件，代表您想要顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="b244e-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="b244e-110">此物件必須是從 繼承的<xref:System.Drawing.Image>類的成員，<xref:System.Drawing.Bitmap>如 。 <xref:System.Drawing.Imaging.Metafile></span><span class="sxs-lookup"><span data-stu-id="b244e-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="b244e-111">範例如下︰</span><span class="sxs-lookup"><span data-stu-id="b244e-111">An example is shown:</span></span>  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. <span data-ttu-id="b244e-112">創建<xref:System.Drawing.Graphics>表示要使用的繪圖曲面的物件。</span><span class="sxs-lookup"><span data-stu-id="b244e-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="b244e-113">如需詳細資訊，請參閱[如何：建立繪圖的圖形物件](how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="b244e-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. <span data-ttu-id="b244e-114"><xref:System.Drawing.Graphics.DrawImage%2A>調用繪圖物件以渲染圖像。</span><span class="sxs-lookup"><span data-stu-id="b244e-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="b244e-115">您必須指定要繪製的影像，以及其繪製所在的座標。</span><span class="sxs-lookup"><span data-stu-id="b244e-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b244e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b244e-116">See also</span></span>

- [<span data-ttu-id="b244e-117">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="b244e-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="b244e-118">如何：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="b244e-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="b244e-119">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="b244e-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="b244e-120">如何：在 Windows Form 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="b244e-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="b244e-121">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="b244e-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="b244e-122">繪製線條或封閉圖形</span><span class="sxs-lookup"><span data-stu-id="b244e-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="b244e-123">圖示影像編輯器</span><span class="sxs-lookup"><span data-stu-id="b244e-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
