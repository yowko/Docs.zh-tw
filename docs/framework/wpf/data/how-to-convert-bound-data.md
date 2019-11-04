---
title: 如何：轉換繫結的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458865"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="5cabe-102">如何：轉換繫結的資料</span><span class="sxs-lookup"><span data-stu-id="5cabe-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="5cabe-103">這個範例示範如何將轉換套用到系結中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="5cabe-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="5cabe-104">若要在系結期間轉換資料，您必須建立一個可執行 <xref:System.Windows.Data.IValueConverter> 介面的類別，其中包括 <xref:System.Windows.Data.IValueConverter.Convert%2A> 和 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5cabe-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cabe-105">範例</span><span class="sxs-lookup"><span data-stu-id="5cabe-105">Example</span></span>  
 <span data-ttu-id="5cabe-106">下列範例顯示日期轉換器的執行，該轉換子會轉換傳入的日期值，使其只顯示年、月和日。</span><span class="sxs-lookup"><span data-stu-id="5cabe-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="5cabe-107">在執行 <xref:System.Windows.Data.IValueConverter> 介面時，最好使用 <xref:System.Windows.Data.ValueConversionAttribute> 屬性來裝飾執行，以向開發工具指出轉換所涉及的資料類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5cabe-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="5cabe-108">建立轉換器之後，您可以將它新增為 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案中的資源。</span><span class="sxs-lookup"><span data-stu-id="5cabe-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="5cabe-109">在下列範例中， *src*會對應到定義了*DateConverter*的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5cabe-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="5cabe-110">最後，您可以使用下列語法，在系結中使用轉換器。</span><span class="sxs-lookup"><span data-stu-id="5cabe-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="5cabe-111">在下列範例中，<xref:System.Windows.Controls.TextBlock> 的文字內容系*結至「* 開始」，也就是外部資料源的屬性。</span><span class="sxs-lookup"><span data-stu-id="5cabe-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="5cabe-112">上述範例所參考的樣式資源定義于資源區段中，但未顯示在本主題中。</span><span class="sxs-lookup"><span data-stu-id="5cabe-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cabe-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5cabe-113">See also</span></span>

- [<span data-ttu-id="5cabe-114">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="5cabe-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="5cabe-115">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="5cabe-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5cabe-116">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="5cabe-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
