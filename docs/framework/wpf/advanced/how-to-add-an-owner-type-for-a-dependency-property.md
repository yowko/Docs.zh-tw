---
title: "如何：加入相依性屬性的擁有者類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類別, 加入做為相依性屬性的擁有者"
  - "相依性屬性, 做為擁有者加入類別"
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：加入相依性屬性的擁有者類型
本範例顯示如何加入類別做為針對其他型別而註冊的相依性屬性的擁有者。  藉由進行這項作業，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器和屬性系統都能夠將類別辨識為屬性的額外擁有者。  加入做為擁有者會選擇性允許加入的類別提供型別專有的中繼資料。  
  
 下列範例中的 `StateProperty` 是 `MyStateControl` 類別所註冊的屬性。  類別 `UnrelatedStateControl` 會使用 <xref:System.Windows.DependencyProperty.AddOwner%2A> 方法，將自身加入做為 `StateProperty` 的擁有者，特別會使用簽章允許相依性屬性的新中繼資料，因為它存在於加入的型別上。  請注意，您應該要提供屬性的 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 存取子，類似[實作相依性屬性](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)範例所示，以及在要加入做為擁有者的類別上重新公開相依性屬性識別項。  
  
 在沒有包裝函式的情況下，相依性屬性 \(Property\) 還是會使用 <xref:System.Windows.DependencyObject.GetValue%2A> 或 <xref:System.Windows.DependencyObject.SetValue%2A>，從程式設計存取方面運作。  但您通常會希望讓這個屬性 \(Property\) 系統行為與 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性 \(Property\) 包裝函式一致。  包裝函式可以讓您輕鬆以程式設計方式設定相依性屬性 \(Property\)，並可以讓屬性 \(Property\) 設定為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性 \(Attribute\)。  
  
 若要知道如何覆寫預設中繼資料，請參閱 [覆寫相依性屬性的中繼資料](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)。  
  
## 範例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## 請參閱  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)