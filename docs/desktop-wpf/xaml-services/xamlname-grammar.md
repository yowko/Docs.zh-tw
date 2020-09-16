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
ms.openlocfilehash: ceb027938b6d4313babbe02949e0b6dd5ee85589
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556690"
---
# <a name="xamlname-grammar"></a>XamlName 文法

XamlName 文法是在 XAML 語言規格 [MS-CHAP] 中定義的特定文法，為了方便起見，我們會在這裡重現。

## <a name="from-the-xaml-specification"></a>從 XAML 規格

[MS-CHAP] 規格會定義文法 XamlName，以識別用於類型和屬性的一組合法符號識別碼。

XamlName 型別的字串值必須符合下列文法：

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

這會假設 Unicode 字元資料庫中定義的下列一般分類值

| Unicode 類別   | 描述                   |
|--------------------|-------------------------------|
| 盧巴卡丹加文                 | 字母、大寫             |
| Ll                 | 字母、小寫             |
| Lt                 | 字母、字首大寫             |
| Lm                 | 字母、修飾詞              |
| Lo                 | 字母、其他                 |
| Mn                 | 標記、非間距             |
| Mc                 | 記號，間距組合       |
| Nd                 | 數位、十進位               |
| Nl                 | 數字，字母                |

XAML 會定義第二個文法 DottedXamlName，它是用於屬性和事件限定參考，也會用於附加的成員。 如需詳細資訊，請參閱 <xref:System.Windows.DependencyProperty> 和 [XAML 總覽 (WPF) ](../fundamentals/xaml.md)。

DottedXamlName 型別的字串值必須符合下列文法：

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>備註

如需完整的規格，請參閱[ \[ MS \] XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10))。
