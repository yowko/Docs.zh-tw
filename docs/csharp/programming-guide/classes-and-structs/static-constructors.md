---
title: 靜態建構函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 87a7b16d3e096f6a5bf05475ccc7c43862324ae3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583359"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="298ab-102">靜態建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="298ab-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="298ab-103">靜態建構函式用來初始化任何 [static](../../../csharp/language-reference/keywords/static.md) 資料，或執行只需要執行一次的特定動作。</span><span class="sxs-lookup"><span data-stu-id="298ab-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="298ab-104">在建立第一個執行個體或參考任何靜態成員之前，會自動進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="298ab-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="298ab-105">靜態建構函式具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="298ab-105">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="298ab-106">靜態建構函式不會接受存取修飾詞，也不會包含參數。</span><span class="sxs-lookup"><span data-stu-id="298ab-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
- <span data-ttu-id="298ab-107">系統會在建立第一個執行個體或參考任何靜態成員之前，自動呼叫靜態建構函式來初始化 [class](../../../csharp/language-reference/keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="298ab-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
- <span data-ttu-id="298ab-108">靜態建構函式不能直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="298ab-108">A static constructor cannot be called directly.</span></span>  
  
- <span data-ttu-id="298ab-109">使用者無法控制在程式中執行靜態建構函式的時間。</span><span class="sxs-lookup"><span data-stu-id="298ab-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
- <span data-ttu-id="298ab-110">靜態建構函式的一般用法為：當類別正在使用記錄檔，且建構函式用來將項目寫入這個檔案時。</span><span class="sxs-lookup"><span data-stu-id="298ab-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
- <span data-ttu-id="298ab-111">如果建構函式可以呼叫 `LoadLibrary` 方法，靜態建構函式在建立 unmanaged 程式碼的包裝函式類別時也很有用。</span><span class="sxs-lookup"><span data-stu-id="298ab-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
- <span data-ttu-id="298ab-112">如果靜態建構函式擲回例外狀況，執行階段不會叫用它第二次，而類型會在執行程式的應用程式定義域的存留期內保持未初始化。</span><span class="sxs-lookup"><span data-stu-id="298ab-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="298ab-113">範例</span><span class="sxs-lookup"><span data-stu-id="298ab-113">Example</span></span>  
 <span data-ttu-id="298ab-114">在此範例中，`Bus` 類別具有靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="298ab-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="298ab-115">建立 `Bus` 的第一個執行個體 (`bus1`) 時，即會叫用靜態建構函式來初始化類別。</span><span class="sxs-lookup"><span data-stu-id="298ab-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="298ab-116">範例輸出可確認即使建立了兩個 `Bus` 執行個體，靜態建構函式也只執行一次，而且它是在執行個體建構函式執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="298ab-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a><span data-ttu-id="298ab-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="298ab-117">See also</span></span>

- [<span data-ttu-id="298ab-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="298ab-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="298ab-119">類別和結構</span><span class="sxs-lookup"><span data-stu-id="298ab-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="298ab-120">建構函式</span><span class="sxs-lookup"><span data-stu-id="298ab-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="298ab-121">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="298ab-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="298ab-122">完成項</span><span class="sxs-lookup"><span data-stu-id="298ab-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
