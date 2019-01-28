---
title: 靜態類別和靜態類別成員 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 870d7593dcfd6c2b8d58562d182d37a64484a53e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577489"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a><span data-ttu-id="4137f-102">靜態類別和靜態類別成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4137f-102">Static Classes and Static Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="4137f-103">[static](../../../csharp/language-reference/keywords/static.md) 類別基本上與非靜態類別相同，但有一項差異︰無法具現化靜態類別。</span><span class="sxs-lookup"><span data-stu-id="4137f-103">A [static](../../../csharp/language-reference/keywords/static.md) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated.</span></span> <span data-ttu-id="4137f-104">換句話說，您不能使用 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字來建立類別類型的變數。</span><span class="sxs-lookup"><span data-stu-id="4137f-104">In other words, you cannot use the [new](../../../csharp/language-reference/keywords/new.md) keyword to create a variable of the class type.</span></span> <span data-ttu-id="4137f-105">因為沒有任何執行個體變數，所以您可以使用類別名稱本身來存取靜態類別的成員。</span><span class="sxs-lookup"><span data-stu-id="4137f-105">Because there is no instance variable, you access the members of a static class by using the class name itself.</span></span> <span data-ttu-id="4137f-106">例如，如果您的 `UtilityClass` 靜態類別包含 `MethodA` 公用靜態方法，則會呼叫方法，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="4137f-106">For example, if you have a static class that is named `UtilityClass` that has a public static method named `MethodA`, you call the method as shown in the following example:</span></span>  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 <span data-ttu-id="4137f-107">如果方法集只作業於輸入參數，並且不需要取得或設定任何內部執行個體欄位，則靜態類別可以用作其方便使用的容器。</span><span class="sxs-lookup"><span data-stu-id="4137f-107">A static class can be used as a convenient container for sets of methods that just operate on input parameters and do not have to get or set any internal instance fields.</span></span> <span data-ttu-id="4137f-108">例如，在 .NET Framework 類別庫中，靜態 <xref:System.Math?displayProperty=nameWithType> 類別包含可執行數學運算的方法，而不需要儲存或擷取特定 <xref:System.Math> 類別執行個體所獨有的資料。</span><span class="sxs-lookup"><span data-stu-id="4137f-108">For example, in the .NET Framework Class Library, the static <xref:System.Math?displayProperty=nameWithType> class contains methods that perform mathematical operations, without any requirement to store or retrieve data that is unique to a particular instance of the <xref:System.Math> class.</span></span> <span data-ttu-id="4137f-109">亦即，您可以指定類別名稱和方法名稱來套用類別的成員，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4137f-109">That is, you apply the members of the class by specifying the class name and the method name, as shown in the following example.</span></span>  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 <span data-ttu-id="4137f-110">與所有類別類型的情況相同，載入可參考類別的程式時，[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Common Language Runtime (CLR) 會載入靜態類別的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="4137f-110">As is the case with all class types, the type information for a static class is loaded by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] common language runtime (CLR) when the program that references the class is loaded.</span></span> <span data-ttu-id="4137f-111">程式無法指定確實載入類別的時間。</span><span class="sxs-lookup"><span data-stu-id="4137f-111">The program cannot specify exactly when the class is loaded.</span></span> <span data-ttu-id="4137f-112">不過，一定會載入類別、初始化其欄位，並在第一次於程式中參考類別之前呼叫其靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="4137f-112">However, it is guaranteed to be loaded and to have its fields initialized and its static constructor called before the class is referenced for the first time in your program.</span></span> <span data-ttu-id="4137f-113">只會呼叫靜態建構函式一次，而且靜態類別在程式所在應用程式定義域的存留期間保留在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="4137f-113">A static constructor is only called one time, and a static class remains in memory for the lifetime of the application domain in which your program resides.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4137f-114">若要建立只允許建立它本身之一個執行個體的非靜態類別，請參閱 [Implementing Singleton in C#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29) (在 C# 中實作單一)。</span><span class="sxs-lookup"><span data-stu-id="4137f-114">To create a non-static class that allows only one instance of itself to be created, see [Implementing Singleton in C#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).</span></span>  
  
 <span data-ttu-id="4137f-115">下列清單提供靜態類別的主要功能︰</span><span class="sxs-lookup"><span data-stu-id="4137f-115">The following list provides the main features of a static class:</span></span>  
  
-   <span data-ttu-id="4137f-116">僅包含靜態成員。</span><span class="sxs-lookup"><span data-stu-id="4137f-116">Contains only static members.</span></span>  
  
-   <span data-ttu-id="4137f-117">無法具現化。</span><span class="sxs-lookup"><span data-stu-id="4137f-117">Cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="4137f-118">已密封。</span><span class="sxs-lookup"><span data-stu-id="4137f-118">Is sealed.</span></span>  
  
-   <span data-ttu-id="4137f-119">不能包含[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="4137f-119">Cannot contain [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="4137f-120">因此，建立靜態類別，基本上與建立只包含靜態成員和私用建構函式的類別相同。</span><span class="sxs-lookup"><span data-stu-id="4137f-120">Creating a static class is therefore basically the same as creating a class that contains only static members and a private constructor.</span></span> <span data-ttu-id="4137f-121">私用建構函式可防止具現化類別。</span><span class="sxs-lookup"><span data-stu-id="4137f-121">A private constructor prevents the class from being instantiated.</span></span> <span data-ttu-id="4137f-122">使用靜態類別的優點在於編譯器可以確認不會意外新增任何執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="4137f-122">The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added.</span></span> <span data-ttu-id="4137f-123">編譯器將保證無法建立此類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4137f-123">The compiler will guarantee that instances of this class cannot be created.</span></span>  
  
 <span data-ttu-id="4137f-124">靜態類別已密封，因此無法進行繼承。</span><span class="sxs-lookup"><span data-stu-id="4137f-124">Static classes are sealed and therefore cannot be inherited.</span></span> <span data-ttu-id="4137f-125">它們無法繼承自 <xref:System.Object> 以外的任何類別。</span><span class="sxs-lookup"><span data-stu-id="4137f-125">They cannot inherit from any class except <xref:System.Object>.</span></span> <span data-ttu-id="4137f-126">靜態類別不能包含執行個體建構函式，但可以包含靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="4137f-126">Static classes cannot contain an instance constructor; however, they can contain a static constructor.</span></span> <span data-ttu-id="4137f-127">如果類別包含需要重要初始化的靜態成員，則非靜態類別也應該定義靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="4137f-127">Non-static classes should also define a static constructor if the class contains static members that require non-trivial initialization.</span></span> <span data-ttu-id="4137f-128">如需詳細資訊，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="4137f-128">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4137f-129">範例</span><span class="sxs-lookup"><span data-stu-id="4137f-129">Example</span></span>  
 <span data-ttu-id="4137f-130">以下是包含兩種方法可將溫度從攝氏轉換為華氏以及從華氏轉換為攝氏的靜態類別範例︰</span><span class="sxs-lookup"><span data-stu-id="4137f-130">Here is an example of a static class that contains two methods that convert temperature from Celsius to Fahrenheit and from Fahrenheit to Celsius:</span></span>  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a><span data-ttu-id="4137f-131">靜態成員</span><span class="sxs-lookup"><span data-stu-id="4137f-131">Static Members</span></span>  
 <span data-ttu-id="4137f-132">非靜態類別可以包含靜態方法、欄位、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="4137f-132">A non-static class can contain static methods, fields, properties, or events.</span></span> <span data-ttu-id="4137f-133">即使尚未建立類別的執行個體，還是可以在類別上呼叫靜態成員。</span><span class="sxs-lookup"><span data-stu-id="4137f-133">The static member is callable on a class even when no instance of the class has been created.</span></span> <span data-ttu-id="4137f-134">靜態成員一律是透過類別名稱進行存取，而不是執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="4137f-134">The static member is always accessed by the class name, not the instance name.</span></span> <span data-ttu-id="4137f-135">不論建立多少個類別執行個體，都只會有一個靜態成員複本。</span><span class="sxs-lookup"><span data-stu-id="4137f-135">Only one copy of a static member exists, regardless of how many instances of the class are created.</span></span> <span data-ttu-id="4137f-136">靜態方法和屬性無法存取其包含類型中的非靜態欄位和事件，也無法存取任何物件的執行個體變數，除非它明確地傳入方法參數。</span><span class="sxs-lookup"><span data-stu-id="4137f-136">Static methods and properties cannot access non-static fields and events in their containing type, and they cannot access an instance variable of any object unless it is explicitly passed in a method parameter.</span></span>  
  
 <span data-ttu-id="4137f-137">使用一些靜態成員宣告非靜態類別，會比將整個類別宣告為靜態更為常見。</span><span class="sxs-lookup"><span data-stu-id="4137f-137">It is more typical to declare a non-static class with some static members, than to declare an entire class as static.</span></span> <span data-ttu-id="4137f-138">靜態欄位的兩個常用用法是持續計算已具現化的物件數目，或是儲存必須在所有執行個體之間共用的值。</span><span class="sxs-lookup"><span data-stu-id="4137f-138">Two common uses of static fields are to keep a count of the number of objects that have been instantiated, or to store a value that must be shared among all instances.</span></span>  
  
 <span data-ttu-id="4137f-139">可以多載但無法覆寫靜態方法，因為它們屬於類別，而不是類別的任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="4137f-139">Static methods can be overloaded but not overridden, because they belong to the class, and not to any instance of the class.</span></span>  
  
 <span data-ttu-id="4137f-140">雖然欄位不可以宣告為 `static const`，但是 [const](../../../csharp/language-reference/keywords/const.md) 欄位在其行為中基本上是靜態的。</span><span class="sxs-lookup"><span data-stu-id="4137f-140">Although a field cannot be declared as `static const`, a [const](../../../csharp/language-reference/keywords/const.md) field is essentially static in its behavior.</span></span> <span data-ttu-id="4137f-141">它屬於類型，而不是類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4137f-141">It belongs to the type, not to instances of the type.</span></span> <span data-ttu-id="4137f-142">因此，使用用於靜態欄位的相同 `ClassName.MemberName` 標記法可以存取 const 欄位。</span><span class="sxs-lookup"><span data-stu-id="4137f-142">Therefore, const fields can be accessed by using the same `ClassName.MemberName` notation that is used for static fields.</span></span> <span data-ttu-id="4137f-143">不需要物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="4137f-143">No object instance is required.</span></span>  
  
 <span data-ttu-id="4137f-144">C# 不支援靜態區域變數 (方法範圍中所宣告的變數)。</span><span class="sxs-lookup"><span data-stu-id="4137f-144">C# does not support static local variables (variables that are declared in method scope).</span></span>  
  
 <span data-ttu-id="4137f-145">在成員的傳回型別前面使用 `static` 關鍵字，即可宣告靜態類別成員，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="4137f-145">You declare static class members by using the `static` keyword before the return type of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 <span data-ttu-id="4137f-146">第一次存取靜態成員之前，以及呼叫靜態建構函式 (如果有的話) 之前，都會初始化靜態成員。</span><span class="sxs-lookup"><span data-stu-id="4137f-146">Static members are initialized before the static member is accessed for the first time and before the static constructor, if there is one, is called.</span></span> <span data-ttu-id="4137f-147">若要存取靜態類別成員，請使用類別的名稱來指定成員的位置，而不是變數名稱，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="4137f-147">To access a static class member, use the name of the class instead of a variable name to specify the location of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 <span data-ttu-id="4137f-148">如果您的類別包含靜態欄位，請提供在載入類別時初始化它們的靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="4137f-148">If your class contains static fields, provide a static constructor that initializes them when the class is loaded.</span></span>  
  
 <span data-ttu-id="4137f-149">靜態方法的呼叫會使用 Microsoft Intermediate Language (MSIL) 產生呼叫指令，而執行個體方法的呼叫會產生 `callvirt` 指令，這也會檢查是否有 Null 物件參考。</span><span class="sxs-lookup"><span data-stu-id="4137f-149">A call to a static method generates a call instruction in Microsoft intermediate language (MSIL), whereas a call to an instance method generates a `callvirt` instruction, which also checks for a null object references.</span></span> <span data-ttu-id="4137f-150">不過，大部分的時間，兩者之間的效能差異並不明顯。</span><span class="sxs-lookup"><span data-stu-id="4137f-150">However, most of the time the performance difference between the two is not significant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4137f-151">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4137f-151">C# Language Specification</span></span>  

<span data-ttu-id="4137f-152">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[靜態類別](~/_csharplang/spec/classes.md#static-classes)與[靜態和執行個體的成員](~/_csharplang/spec/classes.md#static-and-instance-members)。</span><span class="sxs-lookup"><span data-stu-id="4137f-152">For more information, see [Static classes](~/_csharplang/spec/classes.md#static-classes) and [Static and instance members](~/_csharplang/spec/classes.md#static-and-instance-members) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="4137f-153">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="4137f-153">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4137f-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4137f-154">See also</span></span>

- [<span data-ttu-id="4137f-155">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4137f-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4137f-156">static</span><span class="sxs-lookup"><span data-stu-id="4137f-156">static</span></span>](../../../csharp/language-reference/keywords/static.md)
- [<span data-ttu-id="4137f-157">類別</span><span class="sxs-lookup"><span data-stu-id="4137f-157">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="4137f-158">class</span><span class="sxs-lookup"><span data-stu-id="4137f-158">class</span></span>](../../../csharp/language-reference/keywords/class.md)
- [<span data-ttu-id="4137f-159">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="4137f-159">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)
- [<span data-ttu-id="4137f-160">執行個體建構函式</span><span class="sxs-lookup"><span data-stu-id="4137f-160">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
