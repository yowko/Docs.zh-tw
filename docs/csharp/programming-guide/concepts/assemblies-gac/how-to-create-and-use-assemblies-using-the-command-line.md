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
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>如何：使用命令列建立和使用組件 (C#)
組件又稱為動態連結程式庫 (DLL)，會在執行階段連結到您的程式。 為了示範如何建立和使用 DLL，請考慮下列案例：  
  
-   `MathLibrary.DLL`︰包含要在執行階段呼叫之方法的程式庫檔案。 在此範例中，DLL 包含兩個方法︰`Add` 和 `Multiply`。  
  
-   `Add`：包含 `Add` 方法的原始程式檔。 它會傳回其參數的總和。 包含 `Add` 方法的 `AddClass` 類別是命名空間 `UtilityMethods` 的成員。  
  
-   `Mult`：包含 `Multiply` 方法的原始程式碼。 它會傳回其參數的乘積。 包含 `Multiply` 方法的 `MultiplyClass` 類別也是命名空間 `UtilityMethods` 的成員。  
  
-   `TestCode`：包含 `Main` 方法的檔案。 它使用 DLL 檔案中的方法來計算執行階段引數的總和與乘積。  
  
## <a name="example"></a>範例  
  
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
  
 此檔案包含使用 DLL 方法 `Add` 和 `Multiply` 的演算法。 一開始會剖析從命令列輸入的引數 `num1` 和 `num2`。 然後會使用 `AddClass` 類別中的 `Add` 方法計算總和，並使用 `MultiplyClass` 類別中的 `Multiply` 方法計算乘積。  
  
 請注意，檔案開頭的 `using` 指示詞可讓您使用未限定的類別名稱，在編譯時期參考 DLL 方法，如下所示：  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 否則，您必須使用完整名稱，如下所示：  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>執行  
 若要執行此程式，請輸入 EXE 檔案的名稱，後面接著兩個數字，如下所示：  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要建立 `MathLibrary.DLL` 檔案，請使用下列命令列編譯 `Add` 和 `Mult` 這兩個檔案。  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) 編譯器選項會指示編譯器輸出 DLL，而不是 EXE 檔案。 使用 [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) 編譯器選項，後面接著檔案名稱，即可指定 DLL 檔案名稱。 否則，編譯器會使用第一個檔案 (`Add.cs`) 作為 DLL 的名稱。  
  
 若要建立可執行檔 `TestCode.exe`，請使用下列命令列：  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/out** 編譯器選項會指示編譯器輸出 EXE 檔案，並指定輸出檔案的名稱 (`TestCode.exe`)。 這個編譯器選項是選擇性的。 [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 編譯器選項會指定此程式所使用的一或多個 DLL 檔案。 如需詳細資訊，請參閱 [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md)。  
  
 如需從命令列建立的詳細資訊，請參閱[使用 csc.exe 建置命令列](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../../csharp/programming-guide/index.md)   
 [組件和全域組件快取 (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [建立類別以包裝 DLL 函式](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)

