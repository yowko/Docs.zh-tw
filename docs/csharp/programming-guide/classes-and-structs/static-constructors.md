---
title: 靜態建構函式 - C# 程式設計手冊
description: 'C # 中的靜態函式會初始化靜態資料，或只在建立第一個實例或參考靜態成員之前執行一次動作。'
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: c224f96091e8fd5c51139757002ec8a67461a508
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898732"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="629c4-103">靜態建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="629c4-103">Static Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="629c4-104">靜態建構函式用來初始化任何 [static](../../language-reference/keywords/static.md) 資料，或執行只需要執行一次的特定動作。</span><span class="sxs-lookup"><span data-stu-id="629c4-104">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="629c4-105">在建立第一個執行個體或參考任何靜態成員之前，會自動進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="629c4-105">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[SimpleClass#1](snippets/static-constructors/Program.cs#1)]

## <a name="remarks"></a><span data-ttu-id="629c4-106">備註</span><span class="sxs-lookup"><span data-stu-id="629c4-106">Remarks</span></span>

<span data-ttu-id="629c4-107">靜態建構函式具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="629c4-107">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="629c4-108">靜態建構函式不會接受存取修飾詞，也不會包含參數。</span><span class="sxs-lookup"><span data-stu-id="629c4-108">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="629c4-109">類別或結構只能有一個靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="629c4-109">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="629c4-110">靜態建構函式無法繼承或多載。</span><span class="sxs-lookup"><span data-stu-id="629c4-110">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="629c4-111">您無法直接呼叫靜態建構函式，且它是設計成只由通用語言執行平台 (CLR) 呼叫的。</span><span class="sxs-lookup"><span data-stu-id="629c4-111">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="629c4-112">系統會自動呼叫它。</span><span class="sxs-lookup"><span data-stu-id="629c4-112">It is invoked automatically.</span></span>

- <span data-ttu-id="629c4-113">使用者無法控制在程式中執行靜態建構函式的時間。</span><span class="sxs-lookup"><span data-stu-id="629c4-113">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="629c4-114">系統會在建立第一個執行個體或參考任何靜態成員之前，自動呼叫靜態建構函式來初始化 [class](../../language-reference/keywords/class.md)。</span><span class="sxs-lookup"><span data-stu-id="629c4-114">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="629c4-115">靜態建構函式會在執行個體建構函式之前執行。</span><span class="sxs-lookup"><span data-stu-id="629c4-115">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="629c4-116">當叫用指派給事件或委派的靜態方法，而不是指派給它時，會呼叫類型的靜態函式。</span><span class="sxs-lookup"><span data-stu-id="629c4-116">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="629c4-117">如果靜態欄位變數初始設定式存在於靜態建構函式的類別中，它們會按照出現的文字順序執行，緊接著執行靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="629c4-117">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="629c4-118">如果您未提供靜態的函式來初始化靜態欄位，則會將所有靜態欄位初始化為其預設值，如 [c # 類型的預設值](../../language-reference/builtin-types/default-values.md)所列。</span><span class="sxs-lookup"><span data-stu-id="629c4-118">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="629c4-119">如果靜態建構函式擲回例外狀況，執行階段不會叫用它第二次，而類型會在執行程式的應用程式定義域的存留期內保持未初始化。</span><span class="sxs-lookup"><span data-stu-id="629c4-119">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="629c4-120">在多數情況下，當靜態建構函示無法具現化型別時，或靜態建構函式內出現未處理的例外狀況時，會擲回 <xref:System.TypeInitializationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="629c4-120">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="629c4-121">對於在原始程式碼中未明確定義的隱含靜態建構函式，進行疑難排解可能需要檢查中繼語言 (IL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="629c4-121">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="629c4-122">靜態建構函式的存在可能阻止 <xref:System.Reflection.TypeAttributes.BeforeFieldInit> 型別屬性的新增。</span><span class="sxs-lookup"><span data-stu-id="629c4-122">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="629c4-123">這會限制執行階段最佳化。</span><span class="sxs-lookup"><span data-stu-id="629c4-123">This limits runtime optimization.</span></span>

- <span data-ttu-id="629c4-124">宣告為 `static readonly` 的欄位，只能指派為其宣告的一部分，或在靜態建構函式中指派。</span><span class="sxs-lookup"><span data-stu-id="629c4-124">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="629c4-125">當不需要明確靜態建構函式時，請在宣告時初始化靜態欄位，而不要透過靜態建構函式，以獲得更好的執行階段最佳化。</span><span class="sxs-lookup"><span data-stu-id="629c4-125">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="629c4-126">雖然無法直接存取明確靜態建構函式，但應記錄其存在，以協助對初始化例外狀況進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="629c4-126">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="629c4-127">使用方式</span><span class="sxs-lookup"><span data-stu-id="629c4-127">Usage</span></span>

- <span data-ttu-id="629c4-128">靜態建構函式的一般用法為：當類別正在使用記錄檔，且建構函式用來將項目寫入這個檔案時。</span><span class="sxs-lookup"><span data-stu-id="629c4-128">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="629c4-129">如果建構函式可以呼叫 `LoadLibrary` 方法，靜態建構函式在建立 unmanaged 程式碼的包裝函式類別時也很有用。</span><span class="sxs-lookup"><span data-stu-id="629c4-129">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="629c4-130">靜態的函式也是在類型參數上強制執行執行時間檢查的方便位置，該參數無法在編譯時期透過條件約束 (類型參數條件約束) 來檢查。</span><span class="sxs-lookup"><span data-stu-id="629c4-130">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="629c4-131">範例</span><span class="sxs-lookup"><span data-stu-id="629c4-131">Example</span></span>

 <span data-ttu-id="629c4-132">在此範例中，`Bus` 類別具有靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="629c4-132">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="629c4-133">建立 `Bus` 的第一個執行個體 (`bus1`) 時，即會叫用靜態建構函式來初始化類別。</span><span class="sxs-lookup"><span data-stu-id="629c4-133">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="629c4-134">範例輸出可確認即使建立了兩個 `Bus` 執行個體，靜態建構函式也只執行一次，而且它是在執行個體建構函式執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="629c4-134">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[BusSample#2](snippets/static-constructors/Program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="629c4-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="629c4-135">C# language specification</span></span>

<span data-ttu-id="629c4-136">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[靜態建構函式](~/_csharplang/spec/classes.md#static-constructors)一節。</span><span class="sxs-lookup"><span data-stu-id="629c4-136">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="629c4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="629c4-137">See also</span></span>

- [<span data-ttu-id="629c4-138">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="629c4-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="629c4-139">類別和結構</span><span class="sxs-lookup"><span data-stu-id="629c4-139">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="629c4-140">建構函式</span><span class="sxs-lookup"><span data-stu-id="629c4-140">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="629c4-141">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="629c4-141">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="629c4-142">完成項</span><span class="sxs-lookup"><span data-stu-id="629c4-142">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="629c4-143">建構函式設計指導方針</span><span class="sxs-lookup"><span data-stu-id="629c4-143">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="629c4-144">安全性警告-CA2121：靜態的函式應為私用</span><span class="sxs-lookup"><span data-stu-id="629c4-144">Security Warning - CA2121: Static constructors should be private</span></span>](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
