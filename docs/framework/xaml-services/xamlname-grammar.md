---
title: "XamlName 文法 | Microsoft Docs"
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
  - "DottedXamlName 文法 [XAML 服務]"
  - "文法 [XAML 服務]，DottedXamlName"
  - "文法 [XAML 服務]，XamlName"
  - "XAML 中的名稱 [XAML 服務]"
  - "XamlName 文法 [XAML 服務]"
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# XamlName 文法
XamlName 文法是 XAML 語言規格 \[MS\-XAML\] 中定義的特定文法，在此為了便利而將其重現。  
  
## 來自 XAML 規格  
 \[MS\-XAML\] 規格定義 XamlName 文法來識別用於型別和屬性的一組合法符號識別項。  
  
 屬於型別 XamlName 的字串值必須符合下列文法：  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
  
```  
  
 其中採用了 Unicode 字元資料庫中定義的一般分類值如下  
  
```  
  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML 定義有第二個文法 DottedXamlName，以用於屬性、事件限定參考以及附加成員。  如需詳細資訊，請參閱<xref:System.Windows.DependencyProperty>與[XAML 概觀 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
 屬於型別 DottedXamlName 的字串值必須符合下列文法：  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## 備註  
 如需完整規格，請參閱 [\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525) \(英文\)。