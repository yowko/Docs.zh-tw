---
title: nameof - C# 參考
ms.custom: seodec18
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 61c0744168a6fef0f8c8cfb589602e7aeff0c48b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241482"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="417b5-102">nameof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="417b5-102">nameof (C# Reference)</span></span>

<span data-ttu-id="417b5-103">用來取得變數、類型或成員的簡單 (不完整) 字串名稱。</span><span class="sxs-lookup"><span data-stu-id="417b5-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>  

<span data-ttu-id="417b5-104">因程式碼發生錯誤、錯誤與模型檢視控制器 (MVC) 連結相互連接，或者錯誤引發了屬性變更事件等狀況而進行回報時，通常還需要擷取方法的字串名稱。</span><span class="sxs-lookup"><span data-stu-id="417b5-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="417b5-105">使用 `nameof` 可協助您在重新命名定義時保持程式碼有效。</span><span class="sxs-lookup"><span data-stu-id="417b5-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="417b5-106">之前，您必須使用字串常值來參考定義，這在重新命名程式碼項目時很容易損毀，因為工具不知道要檢查這些字串常值。</span><span class="sxs-lookup"><span data-stu-id="417b5-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>  
  
 <span data-ttu-id="417b5-107">`nameof` 運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="417b5-107">A `nameof` expression has this form:</span></span>  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a><span data-ttu-id="417b5-108">主要使用案例</span><span class="sxs-lookup"><span data-stu-id="417b5-108">Key Use Cases</span></span>  
 <span data-ttu-id="417b5-109">下列範例顯示 `nameof` 的主要使用案例。</span><span class="sxs-lookup"><span data-stu-id="417b5-109">These examples show the key use cases for `nameof`.</span></span>  
  
 <span data-ttu-id="417b5-110">驗證參數：</span><span class="sxs-lookup"><span data-stu-id="417b5-110">Validate parameters:</span></span>  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 <span data-ttu-id="417b5-111">MVC 動作連結：</span><span class="sxs-lookup"><span data-stu-id="417b5-111">MVC Action links:</span></span>  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 <span data-ttu-id="417b5-112">INotifyPropertyChanged：</span><span class="sxs-lookup"><span data-stu-id="417b5-112">INotifyPropertyChanged:</span></span>  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 <span data-ttu-id="417b5-113">XAML 相依性屬性：</span><span class="sxs-lookup"><span data-stu-id="417b5-113">XAML dependency property:</span></span>  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 <span data-ttu-id="417b5-114">記錄：</span><span class="sxs-lookup"><span data-stu-id="417b5-114">Logging:</span></span>  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 <span data-ttu-id="417b5-115">屬性: </span><span class="sxs-lookup"><span data-stu-id="417b5-115">Attributes:</span></span>  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a><span data-ttu-id="417b5-116">範例</span><span class="sxs-lookup"><span data-stu-id="417b5-116">Examples</span></span>  
 <span data-ttu-id="417b5-117">以下是一些 C# 範例：</span><span class="sxs-lookup"><span data-stu-id="417b5-117">Some C# examples:</span></span>  
  
```csharp  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
class Test {  
    static void Main (string[] args) {  
        Console.WriteLine(nameof(C)); // -> "C"  
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"  
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"  
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]  
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"  
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]  
        Console.WriteLine(nameof(f)); // -> "f"  
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]  
        // Console.WriteLine(nameof(f<>)); -> [syntax error]  
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]  
    }
}
```  
  
## <a name="remarks"></a><span data-ttu-id="417b5-118">備註</span><span class="sxs-lookup"><span data-stu-id="417b5-118">Remarks</span></span>  
 <span data-ttu-id="417b5-119">傳遞給 `nameof` 的引數必須是簡單名稱、限定名稱、成員存取、指定成員的基底存取，或指定成員的這項存取。</span><span class="sxs-lookup"><span data-stu-id="417b5-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="417b5-120">引數運算式會識別程式碼定義，但永遠不會加以評估。</span><span class="sxs-lookup"><span data-stu-id="417b5-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>  
  
 <span data-ttu-id="417b5-121">由於引數必須是運算式語法，因此不允許使用許多對清單沒有幫助的項目。</span><span class="sxs-lookup"><span data-stu-id="417b5-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="417b5-122">下列項目可能會產生錯誤，值得留意：預先定義的類型 (例如 `int` 或 `void`)、可為 Null 的類型 (`Point?`)、陣列類型 (`Customer[,]`)、指標類型 (`Buffer*`)、限定別名 (`A::B`)、未繫結的泛型類型 (`Dictionary<,>`)、前置處理符號 (`DEBUG`)，以及標籤 (`loop:`)。</span><span class="sxs-lookup"><span data-stu-id="417b5-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>  
  
 <span data-ttu-id="417b5-123">如果您需要取得完整限定名稱，您可以搭配使用 `typeof` 運算式和 `nameof`。</span><span class="sxs-lookup"><span data-stu-id="417b5-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="417b5-124">例如：</span><span class="sxs-lookup"><span data-stu-id="417b5-124">For example:</span></span>
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 <span data-ttu-id="417b5-125">可惜，`typeof` 不是 `nameof` 這類常數運算式，因此 `typeof` 不能在 `nameof` 的所有相同位置中搭配使用 `nameof`。</span><span class="sxs-lookup"><span data-stu-id="417b5-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="417b5-126">例如，下列情況會導致 CS0182 編譯錯誤：</span><span class="sxs-lookup"><span data-stu-id="417b5-126">For example, the following would cause a CS0182 compile error:</span></span>
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 <span data-ttu-id="417b5-127">報告中有幾個項目能告知我們可能需要處理的問題。</span><span class="sxs-lookup"><span data-stu-id="417b5-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="417b5-128">不同於經評估的運算式規定，您不需要具有類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="417b5-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="417b5-129">在某些情況下使用類型名稱會很方便，由於您只參考名稱而不使用執行個體資料，因此不需要設計執行個體變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="417b5-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>  
  
 <span data-ttu-id="417b5-130">您可以在類別的屬性運算式中參考該類別的成員。</span><span class="sxs-lookup"><span data-stu-id="417b5-130">You can reference the members of a class in attribute expressions on the class.</span></span>  
  
 <span data-ttu-id="417b5-131">您無法取得簽章資訊，例如 "`Method1 (str, str)`"。</span><span class="sxs-lookup"><span data-stu-id="417b5-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="417b5-132">若要執行這項操作，其中一個方法是使用運算式 `Expression e = () => A.B.Method1("s1", "s2")`，然後從產生的運算式樹狀架構中提取 MemberInfo。</span><span class="sxs-lookup"><span data-stu-id="417b5-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="417b5-133">語言規格</span><span class="sxs-lookup"><span data-stu-id="417b5-133">Language Specifications</span></span>  

<span data-ttu-id="417b5-134">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)中的 [Nameof 運算式](~/_csharplang/spec/expressions.md#nameof-expressions)。</span><span class="sxs-lookup"><span data-stu-id="417b5-134">For more information, see [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="417b5-135">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="417b5-135">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="417b5-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="417b5-136">See Also</span></span>

- [<span data-ttu-id="417b5-137">C# 參考</span><span class="sxs-lookup"><span data-stu-id="417b5-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="417b5-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="417b5-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="417b5-139">typeof</span><span class="sxs-lookup"><span data-stu-id="417b5-139">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
