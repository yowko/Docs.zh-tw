---
title: "如何：建立繪製的圖形物件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "GDI+, 建立影像"
  - "圖形 [Windows Form], 建立"
  - "Graphics 類別"
  - "影像 [Windows Form], 建立"
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：建立繪製的圖形物件
在可使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 來描繪線條和形狀、呈現文字或顯示和管理影像之前，您必須先建立 <xref:System.Drawing.Graphics> 物件。  <xref:System.Drawing.Graphics> 物件代表的是 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪圖介面，而且是用來建立圖形影像的物件。  
  
 使用圖形的兩個步驟如下：  
  
1.  建立 <xref:System.Drawing.Graphics> 物件。  
  
2.  使用 <xref:System.Drawing.Graphics> 物件來繪製線條和形狀、呈現文字或顯示和管理影像。  
  
## 建立圖形物件  
 您可使用下列幾種方法來建立圖形物件：  
  
#### 若要建立圖形物件  
  
-   在表單或控制項的 <xref:System.Windows.Forms.Control.Paint> 事件中，接收圖形物件的參考做為 <xref:System.Windows.Forms.PaintEventArgs> 的一部分。  這通常是當您建立控制項的描繪程式碼時，取得圖形物件參考的方式。  同樣地，您也可以在處理 <xref:System.Drawing.Printing.PrintDocument> 的 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件時，取得圖形物件做為 <xref:System.Drawing.Printing.PrintPageEventArgs> 的屬性。  
  
     \-或\-  
  
-   藉由呼叫控制項或表單的 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 方法來取得代表該控制項或表單之繪圖介面的 <xref:System.Drawing.Graphics> 物件參考。  如果您想要在現有表單或控制項上進行繪圖，請使用這個方法。  
  
     \-或\-  
  
-   從繼承自 <xref:System.Drawing.Image> 的任何物件建立 <xref:System.Drawing.Graphics> 物件。  當您要變更現有影像時，這個方法會相當有用。  
  
     下列各節將詳細說明每一個處理程序。  
  
## Paint 事件處理常式中的 PaintEventArgs  
 在為控制項的 <xref:System.Windows.Forms.PaintEventHandler> 或 <xref:System.Drawing.Printing.PrintDocument> 的 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 設計程式時，會提供圖形物件做為 <xref:System.Windows.Forms.PaintEventArgs> 或 <xref:System.Drawing.Printing.PrintPageEventArgs> 的其中一個屬性。  
  
#### 若要從 Paint 事件中的 PaintEventArgs 取得 Graphics 物件的參考  
  
1.  宣告 <xref:System.Drawing.Graphics> 物件。  
  
2.  指派變數，以參考當成 <xref:System.Windows.Forms.PaintEventArgs> 一部分傳遞的 <xref:System.Drawing.Graphics> 物件。  
  
3.  插入程式碼來繪製表單或控制項。  
  
     下列範例顯示如何參考 <xref:System.Windows.Forms.Control.Paint> 事件中來自 <xref:System.Windows.Forms.PaintEventArgs> 的 <xref:System.Drawing.Graphics> 物件：  
  
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
  
## CreateGraphics 方法  
 您也可以使用控制項或表單的 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 方法來取得代表該控制項或表單之繪圖介面的 <xref:System.Drawing.Graphics> 物件參考。  
  
#### 若要使用 CreateGraphics 方法建立 Graphics 物件  
  
-   請呼叫要呈現圖形所在表單或控制項的 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 方法。  
  
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
  
## 從 Image 物件建立  
 除此之外，您可從衍生自 <xref:System.Drawing.Image> 類別的任何物件建立圖形物件。  
  
#### 若要從 Image 建立 Graphics 物件  
  
-   請呼叫 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=fullName> 方法，提供您要建立 <xref:System.Drawing.Graphics> 物件的 Image 變數名稱。  
  
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
>  您只能從未索引的 .bmp 檔案建立 <xref:System.Drawing.Graphics> 物件，例如 16 位元、24 位元和 32 位元的 .bmp 檔。  未索引 .bmp 檔案的每個像素都只包含一種色彩，相較於已索引 .bmp 檔的像素，後者則是包含了色彩表索引。  
  
## 描繪與管理形狀和影像  
 建立 <xref:System.Drawing.Graphics> 物件之後，您可使用它來繪製線條和形狀、呈現文字或顯示和管理影像。  與 <xref:System.Drawing.Graphics> 物件搭配使用的主要物件如下：  
  
-   <xref:System.Drawing.Pen> 類別 \- 用於描繪線條、勾畫形狀或是呈現其他的幾何圖形。  
  
-   <xref:System.Drawing.Brush> 類別 \- 用於填滿圖形區域，例如實心形狀、影像或文字。  
  
-   <xref:System.Drawing.Font> 類別 \- 提供呈現文字時使用哪種形狀的描述。  
  
-   <xref:System.Drawing.Color> 結構 \- 代表要顯示的不同色彩。  
  
#### 若要使用已建立的圖形物件  
  
-   請使用列於上方的適當物件來繪製您需要的項目。  
  
     如需詳細資訊，請參閱下列主題：  
  
    |若要呈現|請參閱|  
    |----------|---------|  
    |程式行|[如何：在 Windows Form 上繪製線條](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |形狀|[如何：繪製外框形狀](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |文字|[如何：在 Windows Form 上繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |影像|[如何：使用 GDI\+ 呈現影像](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## 請參閱  
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：使用 GDI\+ 呈現影像](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)