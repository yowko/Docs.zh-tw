---
title: "如何：覆寫相依性屬性的中繼資料 | Microsoft Docs"
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
  - "相依性屬性, 覆寫中繼資料"
  - "中繼資料, 針對相依性屬性覆寫"
  - "覆寫相依性屬性的中繼資料"
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：覆寫相依性屬性的中繼資料
本範例顯示如何藉由呼叫 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 方法和提供型別專有中繼資料 \(Metadata\)，以覆寫來自繼承類別的預設相依性屬性中繼資料。  
  
## 範例  
 藉由定義 <xref:System.Windows.PropertyMetadata>，類別可定義[相依性屬性](GTMT)的行為，例如其預設值和屬性系統回呼 \(Callback\)。  許多相依性屬性類別在註冊時都已建立了預設中繼資料。  其中包括屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 一部分的相依性屬性。  透過類別繼承來繼承相依性屬性的類別會覆寫原始中繼資料，因此可透過中繼資料變更之屬性的特性將符合任何子類別特定需求。  
  
 覆寫相依性屬性上的中繼資料，必須在提供該屬性給屬性系統使用之前完成 \(也就是註冊屬性之物件的特定執行個體進行執行個體化之前\)。  <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 的呼叫必須在提供本身做為 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 之 `forType` 參數的型別的靜態建構函式內執行。  如果您嘗試在擁有者型別的執行個體一旦存在時變更中繼資料，並不會引發例外狀況，但會造成屬性系統中的行為不一致。  此外，每個型別的中繼資料只能覆寫一次。  接下來若要嘗試覆寫相同型別上的中繼資料，就會引發例外狀況。  
  
 在下列範例中，自訂類別 `MyAdvancedStateControl` 會使用新的屬性中繼資料覆寫 `MyAdvancedStateControl` 提供給 `StateProperty` 的中繼資料。  例如，當在新建構的 `MyAdvancedStateControl` 上查詢屬性時，`StateProperty` 的預設值這時就會是 `true`。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## 請參閱  
 <xref:System.Windows.DependencyProperty>   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)