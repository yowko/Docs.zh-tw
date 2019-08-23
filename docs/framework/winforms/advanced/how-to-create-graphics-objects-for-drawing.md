---
title: 作法：建立繪製的圖形物件
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
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964346"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="797bb-102">HOW TO：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="797bb-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="797bb-103">您必須先建立<xref:System.Drawing.Graphics>物件, 才可以繪製線條和圖形、呈現文字, 或使用 gdi + 來顯示及操作影像。</span><span class="sxs-lookup"><span data-stu-id="797bb-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="797bb-104"><xref:System.Drawing.Graphics>物件代表 gdi + 繪圖介面, 而則是用來建立圖形影像的物件。</span><span class="sxs-lookup"><span data-stu-id="797bb-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="797bb-105">使用圖形的步驟有兩個:</span><span class="sxs-lookup"><span data-stu-id="797bb-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="797bb-106"><xref:System.Drawing.Graphics>建立物件。</span><span class="sxs-lookup"><span data-stu-id="797bb-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="797bb-107"><xref:System.Drawing.Graphics>使用物件繪製線條和圖形、呈現文字, 或顯示和操作影像。</span><span class="sxs-lookup"><span data-stu-id="797bb-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="797bb-108">建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="797bb-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="797bb-109">繪圖物件可以用各種方式建立。</span><span class="sxs-lookup"><span data-stu-id="797bb-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="797bb-110">若要建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="797bb-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="797bb-111">在表單或控制項的事件中,接收繪圖物件的參考做為的一部分。<xref:System.Windows.Forms.Control.Paint> <xref:System.Windows.Forms.PaintEventArgs></span><span class="sxs-lookup"><span data-stu-id="797bb-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="797bb-112">這通常是您在建立控制項的繪製程式碼時, 取得繪圖物件參考的方式。</span><span class="sxs-lookup"><span data-stu-id="797bb-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="797bb-113">同樣地, 您也可以在<xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage>處理的事件<xref:System.Drawing.Printing.PrintDocument>時, 取得繪圖物件做為的屬性。</span><span class="sxs-lookup"><span data-stu-id="797bb-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="797bb-114">-或-</span><span class="sxs-lookup"><span data-stu-id="797bb-114">-or-</span></span>  
  
- <span data-ttu-id="797bb-115">呼叫控制項或表單的<xref:System.Drawing.Graphics> 方法,取得代表該控制項或表單之繪圖介面的物件參考。<xref:System.Windows.Forms.Control.CreateGraphics%2A></span><span class="sxs-lookup"><span data-stu-id="797bb-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="797bb-116">如果您想要在已經存在的表單或控制項上進行繪製, 請使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="797bb-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="797bb-117">-或-</span><span class="sxs-lookup"><span data-stu-id="797bb-117">-or-</span></span>  
  
