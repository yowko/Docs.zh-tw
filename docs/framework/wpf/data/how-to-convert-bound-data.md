---
title: "如何：轉換繫結的資料"
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
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f4bcde15940e76e1d022658e32ff6ef8676e45e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="29485-102">如何：轉換繫結的資料</span><span class="sxs-lookup"><span data-stu-id="29485-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="29485-103">這個範例示範如何套用資料繫結中所使用的轉換。</span><span class="sxs-lookup"><span data-stu-id="29485-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="29485-104">若要在繫結期間轉換資料，您必須建立實作的類別<xref:System.Windows.Data.IValueConverter>介面，其中包括<xref:System.Windows.Data.IValueConverter.Convert%2A>和<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="29485-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29485-105">範例</span><span class="sxs-lookup"><span data-stu-id="29485-105">Example</span></span>  
 <span data-ttu-id="29485-106">下列範例顯示將傳入，讓它只會顯示一年、 月和日的日期值，轉換的日期轉換子的實作。</span><span class="sxs-lookup"><span data-stu-id="29485-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="29485-107">實作時<xref:System.Windows.Data.IValueConverter>介面，它是最好的作法是裝飾實作<xref:System.Windows.Data.ValueConversionAttribute>屬性來指出開發工具的資料相關的類型轉換，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="29485-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="29485-108">一旦您已建立轉換程式，您可以將它當做中的資源程式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="29485-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="29485-109">在下列範例中， *src*對應至命名空間，其中*DateConverter*定義。</span><span class="sxs-lookup"><span data-stu-id="29485-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="29485-110">最後，您可以在您使用下列語法的繫結中使用轉換程式。</span><span class="sxs-lookup"><span data-stu-id="29485-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="29485-111">在下列範例中，文字內容<xref:System.Windows.Controls.TextBlock>繫結至*StartDate*，即為外部資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="29485-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="29485-112">在上述範例中所參考的樣式資源不會顯示在本主題中的資源區段中定義。</span><span class="sxs-lookup"><span data-stu-id="29485-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29485-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="29485-113">See Also</span></span>  
 [<span data-ttu-id="29485-114">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="29485-114">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="29485-115">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="29485-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="29485-116">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="29485-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
