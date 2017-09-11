---
title: "如何：使用命令列建立和使用組件 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 630a799331e03860fbee34eab6bea3bb594ef0f0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="ab1c9-102">如何：使用命令列建立和使用組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="ab1c9-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="ab1c9-103">組件又稱為動態連結程式庫 (DLL)，會在執行階段連結到您的程式。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="ab1c9-104">為了示範如何建立和使用 DLL，請考慮下列案例：</span><span class="sxs-lookup"><span data-stu-id="ab1c9-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="ab1c9-105">`MathLibrary.DLL`︰包含要在執行階段呼叫之方法的程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="ab1c9-106">在此範例中，DLL 包含兩個方法︰`Add` 和 `Multiply`。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="ab1c9-107">`Add`：包含 `Add` 方法的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="ab1c9-108">它會傳回其參數的總和。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="ab1c9-109">包含 `Add` 方法的 `AddClass` 類別是命名空間 `UtilityMethods` 的成員。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="ab1c9-110">`Mult`：包含 `Multiply` 方法的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="ab1c9-111">它會傳回其參數的乘積。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-111">It returns the product of its parameters.</span></span> <span data-ttu-id="ab1c9-112">包含 `Multiply` 方法的 `MultiplyClass` 類別也是命名空間 `UtilityMethods` 的成員。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="ab1c9-113">`TestCode`：包含 `Main` 方法的檔案。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="ab1c9-114">它使用 DLL 檔案中的方法來計算執行階段引數的總和與乘積。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab1c9-115">範例</span><span class="sxs-lookup"><span data-stu-id="ab1c9-115">Example</span></span>  
  
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
  
 <span data-ttu-id="ab1c9-116">此檔案包含使用 DLL 方法 `Add` 和 `Multiply` 的演算法。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="ab1c9-117">一開始會剖析從命令列輸入的引數 `num1` 和 `num2`。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="ab1c9-118">然後會使用 `AddClass` 類別中的 `Add` 方法計算總和，並使用 `MultiplyClass` 類別中的 `Multiply` 方法計算乘積。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="ab1c9-119">請注意，檔案開頭的 `using` 指示詞可讓您使用未限定的類別名稱，在編譯時期參考 DLL 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab1c9-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="ab1c9-120">否則，您必須使用完整名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab1c9-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="ab1c9-121">執行</span><span class="sxs-lookup"><span data-stu-id="ab1c9-121">Execution</span></span>  
 <span data-ttu-id="ab1c9-122">若要執行此程式，請輸入 EXE 檔案的名稱，後面接著兩個數字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab1c9-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ab1c9-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ab1c9-123">Compiling the Code</span></span>  
 <span data-ttu-id="ab1c9-124">若要建立 `MathLibrary.DLL` 檔案，請使用下列命令列編譯 `Add` 和 `Mult` 這兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 <span data-ttu-id="ab1c9-125">[/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) 編譯器選項會指示編譯器輸出 DLL，而不是 EXE 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-125">The [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="ab1c9-126">使用 [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) 編譯器選項，後面接著檔案名稱，即可指定 DLL 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-126">The [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="ab1c9-127">否則，編譯器會使用第一個檔案 (`Add.cs`) 作為 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-127">Otherwise, the compiler uses the first file (`Add.cs`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="ab1c9-128">若要建立可執行檔 `TestCode.exe`，請使用下列命令列：</span><span class="sxs-lookup"><span data-stu-id="ab1c9-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 <span data-ttu-id="ab1c9-129">**/out** 編譯器選項會指示編譯器輸出 EXE 檔案，並指定輸出檔案的名稱 (`TestCode.exe`)。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="ab1c9-130">這個編譯器選項是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-130">This compiler option is optional.</span></span> <span data-ttu-id="ab1c9-131">[/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 編譯器選項會指定此程式所使用的一或多個 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-131">The [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option specifies the DLL file or files that this program uses.</span></span> <span data-ttu-id="ab1c9-132">如需詳細資訊，請參閱 [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-132">For more information, see [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="ab1c9-133">如需從命令列建立的詳細資訊，請參閱[使用 csc.exe 建置命令列](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="ab1c9-133">For more information about building from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1c9-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab1c9-134">See Also</span></span>  
 <span data-ttu-id="ab1c9-135">[C# 程式設計手冊](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab1c9-135">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ab1c9-136">[組件和全域組件快取 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab1c9-136">[Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
 [<span data-ttu-id="ab1c9-137">建立類別以包裝 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="ab1c9-137">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

