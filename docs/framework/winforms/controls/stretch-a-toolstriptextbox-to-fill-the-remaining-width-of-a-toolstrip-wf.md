---
title: HOW TO：Toolstriptextbox 以填滿 ToolStrip (Windows Form) 的剩餘寬度
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 411c00743f0a02bdd498211d03b195aaaf023ecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612264"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>HOW TO：Toolstriptextbox 以填滿 ToolStrip (Windows Form) 的剩餘寬度
當您設定<xref:System.Windows.Forms.ToolStrip.Stretch%2A>屬性<xref:System.Windows.Forms.ToolStrip>若要控制`true`，控制項從端對端的填滿其容器和其容器調整大小時，會調整大小。 在此組態中，您可能會發現它可在控制項中，延伸項目，例如<xref:System.Windows.Forms.ToolStripTextBox>、 填滿可用空間及調整大小的控制項調整大小時。 自動縮放非常有用，例如，如果您想要達到外觀和行為類似於 Microsoft® Internet Explorer 中的 [網址] 列。  
  
## <a name="example"></a>範例  
 下列程式碼範例提供一個衍生自類別<xref:System.Windows.Forms.ToolStripTextBox>稱為`ToolStripSpringTextBox`。 此類別會覆寫<xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>方法，以計算可用寬度的父代<xref:System.Windows.Forms.ToolStrip>之後的所有其他項目結合的寬度減去控制。 此程式碼範例也會提供<xref:System.Windows.Forms.Form>類別和`Program`類別示範新的行為。  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [如何：在 StatusStrip 中以互動方式使用 Spring 屬性](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
