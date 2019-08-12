---
title: 作法：使用全域命名空間別名 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796286"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="22547-102">作法：使用全域命名空間別名 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="22547-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="22547-103">成員可能會被具有相同名稱的另一個實體隱藏時，能夠存取全域[命名空間](../../../csharp/language-reference/keywords/namespace.md)中的成員就很有用。</span><span class="sxs-lookup"><span data-stu-id="22547-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="22547-104">例如，在下列程式碼中，`Console` 會解析成 `TestApp.Console`，而非 <xref:System> 命名空間中的 `Console` 類型。</span><span class="sxs-lookup"><span data-stu-id="22547-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="22547-105">使用 `System.Console` 仍會導致錯誤，因為 `TestApp.System` 類別隱藏了 `System` 命名空間：</span><span class="sxs-lookup"><span data-stu-id="22547-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="22547-106">不過，您可以使用 `global::System.Console` 來暫時解決這個錯誤，如下所示：</span><span class="sxs-lookup"><span data-stu-id="22547-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="22547-107">左邊的識別項是 `global` 時，搜尋正確的識別項會從全域命名空間開始。</span><span class="sxs-lookup"><span data-stu-id="22547-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="22547-108">例如，下列宣告將參考 `TestApp` 作為全域空間的成員。</span><span class="sxs-lookup"><span data-stu-id="22547-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="22547-109">很明顯地，不建議您建立自己的命名空間 `System`，而您也不太可能會遇到任何發生這種狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="22547-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="22547-110">不過，在較大型專案中，命名空間重複項很可能會以某種形式或其他形式出現。</span><span class="sxs-lookup"><span data-stu-id="22547-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="22547-111">在這些情況下，全域命名空間限定詞可確保您能夠指定根命名空間。</span><span class="sxs-lookup"><span data-stu-id="22547-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22547-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22547-112">See also</span></span>

- [<span data-ttu-id="22547-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="22547-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="22547-114">命名空間</span><span class="sxs-lookup"><span data-stu-id="22547-114">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="22547-115">::運算子</span><span class="sxs-lookup"><span data-stu-id="22547-115">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="22547-116">extern</span><span class="sxs-lookup"><span data-stu-id="22547-116">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
