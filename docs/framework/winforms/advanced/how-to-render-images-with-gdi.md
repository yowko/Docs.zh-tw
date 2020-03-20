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
# <a name="how-to-render-images-with-gdi"></a>如何：使用 GDI+ 呈現影像
您可以使用 GDI+ 來渲染應用程式中作為檔存在的圖像。 為此，<xref:System.Drawing.Image>方法是創建類的新物件（如<xref:System.Drawing.Bitmap>），創建引用要使用的繪圖表面<xref:System.Drawing.Graphics>的物件，並調用<xref:System.Drawing.Graphics.DrawImage%2A><xref:System.Drawing.Graphics>物件的方法。 影像將繪製於此圖形類別所代表的繪圖介面上。 您可以使用影像編輯器在設計時創建和編輯影像檔，並在運行時使用 GDI+ 呈現它們。 如需詳細資訊，請參閱[圖示的影像編輯器](/cpp/windows/image-editor-for-icons)。  
  
### <a name="to-render-an-image-with-gdi"></a>使用 GDI+ 呈現影像  
  
1. 建立物件，代表您想要顯示的影像。 此物件必須是從 繼承的<xref:System.Drawing.Image>類的成員，<xref:System.Drawing.Bitmap>如 。 <xref:System.Drawing.Imaging.Metafile> 範例如下︰  
  
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
  
2. 創建<xref:System.Drawing.Graphics>表示要使用的繪圖曲面的物件。 如需詳細資訊，請參閱[如何：建立繪圖的圖形物件](how-to-create-graphics-objects-for-drawing.md)。  
  
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
  
3. <xref:System.Drawing.Graphics.DrawImage%2A>調用繪圖物件以渲染圖像。 您必須指定要繪製的影像，以及其繪製所在的座標。  
  
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

- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [如何：建立繪製的圖形物件](how-to-create-graphics-objects-for-drawing.md)
- [GDI+ 中的畫筆、線條和矩形](pens-lines-and-rectangles-in-gdi.md)
- [如何：在 Windows Form 上繪製文字](how-to-draw-text-on-a-windows-form.md)
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [繪製線條或封閉圖形](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [圖示影像編輯器](/cpp/windows/image-editor-for-icons)
