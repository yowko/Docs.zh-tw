---
title: 靜態建構函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 110d83caad0c588fa899a4129897784e9c74aab8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881919"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="6e6ff-102">靜態建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6e6ff-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="6e6ff-103">靜態建構函式用來初始化任何 [static](../../../csharp/language-reference/keywords/static.md) 資料，或執行只需要執行一次的特定動作。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="6e6ff-104">在建立第一個執行個體或參考任何靜態成員之前，會自動進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="6e6ff-105">靜態建構函式具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6e6ff-105">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="6e6ff-106">靜態建構函式不會接受存取修飾詞，也不會包含參數。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
- <span data-ttu-id="6e6ff-107">系統會在建立第一個執行個體或參考任何靜態成員之前，自動呼叫靜態建構函式來初始化 [class](../../../csharp/language-reference/keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="6e6ff-108">請注意，當靜態方法指派給事件時，會呼叫型別的靜態建構函式；或者指派時會叫用委派。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-108">Note that a type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span>
  
- <span data-ttu-id="6e6ff-109">靜態建構函式不能直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-109">A static constructor cannot be called directly.</span></span>  
  
- <span data-ttu-id="6e6ff-110">使用者無法控制在程式中執行靜態建構函式的時間。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
- <span data-ttu-id="6e6ff-111">靜態建構函式的一般用法為：當類別正在使用記錄檔，且建構函式用來將項目寫入這個檔案時。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
- <span data-ttu-id="6e6ff-112">如果建構函式可以呼叫 `LoadLibrary` 方法，靜態建構函式在建立 unmanaged 程式碼的包裝函式類別時也很有用。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
- <span data-ttu-id="6e6ff-113">如果靜態建構函式擲回例外狀況，執行階段不會叫用它第二次，而類型會在執行程式的應用程式定義域的存留期內保持未初始化。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e6ff-114">範例</span><span class="sxs-lookup"><span data-stu-id="6e6ff-114">Example</span></span>  
 <span data-ttu-id="6e6ff-115">在此範例中，`Bus` 類別具有靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="6e6ff-116">建立 `Bus` 的第一個執行個體 (`bus1`) 時，即會叫用靜態建構函式來初始化類別。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="6e6ff-117">範例輸出可確認即使建立了兩個 `Bus` 執行個體，靜態建構函式也只執行一次，而且它是在執行個體建構函式執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="6e6ff-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a><span data-ttu-id="6e6ff-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e6ff-118">See also</span></span>

- [<span data-ttu-id="6e6ff-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6e6ff-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6e6ff-120">類別和結構</span><span class="sxs-lookup"><span data-stu-id="6e6ff-120">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="6e6ff-121">建構函式</span><span class="sxs-lookup"><span data-stu-id="6e6ff-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="6e6ff-122">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="6e6ff-122">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="6e6ff-123">完成項</span><span class="sxs-lookup"><span data-stu-id="6e6ff-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
