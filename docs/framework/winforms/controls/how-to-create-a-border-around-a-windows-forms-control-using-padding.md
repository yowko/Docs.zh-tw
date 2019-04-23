---
title: HOW TO：使用邊框間距在 Windows Forms 控制項周圍建立框線
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
ms.openlocfilehash: e3bbf43dbe45e675df172a6c3e1db16a3ba9caa8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124018"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>HOW TO：使用邊框間距在 Windows Forms 控制項周圍建立框線
下列程式碼範例示範如何建立框線或外框<xref:System.Windows.Forms.RichTextBox>控制項。 範例設定的值<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Padding>屬性設為 5 並設定<xref:System.Windows.Forms.Control.Dock%2A>屬性的子系<xref:System.Windows.Forms.RichTextBox>若要控制<xref:System.Windows.Forms.DockStyle.Fill>。 <xref:System.Windows.Forms.Control.BackColor%2A>的<xref:System.Windows.Forms.Panel>控制設為<xref:System.Drawing.Color.Blue%2A>，這會建立藍色框線<xref:System.Windows.Forms.RichTextBox>控制項。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Padding>
- [Windows Forms 控制項的邊界和邊框距離](margin-and-padding-in-windows-forms-controls.md)
