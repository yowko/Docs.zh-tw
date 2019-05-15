---
title: 使用 Override 和 New 關鍵字進行版本控制 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: ec6040081d44a389bd42bb50cdd81ac0634abf91
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583117"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="f35c0-102">使用 Override 和 New 關鍵字進行版本控制 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f35c0-102">Versioning with the Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="f35c0-103">C# 語言的設計，就是讓不同文件庫的[基底](../../../csharp/language-reference/keywords/base.md)和衍生類別的版本控制能夠發展兼具回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="f35c0-103">The C# language is designed so that versioning between [base](../../../csharp/language-reference/keywords/base.md) and derived classes in different libraries can evolve and maintain backward compatibility.</span></span> <span data-ttu-id="f35c0-104">例如，這表示 C# 完全支援在基底[類別](../../../csharp/language-reference/keywords/class.md)中引入與衍生類別成員同名的新成員，不會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="f35c0-104">This means, for example, that the introduction of a new member in a base [class](../../../csharp/language-reference/keywords/class.md) with the same name as a member in a derived class is completely supported by C# and does not lead to unexpected behavior.</span></span> <span data-ttu-id="f35c0-105">這也表示，類別必須明確指出方法是打算覆寫繼承的方法，還是方法是一種新方法，會隱藏名稱相似的繼承方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-105">It also means that a class must explicitly state whether a method is intended to override an inherited method, or whether a method is a new method that hides a similarly named inherited method.</span></span>  
  
 <span data-ttu-id="f35c0-106">在 C# 中，衍生類別可以包含與基底類別方法同名的方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-106">In C#, derived classes can contain methods with the same name as base class methods.</span></span>  
  
