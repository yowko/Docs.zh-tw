---
title: HOW TO：轉換繫結的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093796"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="809d4-102">HOW TO：轉換繫結的資料</span><span class="sxs-lookup"><span data-stu-id="809d4-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="809d4-103">此範例示範如何套用轉換成繫結中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="809d4-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="809d4-104">若要轉換的資料繫結期間，您必須建立可實作類別<xref:System.Windows.Data.IValueConverter>介面，其中包括<xref:System.Windows.Data.IValueConverter.Convert%2A>和<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="809d4-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="809d4-105">範例</span><span class="sxs-lookup"><span data-stu-id="809d4-105">Example</span></span>  
 <span data-ttu-id="809d4-106">下列範例顯示將傳入，讓它只會顯示一年、 月和日的日期值，轉換的日期轉換子的實作。</span><span class="sxs-lookup"><span data-stu-id="809d4-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="809d4-107">實作時<xref:System.Windows.Data.IValueConverter>介面後，它是個不錯的做法裝飾與實作<xref:System.Windows.Data.ValueConversionAttribute>屬性來指出開發工具的轉換，如下列範例中的資料類型：</span><span class="sxs-lookup"><span data-stu-id="809d4-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="809d4-108">一旦您已建立的轉換子，您就可以將它新增為資源您[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="809d4-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="809d4-109">在下列範例中， *src*對應至命名空間，其中*DateConverter*定義。</span><span class="sxs-lookup"><span data-stu-id="809d4-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="809d4-110">最後，您可以使用這個轉換子中繫結使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="809d4-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="809d4-111">在下列範例中，文字內容<xref:System.Windows.Controls.TextBlock>繫結至*StartDate*，即為外部資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="809d4-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="809d4-112">在上述範例中所參考的樣式資源不會顯示在本主題的資源區段中定義。</span><span class="sxs-lookup"><span data-stu-id="809d4-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="809d4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="809d4-113">See also</span></span>

- [<span data-ttu-id="809d4-114">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="809d4-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="809d4-115">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="809d4-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="809d4-116">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="809d4-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
