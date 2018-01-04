---
title: "如何：為控制項提供工具箱點陣圖"
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
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 947ac4f8783b388135cf9e8147bb48eda93cfa08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>如何：為控制項提供工具箱點陣圖
如果您想要有特殊的圖示，為您的控制項出現在**工具箱**，您可以指定特定的映像使用<xref:System.Drawing.ToolboxBitmapAttribute>。 此類別是一個「屬性」，一種您可以附加至其他類別的特殊類別。 如需屬性的詳細資訊，請參閱[不在組建中︰Visual Basic 中的屬性概觀](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) (適用於 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) 和[屬性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) (適用於 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)])。  
  
 使用<xref:System.Drawing.ToolboxBitmapAttribute>，您可以指定表示 16 x 16 像素點陣圖的路徑和檔案名稱的字串。 將此點陣圖新增至 [工具箱]，它會接著出現在您的控制項旁邊。 您也可以指定<xref:System.Type>，在此情況下會載入與這個類型相關聯的點陣圖。 如果您同時指定<xref:System.Type>和字串，控制項搜尋影像資源字串中的參數包含所指定之類型的組件所指定的名稱與<xref:System.Type>參數。  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>指定控制項的工具箱點陣圖  
  
1.  新增<xref:System.Drawing.ToolboxBitmapAttribute>至類別宣告之前控制項的`Class`關鍵字[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]，和更高版本的類別宣告[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]。  
  
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
  
2.  重建專案。  
  
    > [!NOTE]
    >  點陣圖並不會針對自動產生的控制項和元件出現在工具箱中。 若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。 如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [在設計階段開發 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [屬性 (Visual Basic)](~/docs/visual-basic/language-reference/attributes.md)  
 [屬性](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