- <span data-ttu-id="797bb-118">從繼承自<xref:System.Drawing.Image>的任何物件建立物件。<xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="797bb-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="797bb-119">當您想要改變已經存在的映射時, 這個方法很有用。</span><span class="sxs-lookup"><span data-stu-id="797bb-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="797bb-120">下列各節提供有關每個處理常式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="797bb-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="797bb-121">繪製事件處理常式中的 PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="797bb-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="797bb-122"><xref:System.Windows.Forms.PaintEventHandler>針對控制項<xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>或<xref:System.Drawing.Printing.PrintDocument.PrintPage> 的進行程式設計時,會將繪圖物件當做或的其中一個<xref:System.Drawing.Printing.PrintDocument>屬性來提供。</span><span class="sxs-lookup"><span data-stu-id="797bb-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="797bb-123">從繪製事件中的 PaintEventArgs 取得繪圖物件的參考</span><span class="sxs-lookup"><span data-stu-id="797bb-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="797bb-124"><xref:System.Drawing.Graphics>宣告物件。</span><span class="sxs-lookup"><span data-stu-id="797bb-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="797bb-125">指派變數來參考<xref:System.Drawing.Graphics>當做一部分<xref:System.Windows.Forms.PaintEventArgs>傳遞的物件。</span><span class="sxs-lookup"><span data-stu-id="797bb-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="797bb-126">插入程式碼以繪製表單或控制項。</span><span class="sxs-lookup"><span data-stu-id="797bb-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="797bb-127">下列範例顯示如何從<xref:System.Drawing.Graphics> <xref:System.Windows.Forms.Control.Paint>事件的<xref:System.Windows.Forms.PaintEventArgs>中參考物件:</span><span class="sxs-lookup"><span data-stu-id="797bb-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="797bb-128">CreateGraphics 方法</span><span class="sxs-lookup"><span data-stu-id="797bb-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="797bb-129">您也可以使用<xref:System.Windows.Forms.Control.CreateGraphics%2A>控制項或表單的方法, 取得代表該控制項或表單之繪圖介面的<xref:System.Drawing.Graphics>物件參考。</span><span class="sxs-lookup"><span data-stu-id="797bb-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="797bb-130">若要使用 CreateGraphics 方法建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="797bb-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="797bb-131">呼叫您要呈現圖形的表單或控制項的方法。<xref:System.Windows.Forms.Control.CreateGraphics%2A></span><span class="sxs-lookup"><span data-stu-id="797bb-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="797bb-132">從 Image 物件建立</span><span class="sxs-lookup"><span data-stu-id="797bb-132">Create from an Image Object</span></span>  
 <span data-ttu-id="797bb-133">此外, 您可以從衍生自<xref:System.Drawing.Image>類別的任何物件建立繪圖物件。</span><span class="sxs-lookup"><span data-stu-id="797bb-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="797bb-134">若要從影像建立繪圖物件</span><span class="sxs-lookup"><span data-stu-id="797bb-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="797bb-135">呼叫方法, 並提供您想要從中<xref:System.Drawing.Graphics>建立物件之映射變數的名稱。 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="797bb-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="797bb-136">下列範例顯示如何使用<xref:System.Drawing.Bitmap>物件:</span><span class="sxs-lookup"><span data-stu-id="797bb-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="797bb-137">您只能從非<xref:System.Drawing.Graphics>索引的 .bmp 檔案 (例如, 16 位、24位和32位的 .bmp 檔案) 建立物件。</span><span class="sxs-lookup"><span data-stu-id="797bb-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="797bb-138">非索引 .bmp 檔案的每個圖元都有一個色彩, 相對於已編制索引之 .bmp 檔案的圖元, 這些檔案會保存色彩表的索引。</span><span class="sxs-lookup"><span data-stu-id="797bb-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="797bb-139">繪製和操作圖形和影像</span><span class="sxs-lookup"><span data-stu-id="797bb-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="797bb-140">建立之後, <xref:System.Drawing.Graphics>物件可以用來繪製線條和圖形、呈現文字, 或顯示和操作影像。</span><span class="sxs-lookup"><span data-stu-id="797bb-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="797bb-141">與<xref:System.Drawing.Graphics>物件搭配使用的主要物件為:</span><span class="sxs-lookup"><span data-stu-id="797bb-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="797bb-142"><xref:System.Drawing.Pen>類別: 用於繪製線條、大綱圖形或轉譯其他幾何標記法。</span><span class="sxs-lookup"><span data-stu-id="797bb-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="797bb-143"><xref:System.Drawing.Brush>類別: 用來填滿圖形的區域, 例如填滿的圖形、影像或文字。</span><span class="sxs-lookup"><span data-stu-id="797bb-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="797bb-144"><xref:System.Drawing.Font>類別: 提供呈現文字時所要使用之圖形的描述。</span><span class="sxs-lookup"><span data-stu-id="797bb-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="797bb-145"><xref:System.Drawing.Color>結構: 代表要顯示的不同色彩。</span><span class="sxs-lookup"><span data-stu-id="797bb-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="797bb-146">若要使用您所建立的繪圖物件</span><span class="sxs-lookup"><span data-stu-id="797bb-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="797bb-147">使用上方所列的適當物件來繪製您所需的內容。</span><span class="sxs-lookup"><span data-stu-id="797bb-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="797bb-148">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="797bb-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="797bb-149">呈現</span><span class="sxs-lookup"><span data-stu-id="797bb-149">To render</span></span>|<span data-ttu-id="797bb-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="797bb-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="797bb-151">線條</span><span class="sxs-lookup"><span data-stu-id="797bb-151">Lines</span></span>|[<span data-ttu-id="797bb-152">如何：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="797bb-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="797bb-153">圖形</span><span class="sxs-lookup"><span data-stu-id="797bb-153">Shapes</span></span>|[<span data-ttu-id="797bb-154">如何：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="797bb-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="797bb-155">文字</span><span class="sxs-lookup"><span data-stu-id="797bb-155">Text</span></span>|[<span data-ttu-id="797bb-156">如何：在 Windows Form 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="797bb-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="797bb-157">影像</span><span class="sxs-lookup"><span data-stu-id="797bb-157">Images</span></span>|[<span data-ttu-id="797bb-158">如何：使用 GDI + 呈現影像</span><span class="sxs-lookup"><span data-stu-id="797bb-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="797bb-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="797bb-159">See also</span></span>

- [<span data-ttu-id="797bb-160">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="797bb-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="797bb-161">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="797bb-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="797bb-162">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="797bb-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="797bb-163">如何：使用 GDI + 呈現影像</span><span class="sxs-lookup"><span data-stu-id="797bb-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
