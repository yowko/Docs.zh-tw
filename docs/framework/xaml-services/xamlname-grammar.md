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
# <a name="xamlname-grammar"></a><span data-ttu-id="70057-102">XamlName 文法</span><span class="sxs-lookup"><span data-stu-id="70057-102">XamlName Grammar</span></span>
<span data-ttu-id="70057-103">XamlName 文法是以 XAML 語言規格 [MS-XAML] 定義的特定文法，為了方便起見，會在這裡重現。</span><span class="sxs-lookup"><span data-stu-id="70057-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="70057-104">從 XAML 規格</span><span class="sxs-lookup"><span data-stu-id="70057-104">From the XAML Specification</span></span>  
 <span data-ttu-id="70057-105">[MS-XAML] 規格會定義文法 XamlName，以識別用於類型和屬性的一組合法符號識別碼。</span><span class="sxs-lookup"><span data-stu-id="70057-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="70057-106">XamlName 類型的字串值必須符合下列文法：</span><span class="sxs-lookup"><span data-stu-id="70057-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="70057-107">這會假設 Unicode 字元資料庫中所定義的下列一般分類值</span><span class="sxs-lookup"><span data-stu-id="70057-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="70057-108">Unicode 分類</span><span class="sxs-lookup"><span data-stu-id="70057-108">Unicode category</span></span>   | <span data-ttu-id="70057-109">描述</span><span class="sxs-lookup"><span data-stu-id="70057-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="70057-110">Lu</span><span class="sxs-lookup"><span data-stu-id="70057-110">Lu</span></span>                 | <span data-ttu-id="70057-111">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="70057-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="70057-112">Ll</span><span class="sxs-lookup"><span data-stu-id="70057-112">Ll</span></span>                 | <span data-ttu-id="70057-113">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="70057-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="70057-114">Lt</span><span class="sxs-lookup"><span data-stu-id="70057-114">Lt</span></span>                 | <span data-ttu-id="70057-115">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="70057-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="70057-116">Lm</span><span class="sxs-lookup"><span data-stu-id="70057-116">Lm</span></span>                 | <span data-ttu-id="70057-117">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="70057-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="70057-118">Lo</span><span class="sxs-lookup"><span data-stu-id="70057-118">Lo</span></span>                 | <span data-ttu-id="70057-119">字母、其他</span><span class="sxs-lookup"><span data-stu-id="70057-119">Letter, Other</span></span>                 |
| <span data-ttu-id="70057-120">Mn</span><span class="sxs-lookup"><span data-stu-id="70057-120">Mn</span></span>                 | <span data-ttu-id="70057-121">標記、非間距</span><span class="sxs-lookup"><span data-stu-id="70057-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="70057-122">Mc</span><span class="sxs-lookup"><span data-stu-id="70057-122">Mc</span></span>                 | <span data-ttu-id="70057-123">記號，間距組合</span><span class="sxs-lookup"><span data-stu-id="70057-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="70057-124">Nd</span><span class="sxs-lookup"><span data-stu-id="70057-124">Nd</span></span>                 | <span data-ttu-id="70057-125">數位、十進位</span><span class="sxs-lookup"><span data-stu-id="70057-125">Number, Decimal</span></span>               |
| <span data-ttu-id="70057-126">Nl</span><span class="sxs-lookup"><span data-stu-id="70057-126">Nl</span></span>                 | <span data-ttu-id="70057-127">數字，字母</span><span class="sxs-lookup"><span data-stu-id="70057-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="70057-128">XAML 會定義第二個文法 DottedXamlName，用於屬性和事件限定的參考，也會用於附加的成員。</span><span class="sxs-lookup"><span data-stu-id="70057-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="70057-129">如需詳細資訊， <xref:System.Windows.DependencyProperty>請參閱和[XAML 總覽（WPF）](../wpf/advanced/xaml-overview-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="70057-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
 <span data-ttu-id="70057-130">DottedXamlName 類型的字串值必須符合下列文法：</span><span class="sxs-lookup"><span data-stu-id="70057-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="70057-131">備註</span><span class="sxs-lookup"><span data-stu-id="70057-131">Remarks</span></span>  
 <span data-ttu-id="70057-132">如需完整的規格，請參閱[ \[MS\]-XAML](https://go.microsoft.com/fwlink/?LinkId=114525)。</span><span class="sxs-lookup"><span data-stu-id="70057-132">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
