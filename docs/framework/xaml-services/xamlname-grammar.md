---
title: XamlName 文法
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 32fd7b7b952ebbc853e41c0a8276d1ab487e619f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561887"
---
# <a name="xamlname-grammar"></a>XamlName 文法
XamlName 文法是特定的文法定義在 XAML 語言規格 [MS-XAML]，這為了方便起見在此處重現。  
  
## <a name="from-the-xaml-specification"></a>從 XAML 規格  
 [MS-XAML] 規格會定義以識別一組用於型別和屬性的合法符號識別碼 XamlName 文法。  
  
 字串值的類型必須符合下列文法 XamlName:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Unicode 字元資料庫中所定義，它會假設下列一般類別目錄值  
  
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
  
 XAML 會定義第二個文法，DottedXamlName 用於屬性和事件參考，完整也針對附加成員。 如需詳細資訊，請參閱<xref:System.Windows.DependencyProperty>和[XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
 字串值的類型必須符合下列文法 DottedXamlName:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>備註  
 完整的規格，請參閱[ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)。
