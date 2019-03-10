---
title: HOW TO：呈現視覺化樣式項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 33c73bf8faa9dfafe5f4889875887dc3aef5985c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714108"
---
# <a name="how-to-render-a-visual-style-element"></a>HOW TO：呈現視覺化樣式項目
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空間會公開<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>物件表示 Windows 使用者介面 (UI) 項目支援視覺化樣式。 本主題示範如何使用<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>類別呈現<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>表示**登出**並**關機**的 [開始] 功能表的按鈕。  
  
### <a name="to-render-a-visual-style-element"></a>要呈現視覺化樣式項目  
  
1.  建立<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>並將它設定為您想要繪製的項目。 請注意，使用<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType>屬性和<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType>方法，而<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A>建構函式會擲回例外狀況，如果停用了視覺化樣式，或未定義的項目。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  呼叫<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A>方法來呈現項目<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>目前呈現。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   自訂控制項衍生自<xref:System.Windows.Forms.Control>類別。  
  
-   A<xref:System.Windows.Forms.Form>會裝載自訂的控制項。  
  
-   若要參考<xref:System?displayProperty=nameWithType>， <xref:System.Drawing?displayProperty=nameWithType>， <xref:System.Windows.Forms?displayProperty=nameWithType>，和<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>命名空間。  
  
## <a name="see-also"></a>另請參閱
- [使用視覺化樣式呈現控制項](rendering-controls-with-visual-styles.md)
