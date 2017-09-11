---
title: "方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 8cf67ed9771a5eb311909e1067aeb39659283d2b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="318d6-102">方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="318d6-102">Methods (C# Programming Guide)</span></span>
<span data-ttu-id="318d6-103">方法是包含一系列陳述式的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="318d6-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="318d6-104">程式會造成呼叫方法並指定任何所需的方法引數來執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="318d6-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="318d6-105">在 C# 中，每個執行的指示是在方法的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="318d6-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="318d6-106">Main 方法是每個 C# 應用程式的進入點，而且它是由 Common Language Runtime (CLR) 啟動程式時呼叫。</span><span class="sxs-lookup"><span data-stu-id="318d6-106">The Main method is the entry point for every C# application and it is called by the common language runtime (CLR) when the program is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="318d6-107">本主題討論具名的方法。</span><span class="sxs-lookup"><span data-stu-id="318d6-107">This topic discusses named methods.</span></span> <span data-ttu-id="318d6-108">如需匿名函式的資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="318d6-108">For information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="method-signatures"></a><span data-ttu-id="318d6-109">方法簽章</span><span class="sxs-lookup"><span data-stu-id="318d6-109">Method Signatures</span></span>  
 <span data-ttu-id="318d6-110">方法是在 [類別](../../../csharp/language-reference/keywords/class.md) 或 [結構](../../../csharp/language-reference/keywords/struct.md) 中宣告，透過指定存取層級 (例如 `public` 或 `private`)、選擇性修飾詞 (例如 `abstract` 或 `sealed`)、傳回值、方法的名稱，以及任何方法參數。</span><span class="sxs-lookup"><span data-stu-id="318d6-110">Methods are declared in a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="318d6-111">這些部份放在一起即為方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="318d6-111">These parts together are the signature of the method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="318d6-112">方法的傳回類型不是方法多載用途的方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="318d6-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="318d6-113">不過，在判斷委派與所指向的方法之間的相容性時，它是方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="318d6-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>  
  
 <span data-ttu-id="318d6-114">方法參數會放在括號中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="318d6-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="318d6-115">空括號表示方法不需要任何參數。</span><span class="sxs-lookup"><span data-stu-id="318d6-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="318d6-116">這個類別包含三個方法：</span><span class="sxs-lookup"><span data-stu-id="318d6-116">This class contains three methods:</span></span>  
  
 <span data-ttu-id="318d6-117">[!code-cs[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-117">[!code-cs[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]</span></span>  
  
## <a name="method-access"></a><span data-ttu-id="318d6-118">方法存取</span><span class="sxs-lookup"><span data-stu-id="318d6-118">Method Access</span></span>  
 <span data-ttu-id="318d6-119">在物件上呼叫方法，就像是存取欄位。</span><span class="sxs-lookup"><span data-stu-id="318d6-119">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="318d6-120">在物件名稱後面加上句點、方法的名稱與括號。</span><span class="sxs-lookup"><span data-stu-id="318d6-120">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="318d6-121">引數會在括號中列出，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="318d6-121">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="318d6-122">因此可以如下列範例所示呼叫 `Motorcycle` 類別的方法：</span><span class="sxs-lookup"><span data-stu-id="318d6-122">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>  
  
 <span data-ttu-id="318d6-123">[!code-cs[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-123">[!code-cs[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]</span></span>  
  
## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="318d6-124">方法參數與引數</span><span class="sxs-lookup"><span data-stu-id="318d6-124">Method Parameters vs. Arguments</span></span>  
 <span data-ttu-id="318d6-125">方法定義會指定所需的任何參數的名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="318d6-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="318d6-126">在呼叫程式碼呼叫此方法時，它會提供對每個參數呼叫的引數的具體值。</span><span class="sxs-lookup"><span data-stu-id="318d6-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="318d6-127">引數都必須與參數類型相容，呼叫程式碼中使用的引數名稱 (如果有的話) 不需要與方法中定義的具名參數相同。</span><span class="sxs-lookup"><span data-stu-id="318d6-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code does not have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="318d6-128">例如: </span><span class="sxs-lookup"><span data-stu-id="318d6-128">For example:</span></span>  
  
 <span data-ttu-id="318d6-129">[!code-cs[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-129">[!code-cs[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]</span></span>  
  
## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="318d6-130">以傳址方式傳遞與以傳值方式傳遞</span><span class="sxs-lookup"><span data-stu-id="318d6-130">Passing by Reference vs. Passing by Value</span></span>  
 <span data-ttu-id="318d6-131">根據預設，傳遞實值類型至方法時，會傳遞複本，而不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="318d6-131">By default, when a value type is passed to a method, a copy is passed instead of the object itself.</span></span> <span data-ttu-id="318d6-132">因此，對引數的變更對於呼叫方法中的原始複本不會有影響。</span><span class="sxs-lookup"><span data-stu-id="318d6-132">Therefore, changes to the argument have no effect on the original copy in the calling method.</span></span> <span data-ttu-id="318d6-133">您可以使用 ref 關鍵字依參考傳遞實值類型。</span><span class="sxs-lookup"><span data-stu-id="318d6-133">You can pass a value-type by reference by using the ref keyword.</span></span> <span data-ttu-id="318d6-134">如需詳細資訊，請參閱[傳遞實值型別參數](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="318d6-134">For more information, see [Passing Value-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md).</span></span> <span data-ttu-id="318d6-135">如需內建實值型別的清單，請參閱[實值型別表](../../../csharp/language-reference/keywords/value-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="318d6-135">For a list of built-in value types, see [Value Types Table](../../../csharp/language-reference/keywords/value-types-table.md).</span></span>  
  
 <span data-ttu-id="318d6-136">傳遞參考類型的物件至方法時，會傳遞物件的參考。</span><span class="sxs-lookup"><span data-stu-id="318d6-136">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="318d6-137">也就是說，此方法接收的不是物件本身，而是指出物件位置的引數。</span><span class="sxs-lookup"><span data-stu-id="318d6-137">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="318d6-138">如果您使用此參考變更物件的成員，變更會反映在呼叫方法的引數中，即使以傳值方式傳遞物件。</span><span class="sxs-lookup"><span data-stu-id="318d6-138">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>  
  
 <span data-ttu-id="318d6-139">您會使用 `class` 關鍵字建立參考類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="318d6-139">You create a reference type by using the `class` keyword, as the following example shows.</span></span>  
  
 <span data-ttu-id="318d6-140">[!code-cs[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-140">[!code-cs[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]</span></span>  
  
 <span data-ttu-id="318d6-141">現在，如果您將此類型為基礎的物件傳遞至方法，即會傳遞物件的參考。</span><span class="sxs-lookup"><span data-stu-id="318d6-141">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="318d6-142">下列範例會將類型 `SampleRefType` 的物件傳遞至方法 `ModifyObject`。</span><span class="sxs-lookup"><span data-stu-id="318d6-142">The following example passes an object of type `SampleRefType` to method `ModifyObject`.</span></span>  
  
 <span data-ttu-id="318d6-143">[!code-cs[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-143">[!code-cs[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]</span></span>  
  
 <span data-ttu-id="318d6-144">此範例會執行與上一個範例基本上相同的動作，依傳值方式將引數傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="318d6-144">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="318d6-145">但是，由於使用參考類型，結果會不同。</span><span class="sxs-lookup"><span data-stu-id="318d6-145">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="318d6-146">`ModifyObject` 中對參數 `value` 的 `obj`欄位做的修改，也會變更 `value` 方法中引數 `rt`的 `TestRefType` 欄位。</span><span class="sxs-lookup"><span data-stu-id="318d6-146">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="318d6-147">`TestRefType` 方法會顯示 33 做為輸出。</span><span class="sxs-lookup"><span data-stu-id="318d6-147">The `TestRefType` method displays 33 as the output.</span></span>  
  
 <span data-ttu-id="318d6-148">如需如何依傳址和依傳值方式來傳遞參考型別的詳細資訊，請參閱[傳遞參考型別參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)和[參考型別](../../../csharp/language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="318d6-148">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) and [Reference Types](../../../csharp/language-reference/keywords/reference-types.md).</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="318d6-149">傳回值</span><span class="sxs-lookup"><span data-stu-id="318d6-149">Return Values</span></span>  
 <span data-ttu-id="318d6-150">方法可以傳回值給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="318d6-150">Methods can return a value to the caller.</span></span> <span data-ttu-id="318d6-151">針對傳回類型，如果列在方法名稱前面的類型不是 `void`，方法可以使用 `return` 關鍵字傳回值。</span><span class="sxs-lookup"><span data-stu-id="318d6-151">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="318d6-152">具有 `return` 關鍵字後面接著符合傳回類型值的陳述式，會將該值傳回給方法呼叫者。</span><span class="sxs-lookup"><span data-stu-id="318d6-152">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span> <span data-ttu-id="318d6-153">`return` 關鍵字也會停止執行方法。</span><span class="sxs-lookup"><span data-stu-id="318d6-153">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="318d6-154">如果傳回類型為 `void`，不含值的 `return` 陳述式對於停止方法的執行仍很有用。</span><span class="sxs-lookup"><span data-stu-id="318d6-154">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="318d6-155">若沒有 `return` 關鍵字，在方法到達程式碼區塊的結尾時，方法將會停止執行。</span><span class="sxs-lookup"><span data-stu-id="318d6-155">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="318d6-156">具有非 void 傳回類型的方法需要使用 `return` 關鍵字以傳回值。</span><span class="sxs-lookup"><span data-stu-id="318d6-156">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="318d6-157">例如，這兩種方法使用 `return` 關鍵字傳回整數：</span><span class="sxs-lookup"><span data-stu-id="318d6-157">For example, these two methods use the `return` keyword to return integers:</span></span>  
  
 <span data-ttu-id="318d6-158">[!code-cs[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-158">[!code-cs[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]</span></span>  
  
 <span data-ttu-id="318d6-159">若要使用從方法傳回的值，呼叫方法可以在使用相同類型值的任意位置使用方法呼叫本身即已足夠。</span><span class="sxs-lookup"><span data-stu-id="318d6-159">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="318d6-160">您也可以指派傳回值給變數。</span><span class="sxs-lookup"><span data-stu-id="318d6-160">You can also assign the return value to a variable.</span></span> <span data-ttu-id="318d6-161">例如，下列兩個程式碼範例會達到相同的目標：</span><span class="sxs-lookup"><span data-stu-id="318d6-161">For example, the following two code examples accomplish the same goal:</span></span>  
  
 <span data-ttu-id="318d6-162">[!code-cs[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-162">[!code-cs[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]</span></span>  
  
 <span data-ttu-id="318d6-163">[!code-cs[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-163">[!code-cs[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]</span></span>  
  
 <span data-ttu-id="318d6-164">使用區域變數，在此情況下的 `result`來儲存值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="318d6-164">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="318d6-165">它有助於程式碼的可讀性，或如果您需要儲存方法的整個範圍引數的原始值，則可能為必要。</span><span class="sxs-lookup"><span data-stu-id="318d6-165">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>  
  
 <span data-ttu-id="318d6-166">如果呼叫端函式將多維陣列傳遞給可修改陣列內容的方法 M，則不需要從 M 傳回該陣列。您可能會從 M 傳回產生的陣列，而產生的陣列具有良好樣式或功能流程的值，但並不需要。</span><span class="sxs-lookup"><span data-stu-id="318d6-166">Returning a multi-dimensional array from a method, M, that modifies the array's contents is not necessary if the calling function passed the array into M.  You may return the resulting array from M for good style or functional flow of values, but it is not necessary.</span></span>  <span data-ttu-id="318d6-167">這是因為 C# 會以傳值方式傳遞所有參考型別，而陣列參考的值是陣列的指標，因此您不需要傳回已修改的陣列。</span><span class="sxs-lookup"><span data-stu-id="318d6-167">The reason you don't need to return the modified array is that C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="318d6-168">在方法 M 中，任何陣列內容變更都可以透過任何具有陣列參考的程式碼觀察到，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="318d6-168">In the method M, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example.</span></span>  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
```  
  
 <span data-ttu-id="318d6-169">如需詳細資訊，請參閱 [return](../../../csharp/language-reference/keywords/return.md)。</span><span class="sxs-lookup"><span data-stu-id="318d6-169">For more information, see [return](../../../csharp/language-reference/keywords/return.md).</span></span>  
  
## <a name="async-methods"></a><span data-ttu-id="318d6-170">非同步方法</span><span class="sxs-lookup"><span data-stu-id="318d6-170">Async Methods</span></span>  
 <span data-ttu-id="318d6-171">使用非同步功能，您就可以呼叫非同步方法，而不需要使用明確回呼或手動將您的程式碼分散到多種方法或 lambda 運算式上。</span><span class="sxs-lookup"><span data-stu-id="318d6-171">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span> 
  
 <span data-ttu-id="318d6-172">如果您使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞來標示方法，可以在方法中使用 [await](../../../csharp/language-reference/keywords/await.md) 運算子。</span><span class="sxs-lookup"><span data-stu-id="318d6-172">If you mark a method with the [async](../../../csharp/language-reference/keywords/async.md) modifier, you can use the [await](../../../csharp/language-reference/keywords/await.md) operator in the method.</span></span> <span data-ttu-id="318d6-173">當控制項到達 async 方法的 await 運算式時，控制項會傳回給呼叫者，方法中的進度會暫停，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="318d6-173">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="318d6-174">當工作完成時，方法中的執行可以繼續。</span><span class="sxs-lookup"><span data-stu-id="318d6-174">When the task is complete, execution can resume in the method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="318d6-175">非同步方法會在遇到第一個未完成的等候物件或是到達非同步方法的結尾時 (以先發生者為準)，傳回呼叫者</span><span class="sxs-lookup"><span data-stu-id="318d6-175">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>  
  
 <span data-ttu-id="318d6-176">非同步方法的傳回類型可以是 <xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task> 或 void。</span><span class="sxs-lookup"><span data-stu-id="318d6-176">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="318d6-177">void 傳回類型主要用於定義需要 void 傳回類型的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="318d6-177">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="318d6-178">傳回 void 類型的非同步方法無法等候，而且 void 傳回方法的呼叫者無法攔截方法擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="318d6-178">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="318d6-179">在下列範例中，`DelayAsync` 是會傳回類型 <xref:System.Threading.Tasks.Task%601> 的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="318d6-179">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="318d6-180">`DelayAsync` 具有傳回整數的 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="318d6-180">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="318d6-181">因此 `DelayAsync` 的方法宣告必須具有傳回類型 `Task<int>`。</span><span class="sxs-lookup"><span data-stu-id="318d6-181">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="318d6-182">因為傳回類型是 `Task<int>`， `await` 中 `DoSomethingAsync` 運算式的評估會產生整數，如下列陳述式所示範： `int result = await delayTask`。</span><span class="sxs-lookup"><span data-stu-id="318d6-182">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>  
  
 <span data-ttu-id="318d6-183">`startButton_Click` 方法是傳回類型為 void 的非同步方法的範例。</span><span class="sxs-lookup"><span data-stu-id="318d6-183">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="318d6-184">因為 `DoSomethingAsync` 是非同步方法，對 `DoSomethingAsync` 的呼叫工作必須等候，如下列陳述式所示： `await DoSomethingAsync();`。</span><span class="sxs-lookup"><span data-stu-id="318d6-184">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="318d6-185">`startButton_Click` 方法都必須定義 `async` 修飾詞，因為方法有 `await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="318d6-185">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>  
  
 <span data-ttu-id="318d6-186">[!code-cs[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="318d6-186">[!code-cs[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]</span></span>  
  
 <span data-ttu-id="318d6-187">非同步方法不可以宣告任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數，但是可以呼叫具有這類參數的方法。</span><span class="sxs-lookup"><span data-stu-id="318d6-187">An async method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, but it can call methods that have such parameters.</span></span>  
  
 <span data-ttu-id="318d6-188">如需非同步方法的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回型別](../../../csharp/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="318d6-188">For more information about async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="318d6-189">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="318d6-189">Expression Body Definitions</span></span>  
 <span data-ttu-id="318d6-190">方法定義只是立即傳回運算式的結果，或是具有單一陳述式做為方法的主體是很常見的。</span><span class="sxs-lookup"><span data-stu-id="318d6-190">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span>  <span data-ttu-id="318d6-191">使用 `=>`定義這類方法有個語法捷徑：</span><span class="sxs-lookup"><span data-stu-id="318d6-191">There is a syntax shortcut for defining such methods using `=>`:</span></span>  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 <span data-ttu-id="318d6-192">如果方法會傳回 `void` 或非同步方法，則方法的主體必須是陳述式運算式 (如同 lambda)。</span><span class="sxs-lookup"><span data-stu-id="318d6-192">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span>  <span data-ttu-id="318d6-193">若為屬性和索引子，它們必須是唯讀，因此您不應使用 `get` 存取子關鍵字。</span><span class="sxs-lookup"><span data-stu-id="318d6-193">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>  
  
## <a name="iterators"></a><span data-ttu-id="318d6-194">Iterator</span><span class="sxs-lookup"><span data-stu-id="318d6-194">Iterators</span></span>  
 <span data-ttu-id="318d6-195">迭代器會對集合執行自訂的反覆項目，例如清單或陣列。</span><span class="sxs-lookup"><span data-stu-id="318d6-195">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="318d6-196">迭代器會使用 [yield return](../../../csharp/language-reference/keywords/yield.md) 陳述式來一次傳回一個項目。</span><span class="sxs-lookup"><span data-stu-id="318d6-196">An iterator uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="318d6-197">當 [yield return](../../../csharp/language-reference/keywords/yield.md) 到達陳述式時，會記住在程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="318d6-197">When a [yield return](../../../csharp/language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="318d6-198">下一次呼叫迭代器時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="318d6-198">Execution is restarted from that location when the iterator is called the next time.</span></span>  
  
 <span data-ttu-id="318d6-199">您會使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式，透過用戶端程式碼呼叫迭代器。</span><span class="sxs-lookup"><span data-stu-id="318d6-199">You call an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
 <span data-ttu-id="318d6-200">迭代器的傳回類型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="318d6-200">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="318d6-201">如需詳細資訊，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="318d6-201">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="318d6-202">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="318d6-202">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="318d6-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="318d6-203">See Also</span></span>  
 <span data-ttu-id="318d6-204">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-204">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="318d6-205"> [類別和結構](index.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-205"> [Classes and Structs](index.md) </span></span>  
<span data-ttu-id="318d6-206"> [存取修飾詞](access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-206"> [Access Modifiers](access-modifiers.md) </span></span>  
<span data-ttu-id="318d6-207"> [靜態類別和靜態類別成員](static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-207"> [Static Classes and Static Class Members](static-classes-and-static-class-members.md) </span></span>  
<span data-ttu-id="318d6-208"> [繼承](inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-208"> [Inheritance](inheritance.md) </span></span>  
<span data-ttu-id="318d6-209"> [抽象和密封類別以及類別成員](abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-209"> [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md) </span></span>  
<span data-ttu-id="318d6-210"> [params](../../../csharp/language-reference/keywords/params.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-210"> [params](../../../csharp/language-reference/keywords/params.md) </span></span>  
<span data-ttu-id="318d6-211"> [return](../../../csharp/language-reference/keywords/return.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-211"> [return](../../../csharp/language-reference/keywords/return.md) </span></span>  
<span data-ttu-id="318d6-212"> [out](../../../csharp/language-reference/keywords/out.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-212"> [out](../../../csharp/language-reference/keywords/out.md) </span></span>  
<span data-ttu-id="318d6-213"> [ref](../../../csharp/language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="318d6-213"> [ref](../../../csharp/language-reference/keywords/ref.md) </span></span>  
<span data-ttu-id="318d6-214"> [傳遞參數](passing-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="318d6-214"> [Passing Parameters](passing-parameters.md)</span></span>

