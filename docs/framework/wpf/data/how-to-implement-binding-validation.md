---
title: "如何：實作繫結驗證 | Microsoft Docs"
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
  - "繫結, 驗證"
  - "資料繫結, 繫結驗證"
  - "繫結驗證"
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：實作繫結驗證
本範例顯示如何使用 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和樣式觸發程序，以提供視覺化回應，依據自訂驗證規則以在輸入無效值時通知使用者。  
  
## 範例  
 下列範例中 <xref:System.Windows.Controls.TextBox> 的文字內容，是繫結到名為 `ods` 的[繫結來源](GTMT)物件的 `Age` 屬性 \(型別 int\)。  繫結是設為使用名為 `AgeRangeRule` 的驗證規則，因此如果使用者輸入非數值字元或小於 21 或大於 130 的值，文字方塊旁邊會出現紅色驚嘆號，並在使用者移動滑鼠到文字方塊上方時出現具有錯誤訊息的工具提示。  
  
 [!code-xml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 下列範例顯示 `AgeRangeRule` 的實作，該規則繼承自 <xref:System.Windows.Controls.ValidationRule> 並會覆寫 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法。  Int32.Parse\(\) 方法會針對值呼叫，以確認當中沒有包含任何無效的字元。  <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法傳回的 <xref:System.Windows.Controls.ValidationResult> 會依據剖析期間是否有攔截到例外狀況以及年齡值是否超出上下限，以指出值是否有效。  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 下列範例顯示的自訂 <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` 會建立紅色驚嘆號，告知使用者發生驗證錯誤。  控制項樣板是用於重新定義控制項的外觀。  
  
 [!code-xml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 如下列範例所示，顯示錯誤訊息的 <xref:System.Windows.Controls.ToolTip> 是使用名為 `textBoxInError` 的樣式建立的。  如果 <xref:System.Windows.Controls.Validation.HasError%2A> 的值為 `true`，觸發程序會將目前 <xref:System.Windows.Controls.TextBox> 的工具提示設定為其第一個驗證錯誤。  <xref:System.Windows.Data.Binding.RelativeSource%2A> 設定為 <xref:System.Windows.Data.RelativeSourceMode>，代表目前的項目。  
  
 [!code-xml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 如需完整範例，請參閱[繫結驗證範例](http://go.microsoft.com/fwlink/?LinkID=159972) \(英文\)。  
  
 請注意，如果您沒有提供自訂 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>，就會在發生驗證錯誤時出現預設錯誤樣板，提供使用者視覺化的回應。  如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)中的＜資料驗證＞。  除此之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的內建驗證規則，會攔截繫結來源屬性更新期間所擲回的例外狀況。  如需詳細資訊，請參閱 <xref:System.Windows.Controls.ExceptionValidationRule>。  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)