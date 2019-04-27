---
title: HOW TO：提供控制項的工具箱點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 7c26e00acd4278ced53ad29c748ac076e0215a23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913207"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>HOW TO：提供控制項的工具箱點陣圖
如果您想要有特殊的圖示，為您的控制項就會出現在**工具箱**，您可以使用，以便指定特定的映像<xref:System.Drawing.ToolboxBitmapAttribute>。 此類別是一個「屬性」，一種您可以附加至其他類別的特殊類別。 如需有關屬性的詳細資訊，請參閱 <<c0> [ 屬性概觀 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)適用於 Visual Basic 或[屬性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)適用於 C#。  
  
 使用<xref:System.Drawing.ToolboxBitmapAttribute>，您可以指定字串，表示 16 x 16 像素點陣圖的路徑和檔案名稱。 將此點陣圖新增至 [工具箱]，它會接著出現在您的控制項旁邊。 您也可以指定<xref:System.Type>，在此情況下載入與該型別相關聯的點陣圖。 如果您同時指定<xref:System.Type>字串，控制項的影像資源以搜尋中包含所指定之類型的組件的字串參數所指定的名稱和<xref:System.Type>參數。  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>指定控制項的工具箱點陣圖  
  
1. 新增<xref:System.Drawing.ToolboxBitmapAttribute>至您的控制項之前的類別宣告`Class`visual basic 和上述類別宣告中的 Visual C# 中的關鍵字。  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2. 重建專案。  
  
    > [!NOTE]
    >  點陣圖並不會針對自動產生的控制項和元件出現在工具箱中。 若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。 如需詳細資訊，請參閱[逐步解說：自動將 [工具箱] 中的以自訂元件填入](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [逐步解說：自動填入 [工具箱] 中的以自訂元件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [屬性概觀 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [屬性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
