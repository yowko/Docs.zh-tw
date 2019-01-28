---
title: 識別碼名稱
description: 了解 C# 程式設計語言中有效識別碼名稱的規則。
ms.date: 08/21/2018
ms.openlocfilehash: 2147b3846d4ba6d5471b81448489c6d716e3cd61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606948"
---
# <a name="identifier-names"></a><span data-ttu-id="6fa2e-103">識別碼名稱</span><span class="sxs-lookup"><span data-stu-id="6fa2e-103">Identifier names</span></span>

<span data-ttu-id="6fa2e-104">**識別碼**是您為類型 (類別、介面、結構、委派或列舉)、成員、變數或命名空間指派的名稱。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="6fa2e-105">有效的識別碼必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="6fa2e-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="6fa2e-106">識別碼必須以字母或 `_` 開頭。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="6fa2e-107">識別碼可能包含 Unicode 字母字元、十進位數字字元、Unicode 連接字元、 Unicode 組合字元或 Unicode 格式化字元。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="6fa2e-108">如需 Unicode 類別的詳細資訊，請參閱 [Unicode 類別資料庫](https://www.unicode.org/reports/tr44/)。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="6fa2e-109">您可以使用識別碼上的 `@` 前置詞，宣告與 C# 關鍵字符合的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="6fa2e-110">`@` 不含在識別碼名稱內。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="6fa2e-111">例如，`@if` 會宣告名為 `if` 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="6fa2e-112">這些[逐字識別碼](../../language-reference/tokens/verbatim.md)的主要目的是與使用其他語言宣告的識別碼達成互通性。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="6fa2e-113">如需有效識別碼的完整定義，請參閱 [C# 語言規格中的識別碼主題](../../../../_csharplang/spec/lexical-structure.md#identifiers)。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="6fa2e-114">命名規範</span><span class="sxs-lookup"><span data-stu-id="6fa2e-114">Naming conventions</span></span>

<span data-ttu-id="6fa2e-115">除了規則外，一些識別碼[命名慣例](../../../standard/design-guidelines/naming-guidelines.md)也用於 .NET API 中。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="6fa2e-116">依照慣例，C# 程式針對類型名稱、命名空間和所有公用成員使用 `PascalCase`。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="6fa2e-117">此外，常見慣例如下：</span><span class="sxs-lookup"><span data-stu-id="6fa2e-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="6fa2e-118">以大寫 `I` 開頭的介面名稱。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="6fa2e-119">以單字 `Attribute` 結尾的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="6fa2e-120">列舉類型會針對非旗標使用單一名詞，並針對旗標使用複數名詞。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="6fa2e-121">識別碼不應包含連續兩個 `_` 字元。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="6fa2e-122">這些名稱保留給編譯器產生的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6fa2e-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6fa2e-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6fa2e-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6fa2e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fa2e-124">See also</span></span>

- [<span data-ttu-id="6fa2e-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6fa2e-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6fa2e-126">C# 程式內部</span><span class="sxs-lookup"><span data-stu-id="6fa2e-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
- [<span data-ttu-id="6fa2e-127">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6fa2e-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="6fa2e-128">類別</span><span class="sxs-lookup"><span data-stu-id="6fa2e-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="6fa2e-129">結構</span><span class="sxs-lookup"><span data-stu-id="6fa2e-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="6fa2e-130">命名空間</span><span class="sxs-lookup"><span data-stu-id="6fa2e-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="6fa2e-131">介面</span><span class="sxs-lookup"><span data-stu-id="6fa2e-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="6fa2e-132">委派</span><span class="sxs-lookup"><span data-stu-id="6fa2e-132">Delegates</span></span>](../delegates/index.md)
