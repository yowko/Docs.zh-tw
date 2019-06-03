---
title: 泛型委派 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: ff19b3d71858552158a8ae5d0ab362a86dc98e65
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423503"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="63159-102">泛型委派 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="63159-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="63159-103">[委派](../../../csharp/language-reference/keywords/delegate.md)可以定義自己的型別參數。</span><span class="sxs-lookup"><span data-stu-id="63159-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="63159-104">參考泛型委派的程式碼，可以指定型別引數建立封閉式建構類型，就像在具現化泛型類別或呼叫泛型方法時一樣，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="63159-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="63159-105">C# 2.0 版具有方法群組轉換新功能，適用於實體及泛型委派類型，並可讓您使用這個簡化的語法撰寫上一行：</span><span class="sxs-lookup"><span data-stu-id="63159-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="63159-106">在泛型類別中定義的委派，可以使用和類別方法相同的方式，使用泛型類別類型參數。</span><span class="sxs-lookup"><span data-stu-id="63159-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="63159-107">參考委派的程式碼必須指定包含類別的型別引數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="63159-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="63159-108">泛型委派在根據一般設計模式定義事件方面特別有幫助，因為傳送者引數可以是強型別，不必再在 <xref:System.Object> 間來回轉換。</span><span class="sxs-lookup"><span data-stu-id="63159-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="63159-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63159-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="63159-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="63159-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="63159-111">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="63159-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="63159-112">泛型方法</span><span class="sxs-lookup"><span data-stu-id="63159-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)
- [<span data-ttu-id="63159-113">泛型類別</span><span class="sxs-lookup"><span data-stu-id="63159-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)
- [<span data-ttu-id="63159-114">泛型介面</span><span class="sxs-lookup"><span data-stu-id="63159-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [<span data-ttu-id="63159-115">委派</span><span class="sxs-lookup"><span data-stu-id="63159-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="63159-116">泛型</span><span class="sxs-lookup"><span data-stu-id="63159-116">Generics</span></span>](~/docs/standard/generics/index.md)
