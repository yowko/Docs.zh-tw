---
title: XAML 載入和相依性屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186244"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 載入和相依性屬性
目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作，在本質上就會感知相依性屬性。 載入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]作為依賴項屬性的二進位[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性和處理屬性時，處理器對依賴項屬性使用屬性系統方法。 這可有效略過屬性的包裝函式。 實現自訂依賴項屬性時，必須考慮此行為，並且應避免將任何其他代碼放在屬性系統方法和<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>以外的屬性包裝器中。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從相依性屬性的消費者和作者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)和[自訂相依性屬性](custom-dependency-properties.md)。 此外，您應已閱讀 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md) 和 [XAML 語法詳細資料](xaml-syntax-in-detail.md)。  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML 載入器實作與效能  
 出於實現原因，將屬性標識為依賴項屬性並訪問屬性系統<xref:System.Windows.DependencyObject.SetValue%2A>方法來設置屬性比使用屬性包裝器及其 setter 的成本更低。 這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器僅能藉由各種字串和標記之結構所表示的型別和成員關聯性，來推斷支援程式碼的整個物件模型。  
  
 類型通過 xmlns 和程式集屬性的組合進行查看，但標識成員，確定哪些可以支援設置為屬性，並解析屬性值支援的類型，否則需要使用<xref:System.Reflection.PropertyInfo>進行廣泛的反射。 由於給定類型的依賴項屬性可通過屬性系統作為存儲[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]表訪問，因此其[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器的實現使用此表，並推斷任何給定屬性 ABC 可以通過使用依賴<xref:System.Windows.DependencyObject.SetValue%2A><xref:System.Windows.DependencyObject>項屬性識別碼 ABC*屬性*調用，更有效地設置任何給定屬性*ABC。*  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>自訂相依性屬性的影響  
 由於目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其屬性設定行為完全略過包裝函式，因此您不應該將任何其他邏輯放入自訂相依性屬性之包裝函式的集合定義中。 如果您在集合定義中放置這類邏輯，則在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定屬性 (而不是在程式碼中設定) 時，將不會執行邏輯。  
  
 同樣，從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理中獲取屬性值的處理器的其他方面也使用<xref:System.Windows.DependencyObject.GetValue%2A>而不是使用包裝器。 因此，還應避免在`get`<xref:System.Windows.DependencyObject.GetValue%2A>調用之外的定義中的任何其他實現。  
  
 下面的示例是建議使用包裝器的依賴項屬性定義，其中屬性識別碼存儲為欄位`public``static``readonly`，`get`和`set`定義不包含定義依賴項屬性支援的必要屬性系統方法之外的代碼。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [集合類型相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)
