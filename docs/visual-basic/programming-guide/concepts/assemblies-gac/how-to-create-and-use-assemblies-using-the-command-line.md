---
title: "如何： 建立和使用組件使用命令列 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="237cf-102">如何： 建立和使用組件使用命令列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="237cf-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="237cf-103">組件又稱為動態連結程式庫 (DLL)，會在執行階段連結到您的程式。</span><span class="sxs-lookup"><span data-stu-id="237cf-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="237cf-104">為了示範如何建立和使用 DLL，請考慮下列案例：</span><span class="sxs-lookup"><span data-stu-id="237cf-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="237cf-105">`MathLibrary.DLL`︰包含要在執行階段呼叫之方法的程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="237cf-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="237cf-106">在此範例中，DLL 包含兩個方法︰`Add` 和 `Multiply`。</span><span class="sxs-lookup"><span data-stu-id="237cf-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="237cf-107">`Add`：包含 `Add` 方法的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="237cf-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="237cf-108">它會傳回其參數的總和。</span><span class="sxs-lookup"><span data-stu-id="237cf-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="237cf-109">包含 `Add` 方法的 `AddClass` 類別是命名空間 `UtilityMethods` 的成員。</span><span class="sxs-lookup"><span data-stu-id="237cf-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="237cf-110">`Mult`：包含 `Multiply` 方法的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="237cf-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="237cf-111">它會傳回其參數的乘積。</span><span class="sxs-lookup"><span data-stu-id="237cf-111">It returns the product of its parameters.</span></span> <span data-ttu-id="237cf-112">包含 `Multiply` 方法的 `MultiplyClass` 類別也是命名空間 `UtilityMethods` 的成員。</span><span class="sxs-lookup"><span data-stu-id="237cf-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="237cf-113">`TestCode`：包含 `Main` 方法的檔案。</span><span class="sxs-lookup"><span data-stu-id="237cf-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="237cf-114">它使用 DLL 檔案中的方法來計算執行階段引數的總和與乘積。</span><span class="sxs-lookup"><span data-stu-id="237cf-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="237cf-115">範例</span><span class="sxs-lookup"><span data-stu-id="237cf-115">Example</span></span>  
  
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
  
 <span data-ttu-id="237cf-116">此檔案包含使用 DLL 方法 `Add` 和 `Multiply` 的演算法。</span><span class="sxs-lookup"><span data-stu-id="237cf-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="237cf-117">一開始會剖析從命令列輸入的引數 `num1` 和 `num2`。</span><span class="sxs-lookup"><span data-stu-id="237cf-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="237cf-118">然後會使用 `AddClass` 類別中的 `Add` 方法計算總和，並使用 `MultiplyClass` 類別中的 `Multiply` 方法計算乘積。</span><span class="sxs-lookup"><span data-stu-id="237cf-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="237cf-119">請注意，`Imports`檔案的開頭的陳述式可讓您使用未限定的類別名稱，如下所示，在編譯時期參考 DLL 方法：</span><span class="sxs-lookup"><span data-stu-id="237cf-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="237cf-120">否則，您必須使用完整名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="237cf-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="237cf-121">執行</span><span class="sxs-lookup"><span data-stu-id="237cf-121">Execution</span></span>  
 <span data-ttu-id="237cf-122">若要執行此程式，請輸入 EXE 檔案的名稱，後面接著兩個數字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="237cf-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="237cf-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="237cf-123">Compiling the Code</span></span>  
 <span data-ttu-id="237cf-124">若要建立 `MathLibrary.DLL` 檔案，請使用下列命令列編譯 `Add` 和 `Mult` 這兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="237cf-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="237cf-125">[/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md)編譯器選項會告訴編譯器輸出的 DLL，而不是 EXE 檔案。</span><span class="sxs-lookup"><span data-stu-id="237cf-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="237cf-126">[/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)編譯器選項後面加上檔案名稱用來指定 DLL 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="237cf-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="237cf-127">否則，編譯器會使用第一個檔案 (`Add.vb`) 作為 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="237cf-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="237cf-128">若要建立可執行檔 `TestCode.exe`，請使用下列命令列：</span><span class="sxs-lookup"><span data-stu-id="237cf-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="237cf-129">**/out** 編譯器選項會指示編譯器輸出 EXE 檔案，並指定輸出檔案的名稱 (`TestCode.exe`)。</span><span class="sxs-lookup"><span data-stu-id="237cf-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="237cf-130">這個編譯器選項是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="237cf-130">This compiler option is optional.</span></span> <span data-ttu-id="237cf-131">[/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)編譯器選項會指定此程式所使用的 DLL 檔案。</span><span class="sxs-lookup"><span data-stu-id="237cf-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="237cf-132">如需從命令列建置的詳細資訊，請參閱和[從命令列建置](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="237cf-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237cf-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="237cf-133">See Also</span></span>  
 [<span data-ttu-id="237cf-134">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="237cf-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="237cf-135">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="237cf-135">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="237cf-136">建立類別以包裝 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="237cf-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
