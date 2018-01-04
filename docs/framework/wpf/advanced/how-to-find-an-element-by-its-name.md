---
title: "如何：依名稱尋找項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c51f22cb663b77ddcbbc280ab9d93c5e0eb7405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a><span data-ttu-id="4de65-102">如何：依名稱尋找項目</span><span class="sxs-lookup"><span data-stu-id="4de65-102">How to: Find an Element by Its Name</span></span>
<span data-ttu-id="4de65-103">這個範例說明如何使用<xref:System.Windows.FrameworkElement.FindName%2A>方法來尋找項目由其<xref:System.Windows.FrameworkElement.Name%2A>值。</span><span class="sxs-lookup"><span data-stu-id="4de65-103">This example describes how to use the <xref:System.Windows.FrameworkElement.FindName%2A> method to find an element by its <xref:System.Windows.FrameworkElement.Name%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4de65-104">範例</span><span class="sxs-lookup"><span data-stu-id="4de65-104">Example</span></span>  
 <span data-ttu-id="4de65-105">在此範例中，若要尋找特定的項目依其名稱的方法會寫入成為按鈕的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4de65-105">In this example, the method to find a particular element by its name is written as the event handler of a button.</span></span> <span data-ttu-id="4de65-106">`stackPanel`是<xref:System.Windows.FrameworkElement.Name%2A>根的<xref:System.Windows.FrameworkElement>正在搜尋範例方法然後以視覺方式表示找到的項目透過將轉型成<xref:System.Windows.Controls.TextBlock>和變更其中一個<xref:System.Windows.Controls.TextBlock>可見[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]屬性。</span><span class="sxs-lookup"><span data-stu-id="4de65-106">`stackPanel` is the <xref:System.Windows.FrameworkElement.Name%2A> of the root <xref:System.Windows.FrameworkElement> being searched, and the example method then visually indicates the found element by casting it as <xref:System.Windows.Controls.TextBlock> and changing one of the <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] properties.</span></span>  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
