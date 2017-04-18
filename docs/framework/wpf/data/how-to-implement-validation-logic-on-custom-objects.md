---
title: "如何：對自訂物件實作驗證邏輯 | Microsoft Docs"
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
  - "檢查驗證錯誤 [WPF]"
  - "自訂物件 [WPF], 實作驗證邏輯"
  - "對自訂物件實作驗證邏輯 [WPF]"
  - "驗證錯誤 [WPF], 檢查"
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：對自訂物件實作驗證邏輯
本範例示範如何對自訂物件實作驗證邏輯，然後再繫結到該物件。  
  
## 範例  
 如果來源物件實作 <xref:System.ComponentModel.IDataErrorInfo>，您就可以在商務層提供驗證邏輯，如下列範例所示：  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 在下列範例中，文字方塊的文字屬性繫結至 `Person` 物件的 `Age` 屬性，此屬性已透過指定 `x:Key` `data` 之資源宣告，變成可以繫結的屬性。  <xref:System.Windows.Controls.DataErrorValidationRule> 會檢查 <xref:System.ComponentModel.IDataErrorInfo> 實作所引發的驗證錯誤。  
  
 [!code-xml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 除了使用 <xref:System.Windows.Controls.DataErrorValidationRule> 之外，您也可以將 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 屬性設定為 `true`。  
  
## 請參閱  
 <xref:System.Windows.Controls.ExceptionValidationRule>   
 [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)