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
# <a name="how-to-create-graphics-objects-for-drawing"></a>如何：建立繪製的圖形物件
您必須先建立物件，才可以繪製線條和圖形、呈現文字，或使用 GDI + 來顯示及操作影像 <xref:System.Drawing.Graphics> 。 <xref:System.Drawing.Graphics>物件代表 GDI + 繪圖介面，而則是用來建立圖形影像的物件。  
  
 使用圖形的步驟有兩個：  
  
1. 建立 <xref:System.Drawing.Graphics> 物件。  
  
2. 使用 <xref:System.Drawing.Graphics> 物件繪製線條和圖形、呈現文字，或顯示和操作影像。  
  
## <a name="creating-a-graphics-object"></a>建立繪圖物件  
 繪圖物件可以用各種方式建立。  
  
#### <a name="to-create-a-graphics-object"></a>若要建立繪圖物件  
  
- <xref:System.Windows.Forms.PaintEventArgs>在 <xref:System.Windows.Forms.Control.Paint> 表單或控制項的事件中，接收繪圖物件的參考做為的一部分。 這通常是您在建立控制項的繪製程式碼時，取得繪圖物件參考的方式。 同樣地，您也可以在處理的事件時，取得繪圖物件做為的屬性 <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> 。  
  
     -或-  
  
- 呼叫 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控制項或表單的方法，取得 <xref:System.Drawing.Graphics> 代表該控制項或表單之繪圖介面的物件參考。 如果您想要在已經存在的表單或控制項上進行繪製，請使用這個方法。  
  
     -或-  
  
- <xref:System.Drawing.Graphics>從繼承自的任何物件建立物件 <xref:System.Drawing.Image> 。 當您想要改變已經存在的映射時，這個方法很有用。  
  
     下列各節提供有關每個處理常式的詳細資料。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>繪製事件處理常式中的 PaintEventArgs  
 針對控制項或的進行程式設計時 <xref:System.Windows.Forms.PaintEventHandler> <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> ，會將繪圖物件當做或的其中一個屬性來提供 <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs> 。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>從繪製事件中的 PaintEventArgs 取得繪圖物件的參考  
  
1. 宣告 <xref:System.Drawing.Graphics> 物件。  
  
2. 指派變數來參考當做 <xref:System.Drawing.Graphics> 一部分傳遞的物件 <xref:System.Windows.Forms.PaintEventArgs> 。  
  
3. 插入程式碼以繪製表單或控制項。  
  
     下列範例顯示如何 <xref:System.Drawing.Graphics> 從事件的中參考物件 <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> ：  
  
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
  
## <a name="creategraphics-method"></a>CreateGraphics 方法  
 您也可以使用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控制項或表單的方法，取得 <xref:System.Drawing.Graphics> 代表該控制項或表單之繪圖介面的物件參考。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>若要使用 CreateGraphics 方法建立繪圖物件  
  
- 呼叫 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 您要呈現圖形的表單或控制項的方法。  
  
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
  
## <a name="create-from-an-image-object"></a>從 Image 物件建立  
 此外，您可以從衍生自類別的任何物件建立繪圖物件 <xref:System.Drawing.Image> 。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>若要從影像建立繪圖物件  
  
- 呼叫 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> 方法，並提供您想要從中建立物件之映射變數的名稱 <xref:System.Drawing.Graphics> 。  
  
     下列範例顯示如何使用 <xref:System.Drawing.Bitmap> 物件：  
  
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
> 您只能從非 <xref:System.Drawing.Graphics> 索引的 .bmp 檔案（例如，16位、24位和32位的 .bmp 檔案）建立物件。 非索引 .bmp 檔案的每個圖元都有一個色彩，相對於已編制索引之 .bmp 檔案的圖元，這些檔案會保存色彩表的索引。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>繪製和操作圖形和影像  
 建立之後， <xref:System.Drawing.Graphics> 物件可以用來繪製線條和圖形、呈現文字，或顯示和操作影像。 與物件搭配使用的主要物件 <xref:System.Drawing.Graphics> 為：  
  
- <xref:System.Drawing.Pen>類別：用於繪製線條、大綱圖形或轉譯其他幾何標記法。  
  
- <xref:System.Drawing.Brush>類別：用來填滿圖形的區域，例如填滿的圖形、影像或文字。  
  
- <xref:System.Drawing.Font>類別：提供呈現文字時所要使用之圖形的描述。  
  
- <xref:System.Drawing.Color>結構：代表要顯示的不同色彩。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>若要使用您所建立的繪圖物件  
  
- 使用上方所列的適當物件來繪製您所需的內容。  
  
     如需詳細資訊，請參閱下列主題：  
  
    |呈現|請參閱|  
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
