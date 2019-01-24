---
title: HOW TO：覆寫相依性屬性的中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: ba2f98d262f5c43dbd0c07d356556cdc3ec4b8dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589749"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>HOW TO：覆寫相依性屬性的中繼資料
此範例示範如何覆寫預設相依性屬性中繼資料來自繼承的類別，藉由呼叫<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>方法，並提供特定類型的中繼資料。  
  
## <a name="example"></a>範例  
 藉由定義其<xref:System.Windows.PropertyMetadata>，類別可以定義相依性屬性的行為，例如其預設值和屬性系統回呼。 許多相依性屬性類別都已經有建立為其註冊程序一部分的預設中繼資料。 這包括屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 一部分的相依性屬性。 透過其類別繼承而繼承相依性屬性的類別可以覆寫原始中繼資料；因此，可透過中繼資料變更之屬性的特性會符合所有子類別特定需求。  
  
 屬性系統使用所放入的屬性之前，必須覆寫相依性屬性上的中繼資料 (這等同於具現化可註冊屬性之物件的特定執行個體的時間)。 若要呼叫<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>必須在本身提供為類型的靜態建構函式中執行`forType`參數<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>。 如果您嘗試在擁有者類型的執行個體存在之後變更中繼資料，則這不會引發例外狀況，但會在屬性系統中導致不一致的行為。 此外，一種類型只能覆寫中繼資料一次。 後續覆寫相同類型上中繼資料的嘗試將會引發例外狀況。  
  
 在下列範例中，自訂類別 `MyAdvancedStateControl` 會將 `MyAdvancedStateControl` 針對 `StateProperty` 所提供的中繼資料覆寫為新的屬性中繼資料。 例如，在新建構之 `MyAdvancedStateControl` 執行個體上查詢屬性時，`StateProperty` 的預設值現在會是 `true`。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.DependencyProperty>
- [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
