---
title: 如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: bd58cbd109b8e3dd04c6a284dc6926e95830fb61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537716"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form)
當您將<xref:System.Windows.Forms.ToolStrip.Stretch%2A>屬性<xref:System.Windows.Forms.ToolStrip>控制權傳輸至`true`，控制項從端對端，填滿其容器和其容器調整大小時，調整大小時。 在此組態中，您可能會發現這類延伸項目在控制項中， <xref:System.Windows.Forms.ToolStripTextBox>、 填滿可用空間和調整大小的控制項重新調整大小時。 延伸而非常有用，例如，如果您想要達到的外觀和行為類似於 Microsoft® Internet Explorer 中的網址列。  
  
## <a name="example"></a>範例  
 下列程式碼範例提供一個衍生自類別<xref:System.Windows.Forms.ToolStripTextBox>呼叫`ToolStripSpringTextBox`。 這個類別會覆寫<xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>方法來計算可用寬度的父代<xref:System.Windows.Forms.ToolStrip>控制項之後已經減去的其他所有項目結合的寬度。 這個程式碼範例也會提供<xref:System.Windows.Forms.Form>類別和`Program`類別來示範新的行為。  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [操作說明：在 StatusStrip 中以互動方式使用 Spring 屬性](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
