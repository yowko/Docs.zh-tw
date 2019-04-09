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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124018"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a><span data-ttu-id="48c2d-102">HOW TO：使用邊框間距在 Windows Forms 控制項周圍建立框線</span><span class="sxs-lookup"><span data-stu-id="48c2d-102">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>
<span data-ttu-id="48c2d-103">下列程式碼範例示範如何建立框線或外框<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="48c2d-103">The following code example demonstrates how to create a border or outline around a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="48c2d-104">範例設定的值<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Padding>屬性設為 5 並設定<xref:System.Windows.Forms.Control.Dock%2A>屬性的子系<xref:System.Windows.Forms.RichTextBox>若要控制<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="48c2d-104">The example sets the value of a <xref:System.Windows.Forms.Panel> control’s <xref:System.Windows.Forms.Padding> property to 5 and sets the <xref:System.Windows.Forms.Control.Dock%2A> property of a child <xref:System.Windows.Forms.RichTextBox> control to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="48c2d-105"><xref:System.Windows.Forms.Control.BackColor%2A>的<xref:System.Windows.Forms.Panel>控制設為<xref:System.Drawing.Color.Blue%2A>，這會建立藍色框線<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="48c2d-105">The <xref:System.Windows.Forms.Control.BackColor%2A> of the <xref:System.Windows.Forms.Panel> control is set to <xref:System.Drawing.Color.Blue%2A>, which creates a blue border around the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48c2d-106">範例</span><span class="sxs-lookup"><span data-stu-id="48c2d-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="48c2d-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48c2d-107">See also</span></span>

- <xref:System.Windows.Forms.Padding>
- [<span data-ttu-id="48c2d-108">Windows Form 控制項的邊界和邊框距離</span><span class="sxs-lookup"><span data-stu-id="48c2d-108">Margin and Padding in Windows Forms Controls</span></span>](margin-and-padding-in-windows-forms-controls.md)
