---
title: "如何：建立繪製的圖形物件"
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
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4b626d3d87c6537b74b6d28e086303474ea2c3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>如何：建立繪製的圖形物件
您可以繪製線條或圖形之前，呈現文字，或顯示和操作的影像[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您必須建立<xref:System.Drawing.Graphics>物件。 <xref:System.Drawing.Graphics>物件代表[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪圖介面，而是用來建立圖形化的映像的物件。  
  
 使用圖形有兩個步驟：  
  
1.  建立<xref:System.Drawing.Graphics>物件。  
  
2.  使用<xref:System.Drawing.Graphics>繪製線條和形狀、 呈現文字，或顯示和管理映像的物件。  
  
## <a name="creating-a-graphics-object"></a>建立圖形物件  
 圖形物件可以建立各種不同的方式。  
  
#### <a name="to-create-a-graphics-object"></a>若要建立圖形物件  
  
-   接收圖形物件的參考做為一部分<xref:System.Windows.Forms.PaintEventArgs>中<xref:System.Windows.Forms.Control.Paint>表單或控制項的事件。 這通常是取得圖形物件的參考，當建立控制項的繪製程式碼。 您也可以做的屬性取得圖形物件的同樣地，<xref:System.Drawing.Printing.PrintPageEventArgs>時處理<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件<xref:System.Drawing.Printing.PrintDocument>。  
  
     -或-  
  
-   呼叫<xref:System.Windows.Forms.Control.CreateGraphics%2A>控制項或表單，以取得參考的方法<xref:System.Drawing.Graphics>代表該控制項或表單的繪圖介面的物件。 如果您想要在表單或已經存在的控制項中繪製，請使用這個方法。  
  
     -或-  
  
-   建立<xref:System.Drawing.Graphics>物件繼承自任何物件從<xref:System.Drawing.Image>。 當您想要變更現有的映像時，這個方法很有用。  
  
     下列各節提供有關每一個程序的詳細資料。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>[小畫家] 的事件處理常式的 PaintEventArgs  
 程式設計時<xref:System.Windows.Forms.PaintEventHandler>控制項或<xref:System.Drawing.Printing.PrintDocument.PrintPage>如<xref:System.Drawing.Printing.PrintDocument>，做為其中一個屬性提供的圖形物件<xref:System.Windows.Forms.PaintEventArgs>或<xref:System.Drawing.Printing.PrintPageEventArgs>。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>若要取得的繪製事件中 PaintEventArgs 圖形物件的參考  
  
1.  宣告<xref:System.Drawing.Graphics>物件。  
  
2.  將參考變數指派<xref:System.Drawing.Graphics>物件的一部分傳送<xref:System.Windows.Forms.PaintEventArgs>。  
  
3.  插入程式碼以繪製的表單或控制項。  
  
     下列範例示範如何參考<xref:System.Drawing.Graphics>物件從<xref:System.Windows.Forms.PaintEventArgs>中<xref:System.Windows.Forms.Control.Paint>事件：  
  
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
  
## <a name="creategraphics-method"></a>包含 CreateGraphics 方法  
 您也可以使用<xref:System.Windows.Forms.Control.CreateGraphics%2A>控制項或表單，以取得參考的方法<xref:System.Drawing.Graphics>代表該控制項或表單的繪圖介面的物件。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>若要建立具有包含 CreateGraphics 方法的圖形物件  
  
-   呼叫<xref:System.Windows.Forms.Control.CreateGraphics%2A>賴以您想要呈現圖形的表單或控制項的方法。  
  
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
  
## <a name="create-from-an-image-object"></a>從映像物件建立  
 此外，您可以建立衍生自所有物件的圖形物件<xref:System.Drawing.Image>類別。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>若要從映像建立圖形物件  
  
-   呼叫<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>方法，並提供您想要建立的映像變數的名稱<xref:System.Drawing.Graphics>物件。  
  
     下列範例示範如何使用<xref:System.Drawing.Bitmap>物件：  
  
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
>  您只能建立<xref:System.Drawing.Graphics>從非索引.bmp 檔案，例如 16 位元、 24 位元和 32 位元之.bmp 檔案的物件。 非索引.bmp 檔案的每個像素包含一種色彩，相較於像素的色彩表中儲存索引的索引的.bmp 檔案。  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>繪圖和操作圖案和影像  
 它建立之後，<xref:System.Drawing.Graphics>物件可能會用來繪製線條和形狀、 呈現文字，或顯示和操作影像。 搭配使用的主體物件<xref:System.Drawing.Graphics>物件：  
  
-   <xref:System.Drawing.Pen>類別，用於繪製線條、 大綱圖形，或呈現其他幾何表示相互轉換。  
  
-   <xref:System.Drawing.Brush>類別，用於填滿圖形，例如填滿的圖案、 影像或文字的區域。  
  
-   <xref:System.Drawing.Font>類別，提供什麼圖形轉譯文字時所要使用的描述。  
  
-   <xref:System.Drawing.Color>結構，代表要顯示不同的色彩。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>若要使用您已建立的圖形物件  
  
-   使用適當的物件上面所列繪製您的需要。  
  
     如需詳細資訊，請參閱下列主題：  
  
    |要呈現|請參閱|  
    |---------------|---------|  
    |線條|[操作說明：在 Windows Form 上繪製線條](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |圖形|[操作說明：繪製外框形狀](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |Text|[操作說明：在 Windows Forms 上繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |影像|[操作說明：使用 GDI+ 呈現影像](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>請參閱  
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [操作說明：使用 GDI+ 呈現影像](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