- <span data-ttu-id="f35c0-107">基底類別方法必須定義為 [virtual](../../../csharp/language-reference/keywords/virtual.md)。</span><span class="sxs-lookup"><span data-stu-id="f35c0-107">The base class method must be defined [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
- <span data-ttu-id="f35c0-108">如果衍生類別中的方法前未加上 [new](../../../csharp/language-reference/keywords/new.md) 或 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字，編譯器就會發出警告，方法會表現為如同有 `new` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f35c0-108">If the method in the derived class is not preceded by [new](../../../csharp/language-reference/keywords/new.md) or [override](../../../csharp/language-reference/keywords/override.md) keywords, the compiler will issue a warning and the method will behave as if the `new` keyword were present.</span></span>  
  
- <span data-ttu-id="f35c0-109">如果衍生類別中的方法前面加上 `new` 關鍵字，方法會定義為不受基底類別中的方法影響。</span><span class="sxs-lookup"><span data-stu-id="f35c0-109">If the method in the derived class is preceded with the `new` keyword, the method is defined as being independent of the method in the base class.</span></span>  
  
- <span data-ttu-id="f35c0-110">如果衍生類別中的方法前面加上 `override` 關鍵字，衍生類別的物件會呼叫該方法，不會呼叫基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-110">If the method in the derived class is preceded with the `override` keyword, objects of the derived class will call that method instead of the base class method.</span></span>  
  
- <span data-ttu-id="f35c0-111">您可以使用 `base` 關鍵字從衍生類別中呼叫基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-111">The base class method can be called from within the derived class using the `base` keyword.</span></span>  
  
- <span data-ttu-id="f35c0-112">`override`、`virtual` 和 `new` 關鍵字也可以套用至屬性、索引子和事件。</span><span class="sxs-lookup"><span data-stu-id="f35c0-112">The `override`, `virtual`, and `new` keywords can also be applied to properties, indexers, and events.</span></span>  
  
 <span data-ttu-id="f35c0-113">C# 方法預設不是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="f35c0-113">By default, C# methods are not virtual.</span></span> <span data-ttu-id="f35c0-114">如果方法宣告為虛擬，則繼承該方法的任何類別都可以實作自己的版本。</span><span class="sxs-lookup"><span data-stu-id="f35c0-114">If a method is declared as virtual, any class inheriting the method can implement its own version.</span></span> <span data-ttu-id="f35c0-115">若要使方法成為虛擬的，基底類別的方法宣告中會使用 `virtual` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="f35c0-115">To make a method virtual, the `virtual` modifier is used in the method declaration of the base class.</span></span> <span data-ttu-id="f35c0-116">然後，衍生類別可以使用 `override` 關鍵字覆寫基底虛擬方法，或使用 `new` 關鍵字隱藏基底類別中的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-116">The derived class can then override the base virtual method by using the `override` keyword or hide the virtual method in the base class by using the `new` keyword.</span></span> <span data-ttu-id="f35c0-117">如果不指定 `override` 關鍵字，也不指定 `new` 關鍵字，則編譯器會發出警告，且衍生類別中的方法會隱藏基底類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-117">If neither the `override` keyword nor the `new` keyword is specified, the compiler will issue a warning and the method in the derived class will hide the method in the base class.</span></span>  
  
 <span data-ttu-id="f35c0-118">為在練習中示範此技巧，假設公司 A 建立了類別 `GraphicsClass`，為您的程式所用。</span><span class="sxs-lookup"><span data-stu-id="f35c0-118">To demonstrate this in practice, assume for a moment that Company A has created a class named `GraphicsClass`, which your program uses.</span></span> <span data-ttu-id="f35c0-119">以下即為 `GraphicsClass`：</span><span class="sxs-lookup"><span data-stu-id="f35c0-119">The following is `GraphicsClass`:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 <span data-ttu-id="f35c0-120">您的公司使用這個類別，而您用它衍生自己的類別，新增了新的方法︰</span><span class="sxs-lookup"><span data-stu-id="f35c0-120">Your company uses this class, and you use it to derive your own class, adding a new method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 <span data-ttu-id="f35c0-121">您的應用程式一直使用正常，直到公司 A 發行新版的 `GraphicsClass`，類似下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="f35c0-121">Your application is used without problems, until Company A releases a new version of `GraphicsClass`, which resembles the following code:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 <span data-ttu-id="f35c0-122">新版的 `GraphicsClass` 現在包含一個名為 `DrawRectangle` 的方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-122">The new version of `GraphicsClass` now contains a method named `DrawRectangle`.</span></span> <span data-ttu-id="f35c0-123">一開始，一切如常。</span><span class="sxs-lookup"><span data-stu-id="f35c0-123">Initially, nothing occurs.</span></span> <span data-ttu-id="f35c0-124">新版本與舊版仍為二進位相容。</span><span class="sxs-lookup"><span data-stu-id="f35c0-124">The new version is still binary compatible with the old version.</span></span> <span data-ttu-id="f35c0-125">您部署的所有軟體仍繼續運作，即使這些電腦系統上安裝了新類別。</span><span class="sxs-lookup"><span data-stu-id="f35c0-125">Any software that you have deployed will continue to work, even if the new class is installed on those computer systems.</span></span> <span data-ttu-id="f35c0-126">目前對方法 `DrawRectangle` 的任何呼叫仍繼續參考您衍生類別中的版本。</span><span class="sxs-lookup"><span data-stu-id="f35c0-126">Any existing calls to the method `DrawRectangle` will continue to reference your version, in your derived class.</span></span>  
  
 <span data-ttu-id="f35c0-127">不過，一旦使用新版的 `GraphicsClass` 重新編譯應用程式，就會立刻收到編譯器警告 CS0108。</span><span class="sxs-lookup"><span data-stu-id="f35c0-127">However, as soon as you recompile your application by using the new version of `GraphicsClass`, you will receive a warning from the compiler, CS0108.</span></span> <span data-ttu-id="f35c0-128">這個警告會通知您，您必須考慮希望 `DrawRectangle` 方法在應用程式中如何表現。</span><span class="sxs-lookup"><span data-stu-id="f35c0-128">This warning informs you that you have to consider how you want your `DrawRectangle` method to behave in your application.</span></span>  
  
 <span data-ttu-id="f35c0-129">如果您希望自己的方法覆寫新的基底類別方法，請使用 `override` 關鍵字︰</span><span class="sxs-lookup"><span data-stu-id="f35c0-129">If you want your method to override the new base class method, use the `override` keyword:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 <span data-ttu-id="f35c0-130">`override` 關鍵字可以確保衍生自 `YourDerivedGraphicsClass` 的所有物件都會使用 `DrawRectangle` 的衍生類別版本。</span><span class="sxs-lookup"><span data-stu-id="f35c0-130">The `override` keyword makes sure that any objects derived from `YourDerivedGraphicsClass` will use the derived class version of `DrawRectangle`.</span></span> <span data-ttu-id="f35c0-131">衍生自 `YourDerivedGraphicsClass` 的物件仍然可以使用 base 關鍵字存取 `DrawRectangle` 的基底類別版本︰</span><span class="sxs-lookup"><span data-stu-id="f35c0-131">Objects derived from `YourDerivedGraphicsClass` can still access the base class version of `DrawRectangle` by using the base keyword:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 <span data-ttu-id="f35c0-132">如果您不希望自己的方法覆寫新的基底類別方法，請採納下列考量。</span><span class="sxs-lookup"><span data-stu-id="f35c0-132">If you do not want your method to override the new base class method, the following considerations apply.</span></span> <span data-ttu-id="f35c0-133">為避免混淆兩個方法，您可以重新命名您的方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-133">To avoid confusion between the two methods, you can rename your method.</span></span> <span data-ttu-id="f35c0-134">這很耗時間又容易發生錯誤，並且在某些情況下不實際。</span><span class="sxs-lookup"><span data-stu-id="f35c0-134">This can be time-consuming and error-prone, and just not practical in some cases.</span></span> <span data-ttu-id="f35c0-135">不過，如果您的專案相對較小，您可以使用 Visual Studio 的重構選項來重新命名方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-135">However, if your project is relatively small, you can use Visual Studio's Refactoring options to rename the method.</span></span> <span data-ttu-id="f35c0-136">如需詳細資訊，請參閱[重構類別和型別 (類別設計工具)](/visualstudio/ide/refactoring-classes-and-types-class-designer)。</span><span class="sxs-lookup"><span data-stu-id="f35c0-136">For more information, see [Refactoring Classes and Types (Class Designer)](/visualstudio/ide/refactoring-classes-and-types-class-designer).</span></span>  
  
 <span data-ttu-id="f35c0-137">或者，您也可以在衍生類別定義中使用關鍵字 `new`，避免出現警告：</span><span class="sxs-lookup"><span data-stu-id="f35c0-137">Alternatively, you can prevent the warning by using the keyword `new` in your derived class definition:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 <span data-ttu-id="f35c0-138">使用 `new` 關鍵字會通知編譯器，您的定義要隱藏基底類別中包含的定義。</span><span class="sxs-lookup"><span data-stu-id="f35c0-138">Using the `new` keyword tells the compiler that your definition hides the definition that is contained in the base class.</span></span> <span data-ttu-id="f35c0-139">這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="f35c0-139">This is the default behavior.</span></span>  
  
## <a name="override-and-method-selection"></a><span data-ttu-id="f35c0-140">覆寫和方法選擇</span><span class="sxs-lookup"><span data-stu-id="f35c0-140">Override and Method Selection</span></span>  
 <span data-ttu-id="f35c0-141">在類別上命名方法時，如果有多個方法與呼叫相容，C# 編譯器會選取最好的方法呼叫，例如當有兩種方法同名時，並傳遞與參數相容的參數。</span><span class="sxs-lookup"><span data-stu-id="f35c0-141">When a method is named on a class, the C# compiler selects the best method to call if more than one method is compatible with the call, such as when there are two methods with the same name, and parameters that are compatible with the parameter passed.</span></span> <span data-ttu-id="f35c0-142">下列方法相容︰</span><span class="sxs-lookup"><span data-stu-id="f35c0-142">The following methods would be compatible:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 <span data-ttu-id="f35c0-143">在 `Derived` 的執行個體上呼叫 `DoWork` 時，C# 編譯器會先嘗試進行與 `DoWork` 版本相容的呼叫，此版本原是在 `Derived` 上宣告。</span><span class="sxs-lookup"><span data-stu-id="f35c0-143">When `DoWork` is called on an instance of `Derived`, the C# compiler will first try to make the call compatible with the versions of `DoWork` declared originally on `Derived`.</span></span> <span data-ttu-id="f35c0-144">覆寫方法不視為在類別中宣告，它們是基底類別中所宣告方法的新實作。</span><span class="sxs-lookup"><span data-stu-id="f35c0-144">Override methods are not considered as declared on a class, they are new implementations of a method declared on a base class.</span></span> <span data-ttu-id="f35c0-145">只有當 C# 編譯器無法比對方法呼叫和 `Derived` 中的原始方法時，才會嘗試比對具有相同名稱和相容參數的覆寫方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="f35c0-145">Only if the C# compiler cannot match the method call to an original method on `Derived` will it try to match the call to an overridden method with the same name and compatible parameters.</span></span> <span data-ttu-id="f35c0-146">例如：</span><span class="sxs-lookup"><span data-stu-id="f35c0-146">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 <span data-ttu-id="f35c0-147">因為變數 `val` 可以隱含方式轉換為 double，所以 C# 編譯器會呼叫 `DoWork(double)`，不是呼叫 `DoWork(int)`。</span><span class="sxs-lookup"><span data-stu-id="f35c0-147">Because the variable `val` can be converted to a double implicitly, the C# compiler calls `DoWork(double)` instead of `DoWork(int)`.</span></span> <span data-ttu-id="f35c0-148">有兩種方式可避免這種情況。</span><span class="sxs-lookup"><span data-stu-id="f35c0-148">There are two ways to avoid this.</span></span> <span data-ttu-id="f35c0-149">首先，避免使用和虛擬方法相同的名稱宣告新方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-149">First, avoid declaring new methods with the same name as virtual methods.</span></span> <span data-ttu-id="f35c0-150">第二，您可以將 `Derived` 執行個體轉換成 `Base`，讓 C# 編譯器搜尋基底類別方法清單，指示它呼叫虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="f35c0-150">Second, you can instruct the C# compiler to call the virtual method by making it search the base class method list by casting the instance of `Derived` to `Base`.</span></span> <span data-ttu-id="f35c0-151">因為方法是虛擬的，所以會在 `Derived` 呼叫 `DoWork(int)` 實作。</span><span class="sxs-lookup"><span data-stu-id="f35c0-151">Because the method is virtual, the implementation of `DoWork(int)` on `Derived` will be called.</span></span> <span data-ttu-id="f35c0-152">例如：</span><span class="sxs-lookup"><span data-stu-id="f35c0-152">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 <span data-ttu-id="f35c0-153">如需更多的 `new` 和 `override` 範例，請參閱[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="f35c0-153">For more examples of `new` and `override`, see [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35c0-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f35c0-154">See also</span></span>

- [<span data-ttu-id="f35c0-155">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f35c0-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f35c0-156">類別和結構</span><span class="sxs-lookup"><span data-stu-id="f35c0-156">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="f35c0-157">方法</span><span class="sxs-lookup"><span data-stu-id="f35c0-157">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="f35c0-158">繼承</span><span class="sxs-lookup"><span data-stu-id="f35c0-158">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
