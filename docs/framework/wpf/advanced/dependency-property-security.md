---
title: "相依性屬性的安全性 | Microsoft Docs"
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
  - "相依性屬性, access"
  - "相依性屬性, 安全性"
  - "安全性, 相依性屬性"
  - "安全性, 包裝函式"
  - "驗證, 相依性屬性"
  - "包裝函式, access"
  - "包裝函式, 安全性"
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 相依性屬性的安全性
相依性屬性通常應該視為公用屬性。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統在本質上會防止進行相依性屬性值的安全性保證。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="AccessSecurity"></a>   
## 包裝函式和相依性屬性的存取和安全性  
 通常，相依性屬性會與「包裝函式」[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性一起實作，該屬性會簡化對執行個體屬性的取得和設定。  不過，包裝函式實際上只是方便的方法，用於實作在與相依性屬性互動時所使用的基礎 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 靜態呼叫。  從另一個方式來想，公開為 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性的屬性，是剛好受到相依性屬性的支援，而非受到私用欄位的支援。  套用到包裝函式的安全性機制，與屬性系統行為和基礎相依性屬性的存取並不相同。  對包裝函式放置安全性要求只會防止使用這種方便的方法，卻無法防止呼叫 <xref:System.Windows.DependencyObject.GetValue%2A> 或 <xref:System.Windows.DependencyObject.SetValue%2A>。  同樣地，對包裝函式放置保護或私用存取層級並不會提供任何有效的安全性防護。  
  
 如果您在撰寫自己的相依性屬性，應該要將包裝函式和 <xref:System.Windows.DependencyProperty> 識別項欄位宣告為公用成員，這樣呼叫端才不會誤會該屬性的真實存取層級 \(因為其存放區會實作為相依性屬性\)。  
  
 對於自訂相依性屬性，您可以將屬性註冊為唯讀相依性屬性，這樣即能有效防止未持有屬性的 <xref:System.Windows.DependencyPropertyKey> 參考的任何人設定該屬性。  如需詳細資訊，請參閱[唯讀相依性屬性](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)。  
  
> [!NOTE]
>  宣告 <xref:System.Windows.DependencyProperty> 識別項欄位為私用並不會受到禁止，而且也認定可用於協助降低直接公開自訂類別的命名空間，但不應該以 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 語言定義會定義該存取層級的相同概念來將這類屬性視為「私用」，下節會詳細討論其原因。  
  
<a name="PropertySystemExposure"></a>   
## 相依性屬性的屬性系統公開  
 將 <xref:System.Windows.DependencyProperty> 宣告為公用以外的任何存取層級，通常並不好用而且很可能造成誤會。  該存取層級設定只能防止某人能夠取得宣告類別執行個體的參考。  但還是有數個屬性系統，會將傳回 <xref:System.Windows.DependencyProperty> 做為特定屬性是否存在於類別執行個體或衍生類別執行個體中的識別方式，而即使原始靜態識別項是宣告為非公用，仍然可以在 <xref:System.Windows.DependencyObject.SetValue%2A> 呼叫中使用這個識別項。  而 <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> 虛擬方法也會接收任何變更值的現有相依性屬性的資訊。  除此之外，對於具有區域設定值的執行個體的任何屬性，<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> 方法會傳回其識別項。  
  
### 驗證和安全性  
 藉由套用 <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> 的要求，並預期要求失敗會造成驗證失敗，即可防止屬性是在不足夠的安全性機制下設定的。  如果惡意呼叫端是在應用程式定義域內操作的話，這些呼叫端也可以隱藏透過 <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> 強制的設定值失效。  
  
## 請參閱  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)