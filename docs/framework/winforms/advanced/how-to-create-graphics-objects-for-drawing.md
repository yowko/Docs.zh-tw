---
title: 如何：建立繪製的圖形物件
description: 立即瞭解如何建立繪圖物件，您需要繪製線條和圖形、呈現文字，或使用 GDI + 來顯示及操作影像。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903203"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="04819-103">如何：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="04819-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="04819-104">您必須先建立物件，才可以繪製線條和圖形、呈現文字，或使用 GDI + 來顯示及操作影像 <xref:System.Drawing.Graphics> 。</span><span class="sxs-lookup"><span data-stu-id="04819-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="04819-105"><xref:System.Drawing.Graphics>物件代表 GDI + 繪圖介面，而則是用來建立圖形影像的物件。</span><span class="sxs-lookup"><span data-stu-id="04819-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="04819-106">使用圖形的步驟有兩個：</span><span class="sxs-lookup"><span data-stu-id="04819-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="04819-107">建立 <xref:System.Drawing.Graphics> 物件。</span><span class="sxs-lookup"><span data-stu-id="04819-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="04819-108">使用 <xref:System.Drawing.Graphics> 物件繪製線條和圖形、呈現文字，或顯示和操作影像。</span><span class="sxs-lookup"><span data-stu-id="04819-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="04819-109">建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="04819-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="04819-110">繪圖物件可以用各種方式建立。</span><span class="sxs-lookup"><span data-stu-id="04819-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="04819-111">若要建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="04819-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="04819-112"><xref:System.Windows.Forms.PaintEventArgs>在 <xref:System.Windows.Forms.Control.Paint> 表單或控制項的事件中，接收繪圖物件的參考做為的一部分。</span><span class="sxs-lookup"><span data-stu-id="04819-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="04819-113">這通常是您在建立控制項的繪製程式碼時，取得繪圖物件參考的方式。</span><span class="sxs-lookup"><span data-stu-id="04819-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="04819-114">同樣地，您也可以在處理的事件時，取得繪圖物件做為的屬性 <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> 。</span><span class="sxs-lookup"><span data-stu-id="04819-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="04819-115">-或-</span><span class="sxs-lookup"><span data-stu-id="04819-115">-or-</span></span>  
  
- <span data-ttu-id="04819-116">呼叫 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控制項或表單的方法，取得 <xref:System.Drawing.Graphics> 代表該控制項或表單之繪圖介面的物件參考。</span><span class="sxs-lookup"><span data-stu-id="04819-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="04819-117">如果您想要在已經存在的表單或控制項上進行繪製，請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="04819-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="04819-118">-或-</span><span class="sxs-lookup"><span data-stu-id="04819-118">-or-</span></span>  
  
