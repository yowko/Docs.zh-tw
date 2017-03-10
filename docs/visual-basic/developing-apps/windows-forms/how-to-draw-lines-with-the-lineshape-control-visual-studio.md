---
title: "How to: Draw Lines with the LineShape Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LineShape control"
  - "lines, drawing"
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Draw Lines with the LineShape Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在設計階段和執行階段，您都可以使用 <xref:Microsoft.VisualBasic.PowerPacks.LineShape> 控制項在表單或容器 \(Container\) 上繪製水平線、垂直線或對角線。  
  
 **注意**：在下列指示中，某些 Visual Studio 使用者介面項目的名稱和位置可能會與您電腦所顯示的有所不同。  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段繪製線條  
  
1.  從 \[**工具箱**\] 的 \[**Visual Basic PowerPacks**\] 索引標籤中，將 <xref:Microsoft.VisualBasic.PowerPacks.LineShape> 控制項拖曳到表單或容器控制項。  
  
2.  拖曳縮放控點 \(Sizing Handle\) 並移動控制軸，以調整線條的大小和位置。  
  
     您也可以在 \[**屬性**\] 視窗中變更 `X1`、`X2`、`Y1` 和 `Y2` 屬性，以調整線條的大小和位置。  
  
3.  在 \[**屬性**\] 視窗中，選擇性地設定其他屬性 \(例如 `BorderStyle` 或 `BorderColor`\) 來變更線條的外觀。  
  
### 若要在執行階段繪製線條  
  
1.  在 \[**專案**\] 功能表上，按一下 \[**加入參考**\]。  
  
2.  在 \[**加入參考**\] 對話方塊中，選取 \[**Microsoft.VisualBasic.PowerPacks.VS**\]，然後按一下 \[**確定**\]。  
  
3.  在 \[**程式碼編輯器**\] 中，將 `Imports` 或 `using` 陳述式 \(Statement\) 加入至模組的最上方：  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  在 `Event` 程序中，加入下列程式碼：  
  
     [!code-cs[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerpacksLineCS/VbPowerpacksLine.cs#1)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerpacksLine/VBPowerpacksLine.vb#1)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)