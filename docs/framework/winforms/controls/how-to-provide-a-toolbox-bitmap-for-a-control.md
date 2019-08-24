---
title: 作法：提供控制項的工具箱點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e6da7318ba481af721a9220c8f71af2a18e764a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015781"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>作法：提供控制項的工具箱點陣圖

如果您想要讓控制項的特殊圖示出現在 Visual Studio 的 [**工具箱**] 中, 您可以使用<xref:System.Drawing.ToolboxBitmapAttribute>來指定特定的影像。 此類別是一個「屬性」，一種您可以附加至其他類別的特殊類別。 如需屬性的詳細資訊, 請參閱的C#Visual Basic 或[屬性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)的[屬性總覽 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) 。

<xref:System.Drawing.ToolboxBitmapAttribute>使用, 您可以指定字串, 指出 16 x 16 圖元點陣圖的路徑和檔案名。 將此點陣圖新增至 [工具箱]，它會接著出現在您的控制項旁邊。 您也可以指定<xref:System.Type>, 在此情況下, 會載入與該類型相關聯的點陣圖。 如果您同時<xref:System.Type>指定和字串, 控制項會在包含<xref:System.Type>參數所指定之類型的元件中, 搜尋具有 string 參數所指定之名稱的影像資源。

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>指定控制項的工具箱點陣圖

1. 在 visual Basic 的`Class`關鍵字之前以及 visual C#的類別宣告上方, 將加入至控制項的類別宣告。<xref:System.Drawing.ToolboxBitmapAttribute>

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
    > 點陣圖並不會針對自動產生的控制項和元件出現在工具箱中。 若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。 如需詳細資訊，請參閱[逐步解說：自動將自訂群組件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)填入工具箱。

## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [逐步解說：使用自訂群組件自動填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [屬性概觀 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [屬性 (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
