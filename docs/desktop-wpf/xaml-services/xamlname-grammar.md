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
# <a name="xamlname-grammar"></a><span data-ttu-id="2f86c-102">XamlName 文法</span><span class="sxs-lookup"><span data-stu-id="2f86c-102">XamlName Grammar</span></span>

<span data-ttu-id="2f86c-103">XamlName 語法是在 XAML 語言規範 [MS-XAML] 中定義的一種特定語法,為了方便起見,此處進行了複製。</span><span class="sxs-lookup"><span data-stu-id="2f86c-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="2f86c-104">從 XAML 規範</span><span class="sxs-lookup"><span data-stu-id="2f86c-104">From the XAML Specification</span></span>

<span data-ttu-id="2f86c-105">[MS-XAML] 規範定義語法 XamlName 來識別用於類型和屬性的法律符號識別符集。</span><span class="sxs-lookup"><span data-stu-id="2f86c-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="2f86c-106">XamlName 類型的字串值必須符合以下語法:</span><span class="sxs-lookup"><span data-stu-id="2f86c-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="2f86c-107">它假定 Unicode 字元資料庫中定義的一般類別值</span><span class="sxs-lookup"><span data-stu-id="2f86c-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="2f86c-108">Unicode 類別</span><span class="sxs-lookup"><span data-stu-id="2f86c-108">Unicode category</span></span>   | <span data-ttu-id="2f86c-109">描述</span><span class="sxs-lookup"><span data-stu-id="2f86c-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="2f86c-110">盧巴卡丹加文</span><span class="sxs-lookup"><span data-stu-id="2f86c-110">Lu</span></span>                 | <span data-ttu-id="2f86c-111">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="2f86c-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="2f86c-112">Ll</span><span class="sxs-lookup"><span data-stu-id="2f86c-112">Ll</span></span>                 | <span data-ttu-id="2f86c-113">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="2f86c-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="2f86c-114">Lt</span><span class="sxs-lookup"><span data-stu-id="2f86c-114">Lt</span></span>                 | <span data-ttu-id="2f86c-115">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="2f86c-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="2f86c-116">Lm</span><span class="sxs-lookup"><span data-stu-id="2f86c-116">Lm</span></span>                 | <span data-ttu-id="2f86c-117">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="2f86c-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="2f86c-118">Lo</span><span class="sxs-lookup"><span data-stu-id="2f86c-118">Lo</span></span>                 | <span data-ttu-id="2f86c-119">字母、其他</span><span class="sxs-lookup"><span data-stu-id="2f86c-119">Letter, Other</span></span>                 |
| <span data-ttu-id="2f86c-120">Mn</span><span class="sxs-lookup"><span data-stu-id="2f86c-120">Mn</span></span>                 | <span data-ttu-id="2f86c-121">標記,非間距</span><span class="sxs-lookup"><span data-stu-id="2f86c-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="2f86c-122">Mc</span><span class="sxs-lookup"><span data-stu-id="2f86c-122">Mc</span></span>                 | <span data-ttu-id="2f86c-123">記號，間距組合</span><span class="sxs-lookup"><span data-stu-id="2f86c-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="2f86c-124">Nd</span><span class="sxs-lookup"><span data-stu-id="2f86c-124">Nd</span></span>                 | <span data-ttu-id="2f86c-125">數位,十進位</span><span class="sxs-lookup"><span data-stu-id="2f86c-125">Number, Decimal</span></span>               |
| <span data-ttu-id="2f86c-126">Nl</span><span class="sxs-lookup"><span data-stu-id="2f86c-126">Nl</span></span>                 | <span data-ttu-id="2f86c-127">數字，字母</span><span class="sxs-lookup"><span data-stu-id="2f86c-127">Number, Letter</span></span>                |

<span data-ttu-id="2f86c-128">XAML 定義了第二個語法,即 DottedXamlName,用於屬性和事件限定引用,也用於附加成員。</span><span class="sxs-lookup"><span data-stu-id="2f86c-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="2f86c-129">有關詳細資訊,請參閱<xref:System.Windows.DependencyProperty>和[XAML 概述 (WPF)。](../fundamentals/xaml.md)</span><span class="sxs-lookup"><span data-stu-id="2f86c-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="2f86c-130">類型為 DottedXamlName 的字串值必須符合以下語法:</span><span class="sxs-lookup"><span data-stu-id="2f86c-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="2f86c-131">備註</span><span class="sxs-lookup"><span data-stu-id="2f86c-131">Remarks</span></span>

<span data-ttu-id="2f86c-132">有關完整的規範,請參閱[\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="2f86c-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
