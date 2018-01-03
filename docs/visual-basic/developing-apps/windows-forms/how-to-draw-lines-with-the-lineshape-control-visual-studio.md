---
title: "如何：使用 LineShape 控制項繪製線條 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42e7f01a57a514ad1dc64e3d4451ce38ea199f93
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>如何：使用 LineShape 控制項繪製線條 (Visual Studio)
您可以使用<xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項在表單或容器上繪製水平、 垂直或對角線，在設計階段和執行階段。  
  
 **請注意**您的電腦可能會顯示不同的名稱或位置的某些 Visual Studio 使用者介面項目中的下列指示。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-draw-a-line-at-design-time"></a>在設計階段繪製線條  
  
1.  拖曳<xref:Microsoft.VisualBasic.PowerPacks.LineShape>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**拖曳到表單或容器控制項。  
  
2.  拖曳調整大小並移動控點大小和位置的行。  
  
     您可以調整大小，並藉由變更調整線條`X1`， `X2`， `Y1`，和`Y2`中的屬性**屬性**視窗。  
  
3.  在**屬性**視窗中，選擇性地設定其他屬性如`BorderStyle`或`BorderColor`若要變更線條的外觀。  
  
### <a name="to-draw-a-line-at-run-time"></a>若要在執行階段繪製一條線  
  
1.  在 [專案] 功能表上，按一下 [新增參考]。  
  
2.  在**加入參考**對話方塊中，選取**Microsoft.VisualBasic.PowerPacks.VS**，然後按一下 **確定**。  
  
3.  在**程式碼編輯器**，新增`Imports`或`using`陳述式之模組的頂端：  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  在 `Event` 程序中加入下列程式碼：  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [Line 和 Shape 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [操作說明：使用 OvalShape 和 RectangleShape 控制項繪製圖案](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
