---
title: "How to: Enable Tabbing Between Shapes (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Line control, implementing tabbing"
  - "Shape control, implementing tabbing"
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Enable Tabbing Between Shapes (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Line 和 Shape 控制項沒有 `TabStop` 或 `TabIndex` 屬性，但您仍然可以為兩者啟用定位停駐。  在下列範例中，同時按下 CTRL 和 TAB 鍵會在形狀間定位停駐，而只按下 TAB 鍵則會在按鈕間定位停駐。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在形狀間啟用定位停駐  
  
1.  從 \[**工具箱**\] 將三個 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> 控制項和兩個 <xref:System.Windows.Forms.Button> 控制項拖曳到表單上。  
  
2.  在 \[**程式碼編輯器**\] 中，將 `Imports` 或 `using` 陳述式加入至模組的最上方：  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
3.  在事件程序中，加入下列程式碼：  
  
     [!CODE [VbPowerPacksTabbing#1](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksTabbing#1)]  
  
4.  在 `Button1_PreviewKeyDown` 事件程序中，加入下列程式碼：  
  
     [!CODE [VbPowerPacksTabbing#2](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksTabbing#2)]  
  
## 請參閱  
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)