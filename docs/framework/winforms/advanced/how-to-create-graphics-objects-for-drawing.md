---
title: 如何：建立繪製的圖形物件
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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142429"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>如何：建立繪製的圖形物件
在使用 GDI+ 繪製線條和形狀、渲染文本或顯示和操作圖像之前，需要創建一個<xref:System.Drawing.Graphics>物件。 該<xref:System.Drawing.Graphics>物件表示 GDI+ 繪圖表面，是用於創建圖形圖像的物件。  
  
 使用圖形有兩個步驟：  
  
1. 創建<xref:System.Drawing.Graphics>物件。  
  
2. 使用<xref:System.Drawing.Graphics>物件繪製線條和形狀、渲染文本或顯示和操作圖像。  
  
## <a name="creating-a-graphics-object"></a>創建繪圖物件  
 繪圖物件可以通過多種方式創建。  
  
#### <a name="to-create-a-graphics-object"></a>創建繪圖物件  
  
- 在表單或控制項<xref:System.Windows.Forms.PaintEventArgs><xref:System.Windows.Forms.Control.Paint>的情況下，接收對繪圖物件的引用，作為 的一部分。 這通常是在為控制項創建繪製代碼時獲取繪圖物件的引用的方式。 同樣，在處理 的事件<xref:System.Drawing.Printing.PrintPageEventArgs>時<xref:System.Drawing.Printing.PrintDocument.PrintPage>，還可以獲取繪圖物件作為<xref:System.Drawing.Printing.PrintDocument>屬性。  
  
     -或-  
  
- 調用控制項<xref:System.Windows.Forms.Control.CreateGraphics%2A>或表單的方法以獲取對表示該控制項或表單的繪圖<xref:System.Drawing.Graphics>表面的物件的引用。 如果要在已存在的表單或控制項上繪製，請使用此方法。  
  
     -或-  
  
- 從<xref:System.Drawing.Graphics>繼承的任何<xref:System.Drawing.Image>物件創建物件。 當您要更改已有的映射時，此方法非常有用。  
  
     以下各節詳細介紹了每個過程。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>繪製事件處理常式中的繪製事件  
 在程式設計<xref:System.Windows.Forms.PaintEventHandler>控制項 或<xref:System.Drawing.Printing.PrintDocument.PrintPage>的 時<xref:System.Drawing.Printing.PrintDocument>，繪圖物件作為 或<xref:System.Windows.Forms.PaintEventArgs><xref:System.Drawing.Printing.PrintPageEventArgs>的屬性之一提供。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>從"繪製"事件中的"繪製事件"中獲取對繪圖物件的引用  
  
1. 聲明物件<xref:System.Drawing.Graphics>。  
  
2. 分配變數以引用作為 的<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>一部分傳遞的物件。  
  
3. 插入代碼以繪製表單或控制項。  
  
     下面的示例演示如何引用<xref:System.Drawing.Graphics><xref:System.Windows.Forms.PaintEventArgs>事件中<xref:System.Windows.Forms.Control.Paint>的物件：  
  
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
  
## <a name="creategraphics-method"></a>創建圖形方法  
 您還可以使用控制項或表單<xref:System.Windows.Forms.Control.CreateGraphics%2A>的方法來獲取對表示該控制項或表單的繪圖表面<xref:System.Drawing.Graphics>的物件的引用。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>使用"創建圖形"方法創建繪圖物件  
  
- 調用要<xref:System.Windows.Forms.Control.CreateGraphics%2A>呈現圖形的表單或控制項的方法。  
  
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
  
## <a name="create-from-an-image-object"></a>從影像物件創建  
 此外，還可以從從<xref:System.Drawing.Image>類派生的任何物件創建繪圖物件。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>從圖像創建繪圖物件  
  
- 調用<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>方法，提供要從中創建<xref:System.Drawing.Graphics>物件的 Image 變數的名稱。  
  
     下面的示例演示如何使用<xref:System.Drawing.Bitmap>物件：  
  
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
> 只能從非索引<xref:System.Drawing.Graphics>的 .bmp 檔創建物件，例如 16 位、24 位和 32 位 .bmp 檔。 非索引 .bmp 檔的每個圖元都包含一種顏色，而索引 .bmp 檔的圖元將索引保留到顏色表。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>繪製和操作形狀和圖像  
 創建物件後，可以使用物件<xref:System.Drawing.Graphics>繪製線條和形狀、渲染文本或顯示和操作圖像。 與<xref:System.Drawing.Graphics>物件一起使用的主體物件是：  
  
- 類<xref:System.Drawing.Pen>— 用於繪製線條、勾畫形狀或渲染其他幾何表示。  
  
- 類<xref:System.Drawing.Brush>— 用於填充繪圖區域，如填充形狀、圖像或文本。  
  
- 類<xref:System.Drawing.Font>— 提供渲染文本時要使用的形狀的說明。  
  
- 結構<xref:System.Drawing.Color>— 表示要顯示的不同顏色。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>使用已創建的繪圖物件  
  
- 使用上面列出的相應物件繪製所需的內容。  
  
     如需詳細資訊，請參閱下列主題：  
  
    |渲染|請參閱|  
    |---------------|---------|  
    |線條|[操作說明：在 Windows Form 上繪製線條](how-to-draw-a-line-on-a-windows-form.md)|  
    |圖形|[如何：繪製外框形狀](how-to-draw-an-outlined-shape.md)|  
    |Text|[如何：在 Windows Form 上繪製文字](how-to-draw-text-on-a-windows-form.md)|  
    |影像|[如何：使用 GDI+ 呈現影像](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>另請參閱

- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [如何：使用 GDI+ 呈現影像](how-to-render-images-with-gdi.md)
