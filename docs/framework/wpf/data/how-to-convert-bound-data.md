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
# <a name="how-to-convert-bound-data"></a>如何：轉換繫結的資料
這個範例示範如何將轉換套用到系結中使用的資料。  
  
 若要在系結期間轉換資料，您必須建立一個可執行 <xref:System.Windows.Data.IValueConverter> 介面的類別，其中包括 <xref:System.Windows.Data.IValueConverter.Convert%2A> 和 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方法。  
  
## <a name="example"></a>範例  
 下列範例顯示日期轉換器的執行，該轉換子會轉換傳入的日期值，使其只顯示年、月和日。 在執行 <xref:System.Windows.Data.IValueConverter> 介面時，最好使用 <xref:System.Windows.Data.ValueConversionAttribute> 屬性來裝飾執行，以向開發工具指出轉換所涉及的資料類型，如下列範例所示：  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 建立轉換器之後，您可以將它新增為 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案中的資源。 在下列範例中， *src*會對應到定義了*DateConverter*的命名空間。  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後，您可以使用下列語法，在系結中使用轉換器。 在下列範例中，<xref:System.Windows.Controls.TextBlock> 的文字內容系*結至「* 開始」，也就是外部資料源的屬性。  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 上述範例所參考的樣式資源定義于資源區段中，但未顯示在本主題中。  
  
## <a name="see-also"></a>請參閱

- [實作繫結驗證](how-to-implement-binding-validation.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
