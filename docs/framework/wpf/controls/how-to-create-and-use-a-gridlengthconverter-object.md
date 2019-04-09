---
title: HOW TO：建立和使用 GridLengthConverter 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: 498d2b9c531f391f4cbeb1478469a99d381deec7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206781"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="add99-102">HOW TO：建立和使用 GridLengthConverter 物件</span><span class="sxs-lookup"><span data-stu-id="add99-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="add99-103">範例</span><span class="sxs-lookup"><span data-stu-id="add99-103">Example</span></span>  
 <span data-ttu-id="add99-104">下列範例示範如何建立和使用的執行個體<xref:System.Windows.GridLengthConverter>。</span><span class="sxs-lookup"><span data-stu-id="add99-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="add99-105">此範例會定義呼叫的自訂方法`changeCol`，哪一個階段<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.GridLengthConverter>可將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Windows.GridLength>。</span><span class="sxs-lookup"><span data-stu-id="add99-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="add99-106">已轉換的值傳遞的值<xref:System.Windows.Controls.ColumnDefinition.Width%2A>屬性<xref:System.Windows.Controls.ColumnDefinition>項目。</span><span class="sxs-lookup"><span data-stu-id="add99-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="add99-107">此範例也會定義第二個的自訂方法，稱為`changeColVal`。</span><span class="sxs-lookup"><span data-stu-id="add99-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="add99-108">這個自訂的方法轉換<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>的<xref:System.Windows.Controls.Slider>要<xref:System.String>和傳遞的值將會回到<xref:System.Windows.Controls.ColumnDefinition>做為<xref:System.Windows.Controls.ColumnDefinition.Width%2A>的項目。</span><span class="sxs-lookup"><span data-stu-id="add99-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="add99-109">請注意，個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案中定義的內容<xref:System.Windows.Controls.ListBoxItem>。</span><span class="sxs-lookup"><span data-stu-id="add99-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="add99-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="add99-110">See also</span></span>

- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
