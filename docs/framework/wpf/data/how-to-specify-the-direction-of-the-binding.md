---
title: "如何：指定繫結的方向 | Microsoft Docs"
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
  - "繫結方向"
  - "資料繫結, 繫結方向"
  - "繫結方向"
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 如何：指定繫結的方向
本範例顯示如何指定繫結只更新[繫結目標](GTMT) \(目標\) 屬性、[繫結來源](GTMT) \(來源\) 屬性，或同時更新目標屬性與來源屬性。  
  
## 範例  
 您可使用 <xref:System.Windows.Data.Binding.Mode%2A> 屬性指定繫結的方向。  下列列舉型別清單顯示繫結更新的可用選項：  
  
-   <xref:System.Windows.Data.BindingMode>：當目標屬性或來源屬性變更時，會更新目標屬性或來源屬性。  
  
-   <xref:System.Windows.Data.BindingMode>：當來源屬性變更時，才會更新目標屬性。  
  
-   <xref:System.Windows.Data.BindingMode>：當應用程式啟動時，或者當 <xref:System.Windows.FrameworkElement.DataContext%2A> 歷經變更時，才會更新目標屬性。  
  
-   <xref:System.Windows.Data.BindingMode>：當目標屬性變更時，會更新來源屬性。  
  
-   <xref:System.Windows.Data.BindingMode>：會導致使用目標屬性的預設 <xref:System.Windows.Data.Binding.Mode%2A> 值。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Data.BindingMode> 列舉。  
  
 下列範例顯示如何設定 <xref:System.Windows.Data.Binding.Mode%2A> 屬性。  
  
 [!code-xml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 若要偵測來源變更 \(適用於 <xref:System.Windows.Data.BindingMode> 和 <xref:System.Windows.Data.BindingMode> 繫結\)，來源必須實作適合的屬性變更通知機制，例如 <xref:System.ComponentModel.INotifyPropertyChanged>。  請參閱 [實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)，以取得 <xref:System.ComponentModel.INotifyPropertyChanged> 實作的範例。  
  
 對於 <xref:System.Windows.Data.BindingMode> 或 <xref:System.Windows.Data.BindingMode> 繫結，您可以設定 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 屬性，藉以控制來源更新的時機。  如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
## 請參閱  
 <xref:System.Windows.Data.Binding>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)