---
title: "如何：為控制項提供工具箱點陣圖 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "點陣圖 [Windows Form], 自訂控制項"
  - "自訂控制項 [Windows Form], 工具箱點陣圖"
  - "工具箱 [Windows Form], 加入自訂控制項的點陣圖"
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 如何：為控制項提供工具箱點陣圖
如果想讓控制項的特殊圖示出現在 \[**工具箱**\] 中，您可使用 <xref:System.Drawing.ToolboxBitmapAttribute> 指定特定的影像。  這個類別是一種*屬性* \(Attribute\)，是可以附加到其他類別的特殊類別。  如需屬性的詳細資訊，請參閱 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 的 [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/zh-tw/0d0cff64-892d-4f57-83bd-bef388553d4f)和 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的[屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 您可使用 <xref:System.Drawing.ToolboxBitmapAttribute> 來指定字串，此字串表示 16 x 16 像素點陣圖的路徑和檔名。  將控制項加入 \[**工具箱**\] 時，這個點陣圖就會出現在控制項旁。  您也可以指定 <xref:System.Type>，而在這種情況下就會載入與該型別關聯的點陣圖。  如果同時指定了 <xref:System.Type> 和字串，控制項就會搜尋名稱是由組件中的字串參數所指定的影像資源，此組件包含 <xref:System.Type> 參數指定的型別。  
  
### 若要為您的控制項指定工具箱點陣圖  
  
1.  在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 的 `Class` 關鍵字之前，以及在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的類別宣告 \(Class Declaration\) 上方，將 <xref:System.Drawing.ToolboxBitmapAttribute> 加入至控制項的類別宣告。  
  
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
    >  \[工具箱\] 中沒有出現用來自動產生控制項和元件的點陣圖。  若要看到點陣圖，請使用 \[**選擇工具箱項目**\] 對話方塊重新載入該控制項。  如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
## 請參閱  
 <xref:System.Drawing.ToolboxBitmapAttribute>   
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)   
 [在設計階段開發 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Attributes](../Topic/Attributes%20\(Visual%20Basic\)1.md)   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)