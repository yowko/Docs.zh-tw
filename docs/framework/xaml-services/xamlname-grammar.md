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
# <a name="xamlname-grammar"></a><span data-ttu-id="afff1-102">XamlName 文法</span><span class="sxs-lookup"><span data-stu-id="afff1-102">XamlName Grammar</span></span>
<span data-ttu-id="afff1-103">XamlName 文法是特定的文法定義在 XAML 語言規格 [MS-XAML]，這為了方便起見在此處重現。</span><span class="sxs-lookup"><span data-stu-id="afff1-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="afff1-104">從 XAML 規格</span><span class="sxs-lookup"><span data-stu-id="afff1-104">From the XAML Specification</span></span>  
 <span data-ttu-id="afff1-105">[MS-XAML] 規格會定義以識別一組用於型別和屬性的合法符號識別碼 XamlName 文法。</span><span class="sxs-lookup"><span data-stu-id="afff1-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="afff1-106">字串值的類型必須符合下列文法 XamlName:</span><span class="sxs-lookup"><span data-stu-id="afff1-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="afff1-107">Unicode 字元資料庫中所定義，它會假設下列一般類別目錄值</span><span class="sxs-lookup"><span data-stu-id="afff1-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  
  
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
  
 <span data-ttu-id="afff1-108">XAML 會定義第二個文法，DottedXamlName 用於屬性和事件參考，完整也針對附加成員。</span><span class="sxs-lookup"><span data-stu-id="afff1-108">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="afff1-109">如需詳細資訊，請參閱<xref:System.Windows.DependencyProperty>和[XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="afff1-109">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
 <span data-ttu-id="afff1-110">字串值的類型必須符合下列文法 DottedXamlName:</span><span class="sxs-lookup"><span data-stu-id="afff1-110">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="afff1-111">備註</span><span class="sxs-lookup"><span data-stu-id="afff1-111">Remarks</span></span>  
 <span data-ttu-id="afff1-112">完整的規格，請參閱[ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="afff1-112">For the complete specification, see [\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
