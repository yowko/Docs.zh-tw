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
# <a name="xamlname-grammar"></a><span data-ttu-id="9d356-102">XamlName 文法</span><span class="sxs-lookup"><span data-stu-id="9d356-102">XamlName Grammar</span></span>

<span data-ttu-id="9d356-103">XamlName 文法是在 XAML 語言規格 [MS-CHAP] 中定義的特定文法，為了方便起見，我們會在這裡重現。</span><span class="sxs-lookup"><span data-stu-id="9d356-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="9d356-104">從 XAML 規格</span><span class="sxs-lookup"><span data-stu-id="9d356-104">From the XAML Specification</span></span>

<span data-ttu-id="9d356-105">[MS-CHAP] 規格會定義文法 XamlName，以識別用於類型和屬性的一組合法符號識別碼。</span><span class="sxs-lookup"><span data-stu-id="9d356-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="9d356-106">XamlName 型別的字串值必須符合下列文法：</span><span class="sxs-lookup"><span data-stu-id="9d356-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="9d356-107">這會假設 Unicode 字元資料庫中定義的下列一般分類值</span><span class="sxs-lookup"><span data-stu-id="9d356-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="9d356-108">Unicode 類別</span><span class="sxs-lookup"><span data-stu-id="9d356-108">Unicode category</span></span>   | <span data-ttu-id="9d356-109">描述</span><span class="sxs-lookup"><span data-stu-id="9d356-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="9d356-110">盧巴卡丹加文</span><span class="sxs-lookup"><span data-stu-id="9d356-110">Lu</span></span>                 | <span data-ttu-id="9d356-111">字母、大寫</span><span class="sxs-lookup"><span data-stu-id="9d356-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="9d356-112">Ll</span><span class="sxs-lookup"><span data-stu-id="9d356-112">Ll</span></span>                 | <span data-ttu-id="9d356-113">字母、小寫</span><span class="sxs-lookup"><span data-stu-id="9d356-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="9d356-114">Lt</span><span class="sxs-lookup"><span data-stu-id="9d356-114">Lt</span></span>                 | <span data-ttu-id="9d356-115">字母、字首大寫</span><span class="sxs-lookup"><span data-stu-id="9d356-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="9d356-116">Lm</span><span class="sxs-lookup"><span data-stu-id="9d356-116">Lm</span></span>                 | <span data-ttu-id="9d356-117">字母、修飾詞</span><span class="sxs-lookup"><span data-stu-id="9d356-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="9d356-118">Lo</span><span class="sxs-lookup"><span data-stu-id="9d356-118">Lo</span></span>                 | <span data-ttu-id="9d356-119">字母、其他</span><span class="sxs-lookup"><span data-stu-id="9d356-119">Letter, Other</span></span>                 |
| <span data-ttu-id="9d356-120">Mn</span><span class="sxs-lookup"><span data-stu-id="9d356-120">Mn</span></span>                 | <span data-ttu-id="9d356-121">標記、非間距</span><span class="sxs-lookup"><span data-stu-id="9d356-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="9d356-122">Mc</span><span class="sxs-lookup"><span data-stu-id="9d356-122">Mc</span></span>                 | <span data-ttu-id="9d356-123">記號，間距組合</span><span class="sxs-lookup"><span data-stu-id="9d356-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="9d356-124">Nd</span><span class="sxs-lookup"><span data-stu-id="9d356-124">Nd</span></span>                 | <span data-ttu-id="9d356-125">數位、十進位</span><span class="sxs-lookup"><span data-stu-id="9d356-125">Number, Decimal</span></span>               |
| <span data-ttu-id="9d356-126">Nl</span><span class="sxs-lookup"><span data-stu-id="9d356-126">Nl</span></span>                 | <span data-ttu-id="9d356-127">數字，字母</span><span class="sxs-lookup"><span data-stu-id="9d356-127">Number, Letter</span></span>                |

<span data-ttu-id="9d356-128">XAML 會定義第二個文法 DottedXamlName，它是用於屬性和事件限定參考，也會用於附加的成員。</span><span class="sxs-lookup"><span data-stu-id="9d356-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="9d356-129">如需詳細資訊，請參閱 <xref:System.Windows.DependencyProperty> 和 [XAML 總覽 (WPF) ](../fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9d356-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="9d356-130">DottedXamlName 型別的字串值必須符合下列文法：</span><span class="sxs-lookup"><span data-stu-id="9d356-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="9d356-131">備註</span><span class="sxs-lookup"><span data-stu-id="9d356-131">Remarks</span></span>

<span data-ttu-id="9d356-132">如需完整的規格，請參閱[ \[ MS \] XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="9d356-132">For the complete specification, see [\[MS-XAML\]](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
