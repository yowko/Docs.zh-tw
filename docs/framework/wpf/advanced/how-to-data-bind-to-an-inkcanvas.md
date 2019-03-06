---
title: HOW TO：將資料繫結至 InkCanvas
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 5d3fc0ed7b6176d7bc68bf20af42c311b5563908
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372941"
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a><span data-ttu-id="3169d-102">HOW TO：將資料繫結至 InkCanvas</span><span class="sxs-lookup"><span data-stu-id="3169d-102">How to: Data Bind to an InkCanvas</span></span>
## <a name="example"></a><span data-ttu-id="3169d-103">範例</span><span class="sxs-lookup"><span data-stu-id="3169d-103">Example</span></span>  
 <span data-ttu-id="3169d-104">下列範例示範如何將繫結<xref:System.Windows.Controls.InkCanvas.Strokes%2A>的屬性<xref:System.Windows.Controls.InkCanvas>到另一個<xref:System.Windows.Controls.InkCanvas>。</span><span class="sxs-lookup"><span data-stu-id="3169d-104">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property of an <xref:System.Windows.Controls.InkCanvas> to another <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 <span data-ttu-id="3169d-105">下列範例示範如何將繫結<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>到資料來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="3169d-105">The following example demonstrates how to bind the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property to a data source.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 <span data-ttu-id="3169d-106">下列範例會宣告兩個<xref:System.Windows.Controls.InkCanvas>XAML 中的物件，並建立它們和其他資料來源之間的資料繫結。</span><span class="sxs-lookup"><span data-stu-id="3169d-106">The following example declares two <xref:System.Windows.Controls.InkCanvas> objects in XAML and establishes data binding between them and other data sources.</span></span>  <span data-ttu-id="3169d-107">第一個<xref:System.Windows.Controls.InkCanvas>，稱為`ic`，繫結至兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="3169d-107">The first <xref:System.Windows.Controls.InkCanvas>, called `ic`, is bound to two data sources.</span></span>  <span data-ttu-id="3169d-108"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>並<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>上的屬性`ic`繫結至<xref:System.Windows.Controls.ListBox>會接著繫結至陣列中的 XAML 定義的物件。</span><span class="sxs-lookup"><span data-stu-id="3169d-108">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> and <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties on `ic` are bound to <xref:System.Windows.Controls.ListBox> objects, which are in turn bound to arrays defined in the XAML.</span></span>  <span data-ttu-id="3169d-109"><xref:System.Windows.Controls.InkCanvas.EditingMode%2A>， <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，並<xref:System.Windows.Controls.InkCanvas.Strokes%2A>的第二個屬性<xref:System.Windows.Controls.InkCanvas>繫結至第一個<xref:System.Windows.Controls.InkCanvas>， `ic`。</span><span class="sxs-lookup"><span data-stu-id="3169d-109">The <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, and <xref:System.Windows.Controls.InkCanvas.Strokes%2A> properties of the second <xref:System.Windows.Controls.InkCanvas> are bound to the first <xref:System.Windows.Controls.InkCanvas>, `ic`.</span></span>  
  
 [!code-xaml[InkCanvasBindingSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
