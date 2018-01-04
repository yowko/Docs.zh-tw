---
title: "如何：使用 ColumnDefinitionsCollections 和 RowDefinitionsCollections 管理資料行和資料列"
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
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ba9566e9688984cc881a94e39b065fdadb4cc11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a><span data-ttu-id="3a7bb-102">如何：使用 ColumnDefinitionsCollections 和 RowDefinitionsCollections 管理資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="3a7bb-102">How to: Manipulate Columns and Rows by Using ColumnDefinitionsCollections and RowDefinitionsCollections</span></span>
<span data-ttu-id="3a7bb-103">這個範例示範如何使用中的方法<xref:System.Windows.Controls.ColumnDefinitionCollection>和<xref:System.Windows.Controls.RowDefinitionCollection>類別來執行動作，例如加入、 清除，或計算資料列或資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-103">This example shows how to use the methods in the <xref:System.Windows.Controls.ColumnDefinitionCollection> and <xref:System.Windows.Controls.RowDefinitionCollection> classes to perform actions like adding, clearing, or counting the contents of rows or columns.</span></span> <span data-ttu-id="3a7bb-104">例如，您可以<xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>， <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>，或<xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A>中包含的項目<xref:System.Windows.Controls.ColumnDefinition>或<xref:System.Windows.Controls.RowDefinition>。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-104">For example, you can <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, or <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> the items that are included in a <xref:System.Windows.Controls.ColumnDefinition> or <xref:System.Windows.Controls.RowDefinition>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a7bb-105">範例</span><span class="sxs-lookup"><span data-stu-id="3a7bb-105">Example</span></span>  
 <span data-ttu-id="3a7bb-106">下列範例會建立<xref:System.Windows.Controls.Grid>具有項目<xref:System.Windows.FrameworkElement.Name%2A>的`grid1`。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-106">The following example creates a <xref:System.Windows.Controls.Grid> element with a <xref:System.Windows.FrameworkElement.Name%2A> of `grid1`.</span></span> <span data-ttu-id="3a7bb-107"><xref:System.Windows.Controls.Grid>包含<xref:System.Windows.Controls.StackPanel>保存<xref:System.Windows.Controls.Button>項目，每個由另一個集合方法。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-107">The <xref:System.Windows.Controls.Grid> contains a <xref:System.Windows.Controls.StackPanel> that holds <xref:System.Windows.Controls.Button> elements, each controlled by a different collection method.</span></span> <span data-ttu-id="3a7bb-108">當您按一下<xref:System.Windows.Controls.Button>，它便會啟用方法呼叫程式碼後置檔案中的。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-108">When you click a <xref:System.Windows.Controls.Button>, it activates a method call in the code-behind file.</span></span>  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="3a7bb-109">這個範例會定義一系列的自訂方法，每個對應至<xref:System.Windows.Controls.Primitives.ButtonBase.Click>中的事件[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-109">This example defines a series of custom methods, each corresponding to a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="3a7bb-110">您可以變更資料行中的資料列數目<xref:System.Windows.Controls.Grid>在幾種，包括加入或移除資料列和資料行; 以及計算的資料列和資料行總數。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-110">You can change the number of columns and rows in the <xref:System.Windows.Controls.Grid> in several ways, which includes adding or removing rows and columns; and counting the total number of rows and columns.</span></span> <span data-ttu-id="3a7bb-111">若要避免<xref:System.ArgumentOutOfRangeException>和<xref:System.ArgumentException>例外狀況，您可以使用錯誤檢查功能，<xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A>方法提供。</span><span class="sxs-lookup"><span data-stu-id="3a7bb-111">To prevent <xref:System.ArgumentOutOfRangeException> and <xref:System.ArgumentException> exceptions, you can use the error-checking functionality that the <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> method provides.</span></span>  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3a7bb-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a7bb-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
