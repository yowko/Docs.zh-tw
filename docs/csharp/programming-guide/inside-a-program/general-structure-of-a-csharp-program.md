---
title: "C# 程式的一般結構 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, program structure
ms.assetid: 5ae964a5-0ef0-40fe-88fb-6d1793371d0d
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d55ac6a6d35e5f47ab26da681afe9fb5555331ec
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="general-structure-of-a-c-program-c-programming-guide"></a><span data-ttu-id="d5d2b-102">C# 程式的一般結構 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d5d2b-102">General Structure of a C# Program (C# Programming Guide)</span></span>
<span data-ttu-id="d5d2b-103">C# 程式可以包含一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-103">C# programs can consist of one or more files.</span></span> <span data-ttu-id="d5d2b-104">每個檔案可以包含零個或多個命名空間。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-104">Each file can contain zero or more namespaces.</span></span> <span data-ttu-id="d5d2b-105">命名空間可以包含類別、結構、介面、列舉和委派等類型，以及他命名空間。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-105">A namespace can contain types such as classes, structs, interfaces, enumerations, and delegates, in addition to other namespaces.</span></span> <span data-ttu-id="d5d2b-106">以下是 C# 程式的基本架構，其中包含上述所有項目。</span><span class="sxs-lookup"><span data-stu-id="d5d2b-106">The following is the skeleton of a C# program that contains all of these elements.</span></span>  
  
 <span data-ttu-id="d5d2b-107">[!code-cs[csProgGuide#34](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/general-structure-of-a-csharp-program_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d5d2b-107">[!code-cs[csProgGuide#34](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/general-structure-of-a-csharp-program_1.cs)]</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d5d2b-108">相關章節</span><span class="sxs-lookup"><span data-stu-id="d5d2b-108">Related Sections</span></span>  
 <span data-ttu-id="d5d2b-109">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="d5d2b-109">For more information:</span></span>  
  
-   [<span data-ttu-id="d5d2b-110">類別</span><span class="sxs-lookup"><span data-stu-id="d5d2b-110">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [<span data-ttu-id="d5d2b-111">結構</span><span class="sxs-lookup"><span data-stu-id="d5d2b-111">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [<span data-ttu-id="d5d2b-112">命名空間</span><span class="sxs-lookup"><span data-stu-id="d5d2b-112">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="d5d2b-113">介面</span><span class="sxs-lookup"><span data-stu-id="d5d2b-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [<span data-ttu-id="d5d2b-114">委派</span><span class="sxs-lookup"><span data-stu-id="d5d2b-114">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d5d2b-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d5d2b-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5d2b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d2b-116">See Also</span></span>  
 <span data-ttu-id="d5d2b-117">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5d2b-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d5d2b-118">[C# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5d2b-118">[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md) </span></span>  
 <span data-ttu-id="d5d2b-119">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5d2b-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="d5d2b-120">\<paveover>C# 範例應用程式</span><span class="sxs-lookup"><span data-stu-id="d5d2b-120">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)

