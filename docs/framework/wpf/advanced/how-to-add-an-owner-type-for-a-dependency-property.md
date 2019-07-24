---
title: HOW TO：新增相依性屬性的擁有者類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401128"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>HOW TO：新增相依性屬性的擁有者類型
這個範例示範如何加入類別, 做為針對不同類型註冊之相依性屬性的擁有者。 如此一來, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器和屬性系統就能夠將類別辨識為屬性的其他擁有者。 新增為擁有者可選擇性地允許加入類別, 以提供特定類型的中繼資料。  
  
 在下列範例中, `StateProperty`是`MyStateControl`類別所註冊的屬性。 類別`UnrelatedStateControl`會`StateProperty` 使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法, 將本身新增為的擁有者, 特別是使用簽章, 該簽章可讓相依性屬性的新中繼資料存在於加入型別上。 請注意, 您應該提供屬性的通用語言執行平臺 (CLR) 存取子, 類似于實作為相依性[屬性](how-to-implement-a-dependency-property.md)範例中所示的範例, 以及重新公開要新增為擁有者之類別的相依性屬性識別碼。  
  
 如果沒有包裝函式, 相依性屬性仍然可以從使用<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>的程式設計存取觀點來處理。 但您通常會想要將這個屬性系統行為與 CLR 屬性包裝函式進行平行處理。 包裝函式可讓您以程式設計方式輕鬆設定相依性屬性, 並可將屬性設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]為屬性。  
  
 若要瞭解如何覆寫預設中繼資料, 請參閱覆寫相依性[屬性的中繼資料](how-to-override-metadata-for-a-dependency-property.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>另請參閱

- [自訂相依性屬性](custom-dependency-properties.md)
- [相依性屬性概觀](dependency-properties-overview.md)
