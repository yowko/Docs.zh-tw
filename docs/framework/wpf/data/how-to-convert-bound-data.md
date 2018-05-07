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
ms.openlocfilehash: 526305f32280fb75e95538b9014c34c11ed8bffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-bound-data"></a>如何：轉換繫結的資料
這個範例示範如何套用資料繫結中所使用的轉換。  
  
 若要在繫結期間轉換資料，您必須建立實作的類別<xref:System.Windows.Data.IValueConverter>介面，其中包括<xref:System.Windows.Data.IValueConverter.Convert%2A>和<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方法。  
  
## <a name="example"></a>範例  
 下列範例顯示將傳入，讓它只會顯示一年、 月和日的日期值，轉換的日期轉換子的實作。 實作時<xref:System.Windows.Data.IValueConverter>介面，它是最好的作法是裝飾實作<xref:System.Windows.Data.ValueConversionAttribute>屬性來指出開發工具的資料相關的類型轉換，如下列範例所示：  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 一旦您已建立轉換程式，您可以將它當做中的資源程式[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。 在下列範例中， *src*對應至命名空間，其中*DateConverter*定義。  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後，您可以在您使用下列語法的繫結中使用轉換程式。 在下列範例中，文字內容<xref:System.Windows.Controls.TextBlock>繫結至*StartDate*，即為外部資料來源屬性。  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 在上述範例中所參考的樣式資源不會顯示在本主題中的資源區段中定義。  
  
## <a name="see-also"></a>另請參閱  
 [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
