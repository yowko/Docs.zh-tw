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
ms.openlocfilehash: 4db87c5f266a9eed136f0651f48d11720abede65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053856"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 載入和相依性屬性
目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作，在本質上就會感知相依性屬性。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在載入二進位 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和處理相依性屬性的屬性時，會使用相依性屬性的屬性系統方法。 這可有效略過屬性的包裝函式。 當您實作自訂相依性屬性時，您必須負責此行為，而且應該避免任何其他程式碼置於屬性系統方法您屬性包裝函式<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從相依性屬性的消費者和作者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)和[自訂相依性屬性](custom-dependency-properties.md)。 此外，您應已閱讀 [XAML 概觀 (WPF)](xaml-overview-wpf.md) 和 [XAML 語法詳細資料](xaml-syntax-in-detail.md)。  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML 載入器實作與效能  
 基於實作原因，是比較節省運算成本來識別相依性屬性的屬性和存取屬性系統<xref:System.Windows.DependencyObject.SetValue%2A>方法來設定，而不使用屬性包裝函式和其 setter。 這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器僅能藉由各種字串和標記之結構所表示的型別和成員關聯性，來推斷支援程式碼的整個物件模型。  
  
 型別查閱透過 xmlns 和組件屬性，但識別成員、 判斷其可以支援設為屬性 (attribute) 的組合，並解決何種支援的屬性值的類型就需要廣泛的反映使用<xref:System.Reflection.PropertyInfo>。 因為指定的型別上的相依性屬性為透過屬性系統中，儲存體資料表來存取[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作其[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會使用此資料表，並且推斷的任何給定屬性*ABC*可以藉由呼叫更有效率地設定<xref:System.Windows.DependencyObject.SetValue%2A>上包含<xref:System.Windows.DependencyObject>衍生型別，使用相依性屬性識別項*ABCProperty*。  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>自訂相依性屬性的影響  
 由於目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其屬性設定行為完全略過包裝函式，因此您不應該將任何其他邏輯放入自訂相依性屬性之包裝函式的集合定義中。 如果您在集合定義中放置這類邏輯，則在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定屬性 (而不是在程式碼中設定) 時，將不會執行邏輯。  
  
 同樣地，其他層面[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]取得屬性值的處理器[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理會使用<xref:System.Windows.DependencyObject.GetValue%2A>而不是使用包裝函式。 因此，您也應該避免任何額外的實作，在`get`超出定義<xref:System.Windows.DependencyObject.GetValue%2A>呼叫。  
  
 下列範例是建議的相依性屬性定義與包裝函式，其中將屬性識別項儲存為 `public` `static` `readonly` 欄位，而 `get` 和 `set` 定義所包含的程式碼也都在定義支援相依性屬性的必要屬性系統方法範圍內。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [集合類型的相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)
