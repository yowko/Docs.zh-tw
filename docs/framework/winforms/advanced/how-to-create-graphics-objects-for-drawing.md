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
# <a name="how-to-create-graphics-objects-for-drawing"></a>HOW TO：建立繪製的圖形物件
您必須先建立<xref:System.Drawing.Graphics>物件, 才可以繪製線條和圖形、呈現文字, 或使用 gdi + 來顯示及操作影像。 <xref:System.Drawing.Graphics>物件代表 gdi + 繪圖介面, 而則是用來建立圖形影像的物件。  
  
 使用圖形的步驟有兩個:  
  
1. <xref:System.Drawing.Graphics>建立物件。  
  
2. <xref:System.Drawing.Graphics>使用物件繪製線條和圖形、呈現文字, 或顯示和操作影像。  
  
## <a name="creating-a-graphics-object"></a>建立繪圖物件  
 繪圖物件可以用各種方式建立。  
  
#### <a name="to-create-a-graphics-object"></a>若要建立繪圖物件  
  
- 在表單或控制項的事件中,接收繪圖物件的參考做為的一部分。<xref:System.Windows.Forms.Control.Paint> <xref:System.Windows.Forms.PaintEventArgs> 這通常是您在建立控制項的繪製程式碼時, 取得繪圖物件參考的方式。 同樣地, 您也可以在<xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage>處理的事件<xref:System.Drawing.Printing.PrintDocument>時, 取得繪圖物件做為的屬性。  
  
     -或-  
  
- 呼叫控制項或表單的<xref:System.Drawing.Graphics> 方法,取得代表該控制項或表單之繪圖介面的物件參考。<xref:System.Windows.Forms.Control.CreateGraphics%2A> 如果您想要在已經存在的表單或控制項上進行繪製, 請使用這個方法。  
  
     -或-  
  
- 從繼承自<xref:System.Drawing.Image>的任何物件建立物件。<xref:System.Drawing.Graphics> 當您想要改變已經存在的映射時, 這個方法很有用。  
  
     下列各節提供有關每個處理常式的詳細資料。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>繪製事件處理常式中的 PaintEventArgs  
 <xref:System.Windows.Forms.PaintEventHandler>針對控制項<xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>或<xref:System.Drawing.Printing.PrintDocument.PrintPage> 的進行程式設計時,會將繪圖物件當做或的其中一個<xref:System.Drawing.Printing.PrintDocument>屬性來提供。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>從繪製事件中的 PaintEventArgs 取得繪圖物件的參考  
  
1. <xref:System.Drawing.Graphics>宣告物件。  
  
2. 指派變數來參考<xref:System.Drawing.Graphics>當做一部分<xref:System.Windows.Forms.PaintEventArgs>傳遞的物件。  
  
3. 插入程式碼以繪製表單或控制項。  
  
     下列範例顯示如何從<xref:System.Drawing.Graphics> <xref:System.Windows.Forms.Control.Paint>事件的<xref:System.Windows.Forms.PaintEventArgs>中參考物件:  
  
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
 您也可以使用<xref:System.Windows.Forms.Control.CreateGraphics%2A>控制項或表單的方法, 取得代表該控制項或表單之繪圖介面的<xref:System.Drawing.Graphics>物件參考。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>若要使用 CreateGraphics 方法建立繪圖物件  
  
- 呼叫您要呈現圖形的表單或控制項的方法。<xref:System.Windows.Forms.Control.CreateGraphics%2A>  
  
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
 此外, 您可以從衍生自<xref:System.Drawing.Image>類別的任何物件建立繪圖物件。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>若要從影像建立繪圖物件  
  
- 呼叫方法, 並提供您想要從中<xref:System.Drawing.Graphics>建立物件之映射變數的名稱。 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>  
  
     下列範例顯示如何使用<xref:System.Drawing.Bitmap>物件:  
  
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
> 您只能從非<xref:System.Drawing.Graphics>索引的 .bmp 檔案 (例如, 16 位、24位和32位的 .bmp 檔案) 建立物件。 非索引 .bmp 檔案的每個圖元都有一個色彩, 相對於已編制索引之 .bmp 檔案的圖元, 這些檔案會保存色彩表的索引。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>繪製和操作圖形和影像  
 建立之後, <xref:System.Drawing.Graphics>物件可以用來繪製線條和圖形、呈現文字, 或顯示和操作影像。 與<xref:System.Drawing.Graphics>物件搭配使用的主要物件為:  
  
- <xref:System.Drawing.Pen>類別: 用於繪製線條、大綱圖形或轉譯其他幾何標記法。  
  
- <xref:System.Drawing.Brush>類別: 用來填滿圖形的區域, 例如填滿的圖形、影像或文字。  
  
- <xref:System.Drawing.Font>類別: 提供呈現文字時所要使用之圖形的描述。  
  
- <xref:System.Drawing.Color>結構: 代表要顯示的不同色彩。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>若要使用您所建立的繪圖物件  
  
- 使用上方所列的適當物件來繪製您所需的內容。  
  
     如需詳細資訊，請參閱下列主題：  
  
    |呈現|請參閱|  
    |---------------|---------|  
    |線條|[如何：在 Windows Form 上繪製線條](how-to-draw-a-line-on-a-windows-form.md)|  
    |圖形|[如何：繪製外框形狀](how-to-draw-an-outlined-shape.md)|  
    |文字|[如何：在 Windows Form 上繪製文字](how-to-draw-text-on-a-windows-form.md)|  
    |影像|[如何：使用 GDI + 呈現影像](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>另請參閱

- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [如何：使用 GDI + 呈現影像](how-to-render-images-with-gdi.md)
