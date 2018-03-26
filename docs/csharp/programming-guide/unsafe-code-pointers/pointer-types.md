---
title: 指標類型 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe7b926bdf9f662d25f2fe960b51fc8254b7aa3a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="e813b-102">指標類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e813b-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="e813b-103">在 unsafe 內容中，類型有可能是指標類型、實值類型或參考類型。</span><span class="sxs-lookup"><span data-stu-id="e813b-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="e813b-104">指標類型宣告會使用下列其中一種格式：</span><span class="sxs-lookup"><span data-stu-id="e813b-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="e813b-105">下列任何一種類型都可能是指標類型：</span><span class="sxs-lookup"><span data-stu-id="e813b-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="e813b-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[char](../../../csharp/language-reference/keywords/char.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="e813b-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="e813b-107">任何 [enum](../../../csharp/language-reference/keywords/enum.md) 型別。</span><span class="sxs-lookup"><span data-stu-id="e813b-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="e813b-108">任何指標類型。</span><span class="sxs-lookup"><span data-stu-id="e813b-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="e813b-109">任何只包含 Unmanaged 類型欄位的使用者定義結構類型。</span><span class="sxs-lookup"><span data-stu-id="e813b-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="e813b-110">指標型別不會從 [object](../../../csharp/language-reference/keywords/object.md) 繼承，而且指標型別與 `object` 之間無法進行轉換。</span><span class="sxs-lookup"><span data-stu-id="e813b-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="e813b-111">此外，boxing 和 unboxing 不支援指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="e813b-112">不過，不同的指標類型之間以及指標類型與整數類資料類型之間可以進行轉換。</span><span class="sxs-lookup"><span data-stu-id="e813b-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="e813b-113">當您在相同的宣告中宣告多個指標時，星號 (\*) 只會與基礎類型一起出現，而不會做為每個指標名稱的前置詞使用。</span><span class="sxs-lookup"><span data-stu-id="e813b-113">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="e813b-114">例如: </span><span class="sxs-lookup"><span data-stu-id="e813b-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="e813b-115">指標無法指向參考或包含參考的 [struct](../../../csharp/language-reference/keywords/struct.md)，因為即使指標指向物件參考，依然可以對物件參考進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="e813b-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="e813b-116">記憶體回收行程不會持續追蹤是否有任何指標類型指向物件。</span><span class="sxs-lookup"><span data-stu-id="e813b-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="e813b-117">`myType*` 類型的指標變數值是 `myType` 類型變數的位址。</span><span class="sxs-lookup"><span data-stu-id="e813b-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="e813b-118">以下是指標類型宣告的範例：</span><span class="sxs-lookup"><span data-stu-id="e813b-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="e813b-119">範例</span><span class="sxs-lookup"><span data-stu-id="e813b-119">Example</span></span>|<span data-ttu-id="e813b-120">描述</span><span class="sxs-lookup"><span data-stu-id="e813b-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="e813b-121">`p` 為整數的指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="e813b-122">`p` 為整數指標的指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="e813b-123">`p` 為整數的一維陣列指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="e813b-124">`p` 為字元的指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="e813b-125">`p` 為未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="e813b-126">您可以使用指標間接運算子 \* 存取指標變數所指向位置的內容。</span><span class="sxs-lookup"><span data-stu-id="e813b-126">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="e813b-127">例如，請參考下列宣告：</span><span class="sxs-lookup"><span data-stu-id="e813b-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="e813b-128">這個運算式 `*myVariable` 表示位於 `int` 所包含之位址的 `myVariable` 變數。</span><span class="sxs-lookup"><span data-stu-id="e813b-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="e813b-129">[fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)和[指標轉換](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)主題中有數個指標範例。</span><span class="sxs-lookup"><span data-stu-id="e813b-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="e813b-130">下列範例將示範 `unsafe` 關鍵字和 `fixed` 陳述式的需求，以及如何讓內部指標遞增。</span><span class="sxs-lookup"><span data-stu-id="e813b-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="e813b-131">您可以將這個程式碼貼入主控台應用程式的 Main 函式中來執行它 </span><span class="sxs-lookup"><span data-stu-id="e813b-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="e813b-132">(記得在 [專案設計工具] 中啟用 Unsafe 程式碼、在功能表列上選擇 [專案]、[屬性]，然後選取 [組建] 索引標籤上的 [容許 Unsafe 程式碼])。</span><span class="sxs-lookup"><span data-stu-id="e813b-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="e813b-133">您無法將間接運算子套用至 `void*` 類型的指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="e813b-134">不過，您可以使用轉型，將 Void 指標轉換成任何其他指標類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e813b-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="e813b-135">指標可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="e813b-135">A pointer can be `null`.</span></span> <span data-ttu-id="e813b-136">將間接運算子套用至 null 指標會產生實作定義的行為。</span><span class="sxs-lookup"><span data-stu-id="e813b-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="e813b-137">請注意，在方法之間傳遞指標時，可能會導致未定義的行為。</span><span class="sxs-lookup"><span data-stu-id="e813b-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="e813b-138">請考慮使用透過 `in`、`out` 或 `ref` 參數或是以為函式結果的方式，將指標傳至區域變數的方法。</span><span class="sxs-lookup"><span data-stu-id="e813b-138">Consider a method that returns a pointer to a local variable through an `in`, `out` or `ref` parameter or as the function result.</span></span> <span data-ttu-id="e813b-139">如果已在固定區塊中設定指標，則該指標指向的變數就可能不再是固定的。</span><span class="sxs-lookup"><span data-stu-id="e813b-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="e813b-140">下表所列出的運算子和陳述式可以用於 unsafe 內容中的指標：</span><span class="sxs-lookup"><span data-stu-id="e813b-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="e813b-141">運算子/陳述式</span><span class="sxs-lookup"><span data-stu-id="e813b-141">Operator/Statement</span></span>|<span data-ttu-id="e813b-142">使用</span><span class="sxs-lookup"><span data-stu-id="e813b-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="e813b-143">執行指標間接取值。</span><span class="sxs-lookup"><span data-stu-id="e813b-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="e813b-144">透過指標存取結構的成員。</span><span class="sxs-lookup"><span data-stu-id="e813b-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="e813b-145">[]</span><span class="sxs-lookup"><span data-stu-id="e813b-145">[]</span></span>|<span data-ttu-id="e813b-146">索引指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="e813b-147">取得變數位址。</span><span class="sxs-lookup"><span data-stu-id="e813b-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="e813b-148">++ 和 --</span><span class="sxs-lookup"><span data-stu-id="e813b-148">++ and --</span></span>|<span data-ttu-id="e813b-149">遞增和遞減指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="e813b-150">+ 和 -</span><span class="sxs-lookup"><span data-stu-id="e813b-150">+ and -</span></span>|<span data-ttu-id="e813b-151">執行指標算術。</span><span class="sxs-lookup"><span data-stu-id="e813b-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="e813b-152">==、!=、\<、>、\<= 和 >=</span><span class="sxs-lookup"><span data-stu-id="e813b-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="e813b-153">比較指標。</span><span class="sxs-lookup"><span data-stu-id="e813b-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="e813b-154">在堆疊上配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="e813b-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="e813b-155">`fixed` 陳述式</span><span class="sxs-lookup"><span data-stu-id="e813b-155">`fixed` statement</span></span>|<span data-ttu-id="e813b-156">暫時固定變數以便找到其位址。</span><span class="sxs-lookup"><span data-stu-id="e813b-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="e813b-157">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e813b-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e813b-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e813b-158">See Also</span></span>  
 [<span data-ttu-id="e813b-159">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e813b-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e813b-160">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="e813b-160">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="e813b-161">指標轉換</span><span class="sxs-lookup"><span data-stu-id="e813b-161">Pointer Conversions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [<span data-ttu-id="e813b-162">指標運算式</span><span class="sxs-lookup"><span data-stu-id="e813b-162">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="e813b-163">型別</span><span class="sxs-lookup"><span data-stu-id="e813b-163">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="e813b-164">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="e813b-164">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="e813b-165">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="e813b-165">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="e813b-166">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e813b-166">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)  
 [<span data-ttu-id="e813b-167">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="e813b-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
