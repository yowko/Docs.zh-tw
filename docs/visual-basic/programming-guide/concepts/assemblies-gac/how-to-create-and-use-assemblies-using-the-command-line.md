---
title: "如何︰ 建立和使用組件︰ 使用命令列 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 69e9cab9dda1fefe8bee3dc46b541313d1d80e58
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="c907d-102">如何︰ 建立和使用組件︰ 使用命令列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c907d-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="c907d-103">組件或動態連結程式庫 (DLL)，會在執行階段連結至您的程式。</span><span class="sxs-lookup"><span data-stu-id="c907d-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="c907d-104">為了示範建置和使用 DLL，請考慮下列案例︰</span><span class="sxs-lookup"><span data-stu-id="c907d-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="c907d-105">`MathLibrary.DLL`︰ 包含要在執行階段呼叫的方法程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="c907d-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="c907d-106">在此範例中，DLL 包含兩個方法︰`Add`和`Multiply`。</span><span class="sxs-lookup"><span data-stu-id="c907d-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="c907d-107">`Add`: 包含方法的原始程式檔`Add`。</span><span class="sxs-lookup"><span data-stu-id="c907d-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="c907d-108">它會傳回其參數的總和。</span><span class="sxs-lookup"><span data-stu-id="c907d-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="c907d-109">類別`AddClass`，其中包含方法`Add`命名空間的成員`UtilityMethods`。</span><span class="sxs-lookup"><span data-stu-id="c907d-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="c907d-110">`Mult`: 包含方法的原始程式碼`Multiply`。</span><span class="sxs-lookup"><span data-stu-id="c907d-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="c907d-111">它會傳回其參數的乘積。</span><span class="sxs-lookup"><span data-stu-id="c907d-111">It returns the product of its parameters.</span></span> <span data-ttu-id="c907d-112">類別`MultiplyClass`，其中包含方法`Multiply`也是命名空間的成員`UtilityMethods`。</span><span class="sxs-lookup"><span data-stu-id="c907d-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="c907d-113">`TestCode`︰ 檔案包含`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="c907d-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="c907d-114">它使用中的 DLL 檔案的方式來計算總和及產品的執行階段引數。</span><span class="sxs-lookup"><span data-stu-id="c907d-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c907d-115">範例</span><span class="sxs-lookup"><span data-stu-id="c907d-115">Example</span></span>  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 <span data-ttu-id="c907d-116">這個檔案包含 DLL 的方法，會使用的演算法`Add`和`Multiply`。</span><span class="sxs-lookup"><span data-stu-id="c907d-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="c907d-117">一開始的剖析引數從命令列中，輸入`num1`和`num2`。</span><span class="sxs-lookup"><span data-stu-id="c907d-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="c907d-118">接著它會使用計算總和`Add`方法`AddClass`類別，並使用產品`Multiply`方法`MultiplyClass`類別。</span><span class="sxs-lookup"><span data-stu-id="c907d-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="c907d-119">請注意，`Imports`檔案的開頭的陳述式可讓您使用不合格的類別名稱，如下所示，在編譯時期參考 DLL 方法︰</span><span class="sxs-lookup"><span data-stu-id="c907d-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="c907d-120">否則，您必須使用完整限定的名稱，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="c907d-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="c907d-121">執行</span><span class="sxs-lookup"><span data-stu-id="c907d-121">Execution</span></span>  
 <span data-ttu-id="c907d-122">若要執行程式時，輸入兩個數字，後面，如下所示的 EXE 檔案名稱︰</span><span class="sxs-lookup"><span data-stu-id="c907d-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c907d-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c907d-123">Compiling the Code</span></span>  
 <span data-ttu-id="c907d-124">若要建置檔案`MathLibrary.DLL`，編譯兩個檔案`Add`和`Mult`使用下列命令列。</span><span class="sxs-lookup"><span data-stu-id="c907d-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="c907d-125">[/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md)編譯器選項會指示編譯器輸出的 DLL，而不是 EXE 檔案。</span><span class="sxs-lookup"><span data-stu-id="c907d-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="c907d-126">[/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)編譯器選項後面接著檔案名稱用來指定 DLL 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c907d-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="c907d-127">否則，編譯器會使用第一個檔案 (`Add.vb`) 做為 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c907d-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="c907d-128">若要建置的可執行檔， `TestCode.exe`，請使用下列命令列︰</span><span class="sxs-lookup"><span data-stu-id="c907d-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="c907d-129">**/Out**編譯器選項會指示編譯器輸出的 EXE 檔案，並指定輸出檔案的名稱 (`TestCode.exe`)。</span><span class="sxs-lookup"><span data-stu-id="c907d-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="c907d-130">這個編譯器選項是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c907d-130">This compiler option is optional.</span></span> <span data-ttu-id="c907d-131">[/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)編譯器選項會指定此程式所使用的 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="c907d-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="c907d-132">如需從命令列建置的詳細資訊，請參閱和[從命令列建置](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="c907d-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c907d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c907d-133">See Also</span></span>  
 <span data-ttu-id="c907d-134">[程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="c907d-134">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="c907d-135"> [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="c907d-135"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="c907d-136"> [建立類別以包裝 DLL 函式](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)</span><span class="sxs-lookup"><span data-stu-id="c907d-136"> [Creating a Class to Hold DLL Functions](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)</span></span>
