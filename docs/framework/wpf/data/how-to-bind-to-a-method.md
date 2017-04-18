---
title: "如何：繫結至方法 | Microsoft Docs"
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
  - "繫結, 至方法"
  - "類別, ObjectDataProvider"
  - "資料繫結, 使用 ObjectDataProvider 繫結至方法"
  - "方法, 繫結至"
  - "ObjectDataProvider 類別"
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：繫結至方法
下列範例顯示如何使用 <xref:System.Windows.Data.ObjectDataProvider> 繫結至方法。  
  
## 範例  
 在此範例中，`TemperatureScale` 為具有方法 `ConvertTemp` 的類別，它採用兩個參數 \(一個屬於 `double` 型別，另一個屬於 `enum` 型別 `TempType)`，並會將指定值從某個溫標轉換為另一個溫標。  在下列範例中，將使用 <xref:System.Windows.Data.ObjectDataProvider> 來具現化 \(Instantiate\) `TemperatureScale` 物件。  `ConvertTemp` 方法可透過兩個指定的參數來呼叫。  
  
 [!code-xml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 現在此方法已提供為資源，您可以繫結至其結果。  在下列範例中，<xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性與 <xref:System.Windows.Controls.ComboBox> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 會繫結至方法的兩個參數。  這可讓使用者指定要轉換的溫度以及要轉換的來源溫標。  請注意，<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> 會設為 `true`，因為我們是繫結至 <xref:System.Windows.Data.ObjectDataProvider> 執行個體的 <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> 屬性，而非 <xref:System.Windows.Data.ObjectDataProvider> 所包裝之物件 \(`TemperatureScale` 物件\) 的屬性。  
  
 當使用者修改 <xref:System.Windows.Controls.TextBox> 的內容或 <xref:System.Windows.Controls.ComboBox> 的選取項目時，即會更新最後一個 <xref:System.Windows.Controls.Label> 的 <xref:System.Windows.Controls.ContentControl.Content%2A>。  
  
 [!code-xml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 轉換器 `DoubleToString` 會採用雙精度浮點數，並依照 <xref:System.Windows.Data.IValueConverter.Convert%2A> 方向 \(從[繫結來源](GTMT)至[繫結目標](GTMT)，其為 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性\) 將其轉換成字串，並依照 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方向將 `string` 轉換成 `double`。  
  
 `InvalidationCharacterRule` 是一個可檢查字元是否有效的 <xref:System.Windows.Controls.ValidationRule>。  預設的錯誤範本為紅色框線圍著 <xref:System.Windows.Controls.TextBox>，當輸入值不是雙精度浮點數值時便會顯示，以告知使用者。  
  
## 請參閱  
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [繫結至列舉](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)