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
ms.openlocfilehash: 5069b6d6b7ded52011ec4c65ca2c47e41bba2ece
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705714"
---
# <a name="how-to-convert-bound-data"></a>HOW TO：轉換繫結的資料
此範例示範如何套用轉換成繫結中使用的資料。  
  
 若要轉換的資料繫結期間，您必須建立可實作類別<xref:System.Windows.Data.IValueConverter>介面，其中包括<xref:System.Windows.Data.IValueConverter.Convert%2A>和<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方法。  
  
## <a name="example"></a>範例  
 下列範例顯示將傳入，讓它只會顯示一年、 月和日的日期值，轉換的日期轉換子的實作。 實作時<xref:System.Windows.Data.IValueConverter>介面後，它是個不錯的做法裝飾與實作<xref:System.Windows.Data.ValueConversionAttribute>屬性來指出開發工具的轉換，如下列範例中的資料類型：  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 一旦您已建立的轉換子，您就可以將它新增為資源您[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。 在下列範例中， *src*對應至命名空間，其中*DateConverter*定義。  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後，您可以使用這個轉換子中繫結使用下列語法。 在下列範例中，文字內容<xref:System.Windows.Controls.TextBlock>繫結至*StartDate*，即為外部資料來源屬性。  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 在上述範例中所參考的樣式資源不會顯示在本主題的資源區段中定義。  
  
## <a name="see-also"></a>另請參閱
- [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
