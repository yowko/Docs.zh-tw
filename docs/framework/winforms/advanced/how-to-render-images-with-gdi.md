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
# <a name="how-to-render-images-with-gdi"></a>如何：使用 GDI+ 呈現影像
您可以使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 來呈現應用程式中以檔案形式存在的影像。 您可以建立新物件的<xref:System.Drawing.Image>類別 (例如<xref:System.Drawing.Bitmap>)、 建立<xref:System.Drawing.Graphics>物件，代表您要使用的繪圖介面，並呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。 影像將繪製於此圖形類別所代表的繪圖介面上。 您可以在設計階段使用影像編輯器來建立及編輯影像檔案，而在執行階段使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 來呈現它們。 如需詳細資訊，請參閱[圖示的影像編輯器](/cpp/windows/image-editor-for-icons)。  
  
### <a name="to-render-an-image-with-gdi"></a>使用 GDI+ 呈現影像  
  
1.  建立物件，代表您想要顯示的影像。 這個物件必須繼承自一個類別的成員<xref:System.Drawing.Image>，例如<xref:System.Drawing.Bitmap>或<xref:System.Drawing.Imaging.Metafile>。 範例如下︰  
  
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
  
2.  建立<xref:System.Drawing.Graphics>代表您想要使用的繪圖介面的物件。 如需詳細資訊，請參閱[如何：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。  
  
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
  
3.  呼叫<xref:System.Drawing.Graphics.DrawImage%2A>的圖形物件呈現影像。 您必須指定要繪製的影像，以及其繪製所在的座標。  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [GDI+ 中的畫筆、線條和矩形](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [操作說明：在 Windows Forms 上繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [繪製線條或封閉的圖形](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [圖示影像編輯器](/cpp/windows/image-editor-for-icons)
