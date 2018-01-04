---
title: "如何：使用邊框距離在 Windows Form 控制項周圍建立框線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b8fc8774e1f861db989b05678235ea34e38318c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a><span data-ttu-id="d5a10-102">如何：使用邊框距離在 Windows Form 控制項周圍建立框線</span><span class="sxs-lookup"><span data-stu-id="d5a10-102">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>
<span data-ttu-id="d5a10-103">下列程式碼範例示範如何建立框線或外框<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="d5a10-103">The following code example demonstrates how to create a border or outline around a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="d5a10-104">此範例設定的值<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Padding>5 和集合的屬性<xref:System.Windows.Forms.Control.Dock%2A>屬性的子系<xref:System.Windows.Forms.RichTextBox>控制權傳輸至<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="d5a10-104">The example sets the value of a <xref:System.Windows.Forms.Panel> control’s <xref:System.Windows.Forms.Padding> property to 5 and sets the <xref:System.Windows.Forms.Control.Dock%2A> property of a child <xref:System.Windows.Forms.RichTextBox> control to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="d5a10-105"><xref:System.Windows.Forms.Control.BackColor%2A>的<xref:System.Windows.Forms.Panel>控制設為  <xref:System.Drawing.Color.Blue%2A>，它會建立周圍的藍色框線<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="d5a10-105">The <xref:System.Windows.Forms.Control.BackColor%2A> of the <xref:System.Windows.Forms.Panel> control is set to <xref:System.Drawing.Color.Blue%2A>, which creates a blue border around the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a10-106">範例</span><span class="sxs-lookup"><span data-stu-id="d5a10-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d5a10-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5a10-107">See Also</span></span>  
 <xref:System.Windows.Forms.Padding>  
 [<span data-ttu-id="d5a10-108">Windows Forms 控制項的邊界和邊框距離</span><span class="sxs-lookup"><span data-stu-id="d5a10-108">Margin and Padding in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
