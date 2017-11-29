---
title: "如何：使用 GDI+ 呈現影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c0b4c128667cab04ca8ed015b44dae60d11b474
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="0109c-102">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="0109c-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="0109c-103">您可以使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 來呈現應用程式中以檔案形式存在的影像。</span><span class="sxs-lookup"><span data-stu-id="0109c-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="0109c-104">您可以建立新物件的<xref:System.Drawing.Image>類別 (例如<xref:System.Drawing.Bitmap>)、 建立<xref:System.Drawing.Graphics>物件，代表您要使用的繪圖介面，並呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="0109c-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="0109c-105">影像將繪製於此圖形類別所代表的繪圖介面上。</span><span class="sxs-lookup"><span data-stu-id="0109c-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="0109c-106">您可以在設計階段使用影像編輯器來建立及編輯影像檔案，而在執行階段使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 來呈現它們。</span><span class="sxs-lookup"><span data-stu-id="0109c-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="0109c-107">如需詳細資訊，請參閱[圖示的影像編輯器](/cpp/windows/image-editor-for-icons)。</span><span class="sxs-lookup"><span data-stu-id="0109c-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="0109c-108">使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="0109c-108">To render an image with GDI+</span></span>  
  
1.  <span data-ttu-id="0109c-109">建立物件，代表您想要顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="0109c-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="0109c-110">這個物件必須繼承自一個類別的成員<xref:System.Drawing.Image>，例如<xref:System.Drawing.Bitmap>或<xref:System.Drawing.Imaging.Metafile>。</span><span class="sxs-lookup"><span data-stu-id="0109c-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="0109c-111">範例如下︰</span><span class="sxs-lookup"><span data-stu-id="0109c-111">An example is shown:</span></span>  
  
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
  
2.  <span data-ttu-id="0109c-112">建立<xref:System.Drawing.Graphics>代表您想要使用的繪圖介面的物件。</span><span class="sxs-lookup"><span data-stu-id="0109c-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="0109c-113">如需詳細資訊，請參閱[如何：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="0109c-113">For more information, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3.  <span data-ttu-id="0109c-114">呼叫<xref:System.Drawing.Graphics.DrawImage%2A>的圖形物件呈現影像。</span><span class="sxs-lookup"><span data-stu-id="0109c-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="0109c-115">您必須指定要繪製的影像，以及其繪製所在的座標。</span><span class="sxs-lookup"><span data-stu-id="0109c-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0109c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0109c-116">See Also</span></span>  
 [<span data-ttu-id="0109c-117">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="0109c-117">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="0109c-118">操作說明：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="0109c-118">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="0109c-119">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="0109c-119">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [<span data-ttu-id="0109c-120">操作說明：在 Windows Forms 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="0109c-120">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [<span data-ttu-id="0109c-121">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="0109c-121">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="0109c-122">繪製線條或封閉的圖形</span><span class="sxs-lookup"><span data-stu-id="0109c-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [<span data-ttu-id="0109c-123">圖示影像編輯器</span><span class="sxs-lookup"><span data-stu-id="0109c-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