- <span data-ttu-id="04819-119"><xref:System.Drawing.Graphics>從繼承自的任何物件建立物件 <xref:System.Drawing.Image> 。</span><span class="sxs-lookup"><span data-stu-id="04819-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="04819-120">當您想要改變已經存在的映射時，這個方法很有用。</span><span class="sxs-lookup"><span data-stu-id="04819-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="04819-121">下列各節提供有關每個處理常式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="04819-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="04819-122">繪製事件處理常式中的 PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="04819-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="04819-123">針對控制項或的進行程式設計時 <xref:System.Windows.Forms.PaintEventHandler> <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> ，會將繪圖物件當做或的其中一個屬性來提供 <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="04819-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="04819-124">從繪製事件中的 PaintEventArgs 取得繪圖物件的參考</span><span class="sxs-lookup"><span data-stu-id="04819-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="04819-125">宣告 <xref:System.Drawing.Graphics> 物件。</span><span class="sxs-lookup"><span data-stu-id="04819-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="04819-126">指派變數來參考當做 <xref:System.Drawing.Graphics> 一部分傳遞的物件 <xref:System.Windows.Forms.PaintEventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="04819-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="04819-127">插入程式碼以繪製表單或控制項。</span><span class="sxs-lookup"><span data-stu-id="04819-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="04819-128">下列範例顯示如何 <xref:System.Drawing.Graphics> 從事件的中參考物件 <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> ：</span><span class="sxs-lookup"><span data-stu-id="04819-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="04819-129">CreateGraphics 方法</span><span class="sxs-lookup"><span data-stu-id="04819-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="04819-130">您也可以使用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控制項或表單的方法，取得 <xref:System.Drawing.Graphics> 代表該控制項或表單之繪圖介面的物件參考。</span><span class="sxs-lookup"><span data-stu-id="04819-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="04819-131">若要使用 CreateGraphics 方法建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="04819-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="04819-132">呼叫 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 您要呈現圖形的表單或控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="04819-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="04819-133">從 Image 物件建立</span><span class="sxs-lookup"><span data-stu-id="04819-133">Create from an Image Object</span></span>  
 <span data-ttu-id="04819-134">此外，您可以從衍生自類別的任何物件建立繪圖物件 <xref:System.Drawing.Image> 。</span><span class="sxs-lookup"><span data-stu-id="04819-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="04819-135">若要從影像建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="04819-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="04819-136">呼叫 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> 方法，並提供您想要從中建立物件之映射變數的名稱 <xref:System.Drawing.Graphics> 。</span><span class="sxs-lookup"><span data-stu-id="04819-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="04819-137">下列範例顯示如何使用 <xref:System.Drawing.Bitmap> 物件：</span><span class="sxs-lookup"><span data-stu-id="04819-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> <span data-ttu-id="04819-138">您只能從非 <xref:System.Drawing.Graphics> 索引的 .bmp 檔案（例如，16位、24位和32位的 .bmp 檔案）建立物件。</span><span class="sxs-lookup"><span data-stu-id="04819-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="04819-139">非索引 .bmp 檔案的每個圖元都有一個色彩，相對於已編制索引之 .bmp 檔案的圖元，這些檔案會保存色彩表的索引。</span><span class="sxs-lookup"><span data-stu-id="04819-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="04819-140">繪製和操作圖形和影像</span><span class="sxs-lookup"><span data-stu-id="04819-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="04819-141">建立之後， <xref:System.Drawing.Graphics> 物件可以用來繪製線條和圖形、呈現文字，或顯示和操作影像。</span><span class="sxs-lookup"><span data-stu-id="04819-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="04819-142">與物件搭配使用的主要物件 <xref:System.Drawing.Graphics> 為：</span><span class="sxs-lookup"><span data-stu-id="04819-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="04819-143"><xref:System.Drawing.Pen>類別：用於繪製線條、大綱圖形或轉譯其他幾何標記法。</span><span class="sxs-lookup"><span data-stu-id="04819-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="04819-144"><xref:System.Drawing.Brush>類別：用來填滿圖形的區域，例如填滿的圖形、影像或文字。</span><span class="sxs-lookup"><span data-stu-id="04819-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="04819-145"><xref:System.Drawing.Font>類別：提供呈現文字時所要使用之圖形的描述。</span><span class="sxs-lookup"><span data-stu-id="04819-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="04819-146"><xref:System.Drawing.Color>結構：代表要顯示的不同色彩。</span><span class="sxs-lookup"><span data-stu-id="04819-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="04819-147">若要使用您所建立的繪圖物件</span><span class="sxs-lookup"><span data-stu-id="04819-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="04819-148">使用上方所列的適當物件來繪製您所需的內容。</span><span class="sxs-lookup"><span data-stu-id="04819-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="04819-149">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="04819-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="04819-150">呈現</span><span class="sxs-lookup"><span data-stu-id="04819-150">To render</span></span>|<span data-ttu-id="04819-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="04819-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="04819-152">線條</span><span class="sxs-lookup"><span data-stu-id="04819-152">Lines</span></span>|[<span data-ttu-id="04819-153">操作說明：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="04819-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="04819-154">圖形</span><span class="sxs-lookup"><span data-stu-id="04819-154">Shapes</span></span>|[<span data-ttu-id="04819-155">如何：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="04819-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="04819-156">Text</span><span class="sxs-lookup"><span data-stu-id="04819-156">Text</span></span>|[<span data-ttu-id="04819-157">如何：在 Windows Form 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="04819-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="04819-158">影像</span><span class="sxs-lookup"><span data-stu-id="04819-158">Images</span></span>|[<span data-ttu-id="04819-159">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="04819-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="04819-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04819-160">See also</span></span>

- [<span data-ttu-id="04819-161">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="04819-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="04819-162">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="04819-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="04819-163">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="04819-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="04819-164">如何：使用 GDI+ 呈現影像</span><span class="sxs-lookup"><span data-stu-id="04819-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
