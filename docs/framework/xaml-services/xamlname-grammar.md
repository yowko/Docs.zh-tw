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
ms.openlocfilehash: 837a18ca18d0c634dfa5cc133aa013919cfb9d96
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053891"
---
# <a name="xamlname-grammar"></a>XamlName 文法
XamlName 文法是以 XAML 語言規格 [MS-XAML] 定義的特定文法，為了方便起見，會在這裡重現。  
  
## <a name="from-the-xaml-specification"></a>從 XAML 規格  
 [MS-XAML] 規格會定義文法 XamlName，以識別用於類型和屬性的一組合法符號識別碼。  
  
 XamlName 類型的字串值必須符合下列文法：  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 這會假設 Unicode 字元資料庫中所定義的下列一般分類值  

| Unicode 分類   | 描述                   |
|--------------------|-------------------------------|
| Lu                 | 字母、大寫             |
| Ll                 | 字母、小寫             |
| Lt                 | 字母、字首大寫             |
| Lm                 | 字母、修飾詞              |
| Lo                 | 字母、其他                 |
| Mn                 | 標記、非間距             |
| Mc                 | 記號，間距組合       |
| Nd                 | 數位、十進位               |
| Nl                 | 數字，字母                |
 
 XAML 會定義第二個文法 DottedXamlName，用於屬性和事件限定的參考，也會用於附加的成員。 如需詳細資訊， <xref:System.Windows.DependencyProperty>請參閱和[XAML 總覽（WPF）](../wpf/advanced/xaml-overview-wpf.md)。  
  
 DottedXamlName 類型的字串值必須符合下列文法：  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>備註  
 如需完整的規格，請參閱[ \[MS\]-XAML](https://go.microsoft.com/fwlink/?LinkId=114525)。
