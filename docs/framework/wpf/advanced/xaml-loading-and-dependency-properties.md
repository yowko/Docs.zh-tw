---
title: "XAML 載入和相依性屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9771aa05d029603a018e041644ff3e2018e26ca4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 載入和相依性屬性
目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作，在本質上就會感知相依性屬性。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在載入二進位 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和處理相依性屬性的屬性時，會使用相依性屬性的屬性系統方法。 這可有效略過屬性的包裝函式。 當您實作自訂的相依性屬性時，您必須負責這種行為，並置於您的內容包裝函式屬性系統方法以外的任何其他程式碼應該避免<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>。  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從相依性屬性的消費者和作者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)和[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。 此外，您應已閱讀 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) 和 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>WPF XAML 載入器實作與效能  
 基於實作原因，是較不費時屬性做為相依性屬性的識別及存取屬性系統<xref:System.Windows.DependencyObject.SetValue%2A>方法來設定它，而不是使用屬性的包裝函式和其 setter。 這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器僅能藉由各種字串和標記之結構所表示的型別和成員關聯性，來推斷支援程式碼的整個物件模型。  
  
 型別查閱透過 xmlns 和組件屬性，但是識別的成員，決定無法設定屬性，為支援的組合和解決何種類型的屬性值支援否則會需要大量的反映使用<xref:System.Reflection.PropertyInfo>。 因為相依性屬性上指定的型別為屬性系統，透過儲存體資料表存取[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作其[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會使用此資料表，並且推斷的任何給定屬性*ABC*您可以更有效率地將藉由呼叫<xref:System.Windows.DependencyObject.SetValue%2A>上包含<xref:System.Windows.DependencyObject>衍生型別，使用相依性屬性的識別項*ABCProperty*。  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>自訂相依性屬性的影響  
 由於目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其屬性設定行為完全略過包裝函式，因此您不應該將任何其他邏輯放入自訂相依性屬性之包裝函式的集合定義中。 如果您在集合定義中放置這類邏輯，則在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定屬性 (而不是在程式碼中設定) 時，將不會執行邏輯。  
  
 同樣地，其他方面的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]取得屬性值的處理器[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理也使用<xref:System.Windows.DependencyObject.GetValue%2A>而不是使用包裝函式。 因此，您也應該避免在任何其他實作`get`超出定義<xref:System.Windows.DependencyObject.GetValue%2A>呼叫。  
  
 下列範例是建議的相依性屬性定義與包裝函式，其中將屬性識別項儲存為 `public` `static` `readonly` 欄位，而 `get` 和 `set` 定義所包含的程式碼也都在定義支援相依性屬性的必要屬性系統方法範圍內。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [集合類型的相依性屬性](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [DependencyObject 的安全建構函式模式](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
