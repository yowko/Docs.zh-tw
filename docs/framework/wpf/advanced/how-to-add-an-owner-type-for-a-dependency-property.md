---
title: 如何：加入相依性屬性的擁有者類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: bf3f73743d1c76145bf520ed859c27c4d3aaf662
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>如何：加入相依性屬性的擁有者類型
這個範例示範如何將類別加入做為註冊不同類型的相依性屬性的擁有者。 這樣做， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器和屬性系統都能夠辨識類別做為其他擁有者的屬性。 選擇性地加入做為擁有者可讓加入的類別，以提供特定類型的中繼資料。  
  
 在下列範例中，`StateProperty`屬性是否註冊`MyStateControl`類別。 類別`UnrelatedStateControl`將本身新增的擁有者為`StateProperty`使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法，特別使用存在於加入型別，可讓新的相依性屬性中繼資料的簽章。 請注意，您應該提供[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]類似於範例所示的屬性存取子[實作相依性屬性](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)範例中，以及重新公開的類別加入相依性屬性的識別項做為擁有者。  
  
 沒有包裝函式，相依性屬性將仍可運作以程式設計方式存取使用的觀點<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>。 但您通常想要平行的這個屬性系統行為[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性的包裝函式。 包裝函式更輕鬆地以程式設計的方式，設定相依性屬性，並使其可設定為屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性。  
  
 若要了解如何覆寫預設的中繼資料，請參閱[覆寫相依性屬性的中繼資料](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>另請參閱  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
