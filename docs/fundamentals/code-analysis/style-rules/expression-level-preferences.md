---
title: 運算式層級喜好設定
description: 瞭解運算式層級喜好設定的程式碼分析語言規則
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 9933111b1ed76166e5ae86e9bc1a2332c3c77c81
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "96586551"
---
# <a name="expression-level-preferences"></a><span data-ttu-id="8e692-103">運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="8e692-103">Expression-level preferences</span></span>

## <a name="net-expression-level-preferences"></a><span data-ttu-id="8e692-104">.NET 運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="8e692-104">.NET expression-level preferences</span></span>

<span data-ttu-id="8e692-105">本章節中的樣式規則涉及 c # 和 Visual Basic 通用的下列運算式層級喜好設定：</span><span class="sxs-lookup"><span data-stu-id="8e692-105">The style rules in this section concern the following expression-level preferences that are common to C# and Visual Basic:</span></span>

- [<span data-ttu-id="8e692-106">將遺漏的案例新增至 switch 語句 (IDE0010) </span><span class="sxs-lookup"><span data-stu-id="8e692-106">Add missing cases to switch statement (IDE0010)</span></span>](ide0010.md)
- [<span data-ttu-id="8e692-107">使用物件初始化運算式 (IDE0017) </span><span class="sxs-lookup"><span data-stu-id="8e692-107">Use object initializers (IDE0017)</span></span>](ide0017.md)
- [<span data-ttu-id="8e692-108">使用集合初始化運算式 (IDE0028) </span><span class="sxs-lookup"><span data-stu-id="8e692-108">Use collection initializers (IDE0028)</span></span>](ide0028.md)
- [<span data-ttu-id="8e692-109">使用 auto 屬性 (IDE0032) </span><span class="sxs-lookup"><span data-stu-id="8e692-109">Use auto property (IDE0032)</span></span>](ide0032.md)
- [<span data-ttu-id="8e692-110">使用明確提供的元組名稱 (IDE0033) </span><span class="sxs-lookup"><span data-stu-id="8e692-110">Use explicitly provided tuple name (IDE0033)</span></span>](ide0033.md)
- [<span data-ttu-id="8e692-111">使用推斷的成員名稱 (IDE0037) </span><span class="sxs-lookup"><span data-stu-id="8e692-111">Use inferred member name (IDE0037)</span></span>](ide0037.md)
- [<span data-ttu-id="8e692-112">使用條件運算式指派 (IDE0045) </span><span class="sxs-lookup"><span data-stu-id="8e692-112">Use conditional expression for assignment (IDE0045)</span></span>](ide0045.md)
- [<span data-ttu-id="8e692-113">將條件運算式用於 return (IDE0046) </span><span class="sxs-lookup"><span data-stu-id="8e692-113">Use conditional expression for return (IDE0046)</span></span>](ide0046.md)
- [<span data-ttu-id="8e692-114">將匿名型別轉換為元組 (IDE0050) </span><span class="sxs-lookup"><span data-stu-id="8e692-114">Convert anonymous type to tuple (IDE0050)</span></span>](ide0050.md)
- [<span data-ttu-id="8e692-115">使用複合指派 (IDE0054 和 IDE0074) </span><span class="sxs-lookup"><span data-stu-id="8e692-115">Use compound assignment (IDE0054 and IDE0074)</span></span>](ide0054-ide0074.md)
- [<span data-ttu-id="8e692-116">使用 ' IDE0070) 組合 ' (</span><span class="sxs-lookup"><span data-stu-id="8e692-116">Use 'System.HashCode.Combine' (IDE0070)</span></span>](ide0070.md)
- [<span data-ttu-id="8e692-117">簡化 IDE0071) 的插補 (</span><span class="sxs-lookup"><span data-stu-id="8e692-117">Simplify interpolation (IDE0071)</span></span>](ide0071.md)
- [<span data-ttu-id="8e692-118">簡化條件運算式 (IDE0075) </span><span class="sxs-lookup"><span data-stu-id="8e692-118">Simplify conditional expression (IDE0075)</span></span>](ide0075.md)
- [<span data-ttu-id="8e692-119">將 ' typeof ' 轉換成 ' nameof ' (IDE0082) </span><span class="sxs-lookup"><span data-stu-id="8e692-119">Convert 'typeof' to 'nameof' (IDE0082)</span></span>](ide0082.md)

## <a name="c-expression-level-preferences"></a><span data-ttu-id="8e692-120">C# 運算式層級喜好設定</span><span class="sxs-lookup"><span data-stu-id="8e692-120">C# expression-level preferences</span></span>

<span data-ttu-id="8e692-121">本章節中的樣式規則涉及下列 c # 特有的運算式層級喜好設定：</span><span class="sxs-lookup"><span data-stu-id="8e692-121">The style rules in this section concern the following expression-level preferences that are specific to C#:</span></span>

- [<span data-ttu-id="8e692-122">內嵌變數宣告 (IDE0018) </span><span class="sxs-lookup"><span data-stu-id="8e692-122">Inline variable declaration (IDE0018)</span></span>](ide0018.md)
- [<span data-ttu-id="8e692-123">簡化 ' default ' 運算式 (IDE0034) </span><span class="sxs-lookup"><span data-stu-id="8e692-123">Simplify 'default' expression (IDE0034)</span></span>](ide0034.md)
- [<span data-ttu-id="8e692-124">使用區域函式，而不是 lambda (IDE0039) </span><span class="sxs-lookup"><span data-stu-id="8e692-124">Use local function instead of lambda (IDE0039)</span></span>](ide0039.md)
- [<span data-ttu-id="8e692-125">解構變數宣告 (IDE0042) </span><span class="sxs-lookup"><span data-stu-id="8e692-125">Deconstruct variable declaration (IDE0042)</span></span>](ide0042.md)
- [<span data-ttu-id="8e692-126">使用索引運算子 (IDE0056) </span><span class="sxs-lookup"><span data-stu-id="8e692-126">Use index operator (IDE0056)</span></span>](ide0056.md)
- [<span data-ttu-id="8e692-127">使用範圍運算子 (IDE0057) </span><span class="sxs-lookup"><span data-stu-id="8e692-127">Use range operator (IDE0057)</span></span>](ide0057.md)
- [<span data-ttu-id="8e692-128">將遺漏的案例新增至 switch 運算式 (IDE0072) </span><span class="sxs-lookup"><span data-stu-id="8e692-128">Add missing cases to switch expression (IDE0072)</span></span>](ide0072.md)
- [<span data-ttu-id="8e692-129">簡化 ' new ' 運算式 (IDE0090) </span><span class="sxs-lookup"><span data-stu-id="8e692-129">Simplify 'new' expression (IDE0090)</span></span>](ide0090.md)

## <a name="see-also"></a><span data-ttu-id="8e692-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e692-130">See also</span></span>

- [<span data-ttu-id="8e692-131">程式碼樣式規則參考</span><span class="sxs-lookup"><span data-stu-id="8e692-131">Code style rules reference</span></span>](index.md)
- [<span data-ttu-id="8e692-132">程式碼樣式語言規則</span><span class="sxs-lookup"><span data-stu-id="8e692-132">Code style language rules</span></span>](language-rules.md)
