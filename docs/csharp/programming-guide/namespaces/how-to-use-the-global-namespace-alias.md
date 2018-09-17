---
title: 如何：使用全域命名空間別名 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: c15271abb55cb29a200185e4b512a76a4913d848
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "44514614"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="81aac-102">如何：使用全域命名空間別名 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="81aac-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="81aac-103">成員可能會被具有相同名稱的另一個實體隱藏時，能夠存取全域[命名空間](../../../csharp/language-reference/keywords/namespace.md)中的成員就很有用。</span><span class="sxs-lookup"><span data-stu-id="81aac-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="81aac-104">例如，在下列程式碼中，`Console` 會解析成 `TestApp.Console`，而非 <xref:System> 命名空間中的 `Console` 類型。</span><span class="sxs-lookup"><span data-stu-id="81aac-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 <span data-ttu-id="81aac-105">使用 `System.Console` 仍會導致錯誤，因為 `TestApp.System` 類別隱藏了 `System` 命名空間：</span><span class="sxs-lookup"><span data-stu-id="81aac-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 <span data-ttu-id="81aac-106">不過，您可以使用 `global::System.Console` 來暫時解決這個錯誤，如下所示：</span><span class="sxs-lookup"><span data-stu-id="81aac-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 <span data-ttu-id="81aac-107">左邊的識別項是 `global` 時，搜尋正確的識別項會從全域命名空間開始。</span><span class="sxs-lookup"><span data-stu-id="81aac-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="81aac-108">例如，下列宣告將參考 `TestApp` 作為全域空間的成員。</span><span class="sxs-lookup"><span data-stu-id="81aac-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 <span data-ttu-id="81aac-109">很明顯地，不建議您建立自己的命名空間 `System`，而您也不太可能會遇到任何發生這種狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="81aac-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="81aac-110">不過，在較大型專案中，命名空間重複項很可能會以某種形式或其他形式出現。</span><span class="sxs-lookup"><span data-stu-id="81aac-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="81aac-111">在這些情況下，全域命名空間限定詞可確保您能夠指定根命名空間。</span><span class="sxs-lookup"><span data-stu-id="81aac-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81aac-112">範例</span><span class="sxs-lookup"><span data-stu-id="81aac-112">Example</span></span>  
 <span data-ttu-id="81aac-113">在此範例中，`System` 命名空間用來包含 `TestClass` 類別；因此，`global::System.Console` 必須用來參考 `System` 命名空間所隱藏的 `System.Console` 類別。</span><span class="sxs-lookup"><span data-stu-id="81aac-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="81aac-114">此外，`colAlias` 別名用來參考 `System.Collections` 命名空間；因此，<xref:System.Collections.Hashtable?displayProperty=nameWithType> 的執行個體會使用此別名而不是命名空間來建立。</span><span class="sxs-lookup"><span data-stu-id="81aac-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
<span data-ttu-id="81aac-115">**A 1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="81aac-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="81aac-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="81aac-116">See Also</span></span>

- [<span data-ttu-id="81aac-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="81aac-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="81aac-118">命名空間</span><span class="sxs-lookup"><span data-stu-id="81aac-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="81aac-119">.運算子</span><span class="sxs-lookup"><span data-stu-id="81aac-119">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="81aac-120">:: 運算子</span><span class="sxs-lookup"><span data-stu-id="81aac-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="81aac-121">extern</span><span class="sxs-lookup"><span data-stu-id="81aac-121">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
