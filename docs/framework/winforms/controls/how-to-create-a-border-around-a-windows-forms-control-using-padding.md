---
title: 使用填補在控制項周圍建立框線
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
ms.openlocfilehash: 114186ab5784cf892cb01e9fe2648ce22cecc4b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742194"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a><span data-ttu-id="f0367-102">如何：使用邊框距離在 Windows Form 控制項周圍建立框線</span><span class="sxs-lookup"><span data-stu-id="f0367-102">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>
<span data-ttu-id="f0367-103">下列程式碼範例示範如何在 <xref:System.Windows.Forms.RichTextBox> 控制項周圍建立框線或外框。</span><span class="sxs-lookup"><span data-stu-id="f0367-103">The following code example demonstrates how to create a border or outline around a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="f0367-104">這個範例會將 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Padding> 屬性值設定為5，並將子 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 [<xref:System.Windows.Forms.DockStyle.Fill>]。</span><span class="sxs-lookup"><span data-stu-id="f0367-104">The example sets the value of a <xref:System.Windows.Forms.Panel> control’s <xref:System.Windows.Forms.Padding> property to 5 and sets the <xref:System.Windows.Forms.Control.Dock%2A> property of a child <xref:System.Windows.Forms.RichTextBox> control to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="f0367-105"><xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 設定為 [<xref:System.Drawing.Color.Blue%2A>]，這會在 <xref:System.Windows.Forms.RichTextBox> 控制項周圍建立藍色的框線。</span><span class="sxs-lookup"><span data-stu-id="f0367-105">The <xref:System.Windows.Forms.Control.BackColor%2A> of the <xref:System.Windows.Forms.Panel> control is set to <xref:System.Drawing.Color.Blue%2A>, which creates a blue border around the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0367-106">範例</span><span class="sxs-lookup"><span data-stu-id="f0367-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f0367-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0367-107">See also</span></span>

- <xref:System.Windows.Forms.Padding>
- [<span data-ttu-id="f0367-108">Windows Forms 控制項的邊界和邊框距離</span><span class="sxs-lookup"><span data-stu-id="f0367-108">Margin and Padding in Windows Forms Controls</span></span>](margin-and-padding-in-windows-forms-controls.md)
