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
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071826"
---
# <a name="xamlname-grammar"></a>XamlName 文法

XamlName 語法是在 XAML 語言規範 [MS-XAML] 中定義的一種特定語法,為了方便起見,此處進行了複製。

## <a name="from-the-xaml-specification"></a>從 XAML 規範

[MS-XAML] 規範定義語法 XamlName 來識別用於類型和屬性的法律符號識別符集。

XamlName 類型的字串值必須符合以下語法:

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

它假定 Unicode 字元資料庫中定義的一般類別值

| Unicode 類別   | 描述                   |
|--------------------|-------------------------------|
| 盧巴卡丹加文                 | 字母、大寫             |
| Ll                 | 字母、小寫             |
| Lt                 | 字母、字首大寫             |
| Lm                 | 字母、修飾詞              |
| Lo                 | 字母、其他                 |
| Mn                 | 標記,非間距             |
| Mc                 | 記號，間距組合       |
| Nd                 | 數位,十進位               |
| Nl                 | 數字，字母                |

XAML 定義了第二個語法,即 DottedXamlName,用於屬性和事件限定引用,也用於附加成員。 有關詳細資訊,請參閱<xref:System.Windows.DependencyProperty>和[XAML 概述 (WPF)。](../fundamentals/xaml.md)

類型為 DottedXamlName 的字串值必須符合以下語法:

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>備註

有關完整的規範,請參閱[\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。
