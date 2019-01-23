---
title: HOW TO：Windows Form 周圍建立框線控制使用的填補
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: 26d5dd086828df94c1ea0808d2f72723344b0702
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614650"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>HOW TO：Windows Form 周圍建立框線控制使用的填補
下列程式碼範例示範如何建立框線或外框<xref:System.Windows.Forms.RichTextBox>控制項。 範例設定的值<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Padding>屬性設為 5 並設定<xref:System.Windows.Forms.Control.Dock%2A>屬性的子系<xref:System.Windows.Forms.RichTextBox>若要控制<xref:System.Windows.Forms.DockStyle.Fill>。 <xref:System.Windows.Forms.Control.BackColor%2A>的<xref:System.Windows.Forms.Panel>控制設為<xref:System.Drawing.Color.Blue%2A>，這會建立藍色框線<xref:System.Windows.Forms.RichTextBox>控制項。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Padding>
- [Windows Forms 控制項的邊界和邊框距離](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
