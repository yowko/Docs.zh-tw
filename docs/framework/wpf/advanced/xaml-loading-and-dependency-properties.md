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
ms.openlocfilehash: 57c25297f995acd1ef307466258b5f4e03cc3098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459540"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 載入和相依性屬性
目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作，在本質上就會感知相依性屬性。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在載入二進位 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和處理相依性屬性的屬性時，會使用相依性屬性的屬性系統方法。 這可有效略過屬性的包裝函式。 當您執行自訂相依性屬性時，您必須考慮這項行為，而且應該避免在屬性系統方法 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>以外的其他任何程式碼。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 本主題假設您已從相依性屬性的消費者和作者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)和[自訂相依性屬性](custom-dependency-properties.md)。 此外，您應已閱讀 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md) 和 [XAML 語法詳細資料](xaml-syntax-in-detail.md)。  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML 載入器實作與效能  
 基於執行的理由，將屬性識別為相依性屬性，並存取屬性系統 <xref:System.Windows.DependencyObject.SetValue%2A> 方法來設定它，而不是使用屬性包裝函式及其 setter，計算成本會比較低。 這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器僅能藉由各種字串和標記之結構所表示的型別和成員關聯性，來推斷支援程式碼的整個物件模型。  
  
 此類型是透過 xmlns 和元件屬性的組合進行查閱，但是識別成員、判斷哪些可支援設定為屬性，以及解析屬性值支援的型別，否則會需要大量的反映使用 <xref:System.Reflection.PropertyInfo>。 因為指定類型上的相依性屬性可透過屬性系統存取為儲存體資料表，所以其 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 執行會使用此資料表，並推斷是否可以更有效率地設定任何指定的屬性*ABC*使用相依性屬性識別碼*ABCProperty*，在包含 <xref:System.Windows.DependencyObject> 衍生類型上呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>。  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>自訂相依性屬性的影響  
 由於目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其屬性設定行為完全略過包裝函式，因此您不應該將任何其他邏輯放入自訂相依性屬性之包裝函式的集合定義中。 如果您在集合定義中放置這類邏輯，則在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定屬性 (而不是在程式碼中設定) 時，將不會執行邏輯。  
  
 同樣地，從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理取得屬性值的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的其他層面也會使用 <xref:System.Windows.DependencyObject.GetValue%2A>，而不是使用包裝函式。 因此，您也應該避免 <xref:System.Windows.DependencyObject.GetValue%2A> 呼叫以外的 `get` 定義中的任何額外的執行。  
  
 下列範例是建議的相依性屬性定義與包裝函式，其中將屬性識別項儲存為 `public` `static` `readonly` 欄位，而 `get` 和 `set` 定義所包含的程式碼也都在定義支援相依性屬性的必要屬性系統方法範圍內。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [集合類型的相依性屬性](collection-type-dependency-properties.md)
- [相依性屬性的安全性](dependency-property-security.md)
- [DependencyObject 的安全建構函式模式](safe-constructor-patterns-for-dependencyobjects.md)
