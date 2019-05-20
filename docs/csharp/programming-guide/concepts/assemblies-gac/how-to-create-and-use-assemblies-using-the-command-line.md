---
title: 作法：使用命令列建立和使用組件 (C#)
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 12d23816b740816bd357c3c2ac57583f31bf3cb3
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586031"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="70e9a-102">作法：使用命令列建立和使用組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="70e9a-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="70e9a-103">組件又稱為動態連結程式庫 (DLL)，會在執行階段連結到您的程式。</span><span class="sxs-lookup"><span data-stu-id="70e9a-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="70e9a-104">為了示範如何建立和使用 DLL，請考慮下列案例：</span><span class="sxs-lookup"><span data-stu-id="70e9a-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="70e9a-105">`MathLibrary.DLL`：程式庫檔案，其中包含要在執行階段呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="70e9a-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="70e9a-106">在此範例中，DLL 包含兩個方法︰`Add` 和 `Multiply`。</span><span class="sxs-lookup"><span data-stu-id="70e9a-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="70e9a-107">`Add`：包含 `Add` 方法的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="70e9a-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="70e9a-108">它會傳回其參數的總和。</span><span class="sxs-lookup"><span data-stu-id="70e9a-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="70e9a-109">包含 `Add` 方法的 `AddClass` 類別是命名空間 `UtilityMethods` 的成員。</span><span class="sxs-lookup"><span data-stu-id="70e9a-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="70e9a-110">`Mult`：包含 `Multiply` 方法的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="70e9a-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="70e9a-111">它會傳回其參數的乘積。</span><span class="sxs-lookup"><span data-stu-id="70e9a-111">It returns the product of its parameters.</span></span> <span data-ttu-id="70e9a-112">包含 `Multiply` 方法的 `MultiplyClass` 類別也是命名空間 `UtilityMethods` 的成員。</span><span class="sxs-lookup"><span data-stu-id="70e9a-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="70e9a-113">`TestCode`：包含 `Main` 方法的檔案。</span><span class="sxs-lookup"><span data-stu-id="70e9a-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="70e9a-114">它使用 DLL 檔案中的方法來計算執行階段引數的總和與乘積。</span><span class="sxs-lookup"><span data-stu-id="70e9a-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70e9a-115">範例</span><span class="sxs-lookup"><span data-stu-id="70e9a-115">Example</span></span>  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 <span data-ttu-id="70e9a-116">此檔案包含使用 DLL 方法 `Add` 和 `Multiply` 的演算法。</span><span class="sxs-lookup"><span data-stu-id="70e9a-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="70e9a-117">一開始會剖析從命令列輸入的引數 `num1` 和 `num2`。</span><span class="sxs-lookup"><span data-stu-id="70e9a-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="70e9a-118">然後會使用 `AddClass` 類別中的 `Add` 方法計算總和，並使用 `MultiplyClass` 類別中的 `Multiply` 方法計算乘積。</span><span class="sxs-lookup"><span data-stu-id="70e9a-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="70e9a-119">請注意，檔案開頭的 `using` 指示詞可讓您使用未限定的類別名稱，在編譯時期參考 DLL 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70e9a-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="70e9a-120">否則，您必須使用完整名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70e9a-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="70e9a-121">執行</span><span class="sxs-lookup"><span data-stu-id="70e9a-121">Execution</span></span>  
 <span data-ttu-id="70e9a-122">若要執行此程式，請輸入 EXE 檔案的名稱，後面接著兩個數字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="70e9a-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a><span data-ttu-id="70e9a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70e9a-123">See also</span></span>

- [<span data-ttu-id="70e9a-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="70e9a-124">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="70e9a-125">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="70e9a-125">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="70e9a-126">建立類別以包裝 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="70e9a-126">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
