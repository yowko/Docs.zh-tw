---
title: HOW TO：(Visual Studio) 的圖形間啟用定位處理
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: c47d94317008af57907b747e53bd13ae7ca229f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498277"
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>HOW TO：(Visual Studio) 的圖形間啟用定位處理
Line 與 shape 控制項沒有`TabStop`或`TabIndex`屬性，但您仍然可以啟用定位停駐點在它們之間。 在下列範例中，按下 ctrl 鍵和 TAB 鍵將 索引標籤之間圖形;按下 TAB 鍵按鈕之間將索引標籤上。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="to-enable-tabbing-among-shapes"></a>若要啟用定位停駐點之間的圖形  
  
1.  將三個<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>控制項和兩個<xref:System.Windows.Forms.Button>控制從**工具箱**至表單。  
  
2.  在 **程式碼編輯器**，新增`Imports`或`using`頂端的模組的陳述式：  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  在事件程序中新增下列程式碼：  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  新增下列程式碼中的`Button1_PreviewKeyDown`事件程序：  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>另請參閱
- [如何：使用 OvalShape 和 RectangleShape 控制項繪製圖案](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [如何：使用 LineShape 控制項繪製線條](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [Line 和 Shape 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
