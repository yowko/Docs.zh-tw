---
title: this 關鍵字 (C# 參考)
description: this 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 52e7fce0ebeeccfbf5f56dbbcade9fae2890dfe1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130810"
---
# <a name="this-c-reference"></a><span data-ttu-id="b8d68-103">this (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b8d68-103">this (C# Reference)</span></span>

<span data-ttu-id="b8d68-104">`this` 關鍵字指的是類別的目前執行個體，也用作擴充方法第一個參數的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b8d68-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>

> [!NOTE]
> <span data-ttu-id="b8d68-105">本文討論如何搭配使用 `this` 與類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8d68-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="b8d68-106">如需其在擴充方法中之用法的詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="b8d68-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="b8d68-107">下列是 `this` 的常見用法：</span><span class="sxs-lookup"><span data-stu-id="b8d68-107">The following are common uses of `this`:</span></span>

- <span data-ttu-id="b8d68-108">限定透過類似名稱所隱藏的成員，例如︰</span><span class="sxs-lookup"><span data-stu-id="b8d68-108">To qualify members hidden by similar names, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- <span data-ttu-id="b8d68-109">傳遞物件作為其他方法的參數，例如：</span><span class="sxs-lookup"><span data-stu-id="b8d68-109">To pass an object as a parameter to other methods, for example:</span></span>

  ```csharp
  CalcTax(this);
  ```

- <span data-ttu-id="b8d68-110">宣告索引子，例如︰</span><span class="sxs-lookup"><span data-stu-id="b8d68-110">To declare indexers, for example:</span></span>

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

<span data-ttu-id="b8d68-111">靜態成員函式存在於類別層級，而不是物件的一部分，因此沒有 `this` 指標。</span><span class="sxs-lookup"><span data-stu-id="b8d68-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="b8d68-112">在靜態方法中參照 `this` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8d68-112">It is an error to refer to `this` in a static method.</span></span>

## <a name="example"></a><span data-ttu-id="b8d68-113">範例</span><span class="sxs-lookup"><span data-stu-id="b8d68-113">Example</span></span>

<span data-ttu-id="b8d68-114">在此範例中，`this` 是用來限定 `Employee` 類別成員 `name` 和 `alias`，而這些是透過類似的名稱進行隱藏。</span><span class="sxs-lookup"><span data-stu-id="b8d68-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="b8d68-115">它也會用來將物件傳遞給屬於另一個類別的 `CalcTax` 方法。</span><span class="sxs-lookup"><span data-stu-id="b8d68-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="b8d68-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b8d68-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b8d68-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d68-117">See also</span></span>

- [<span data-ttu-id="b8d68-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b8d68-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b8d68-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b8d68-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b8d68-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b8d68-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b8d68-121">base</span><span class="sxs-lookup"><span data-stu-id="b8d68-121">base</span></span>](base.md)
- [<span data-ttu-id="b8d68-122">方法</span><span class="sxs-lookup"><span data-stu-id="b8d68-122">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
