---
title: "如何：將資料繫結至 InkCanvas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdcd67f972dafa2de7fb74e01b4a3c22dfd848fb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a><span data-ttu-id="a8176-102">如何：將資料繫結至 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="a8176-102">How to: Data Bind to an InkCanvas</span></span>
## <a name="example"></a><span data-ttu-id="a8176-103">範例</span><span class="sxs-lookup"><span data-stu-id="a8176-103">Example</span></span>  
 <span data-ttu-id="a8176-104">下列範例示範如何將繫結<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性<xref:System.Windows.Controls.InkCanvas>到另一個<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="a8176-104">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property of an <xref:System.Windows.Controls.InkCanvas> to another <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 <span data-ttu-id="a8176-105">下列範例示範如何將繫結<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>到資料來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8176-105">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property to a data source.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 <span data-ttu-id="a8176-106">下列範例會宣告兩個<xref:System.Windows.Controls.InkCanvas>XAML 中的物件，並建立其與其他資料來源之間的資料繫結。</span><span class="sxs-lookup"><span data-stu-id="a8176-106">The following example declares two <xref:System.Windows.Controls.InkCanvas> objects in XAML and establishes data binding between them and other data sources.</span></span>  <span data-ttu-id="a8176-107">第一個<xref:System.Windows.Controls.InkCanvas>，稱為`ic`，繫結至兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="a8176-107">The first <xref:System.Windows.Controls.InkCanvas>, called `ic`, is bound to two data sources.</span></span>  <span data-ttu-id="a8176-108"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>和<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性`ic`繫結至<xref:System.Windows.Controls.ListBox>物件，會接著繫結至定義在 XAML 中的陣列。</span><span class="sxs-lookup"><span data-stu-id="a8176-108">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> and <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties on `ic` are bound to <xref:System.Windows.Controls.ListBox> objects, which are in turn bound to arrays defined in the XAML.</span></span>  <span data-ttu-id="a8176-109"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>， <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，和<xref:System.Windows.Controls.InkCanvas.Strokes%2A>屬性的第二個<xref:System.Windows.Controls.InkCanvas>繫結至第一個<xref:System.Windows.Controls.InkCanvas>， `ic`。</span><span class="sxs-lookup"><span data-stu-id="a8176-109">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, and <xref:System.Windows.Controls.InkCanvas.Strokes%2A> properties of the second <xref:System.Windows.Controls.InkCanvas> are bound to the first <xref:System.Windows.Controls.InkCanvas>, `ic`.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
