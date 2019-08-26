---
title: 作法：使用命令列建立和使用組件 (C#)
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595974"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>作法：使用命令列建立和使用組件 (C#)
組件又稱為動態連結程式庫 (DLL)，會在執行階段連結到您的程式。 為了示範如何建立和使用 DLL，請考慮下列案例：  
  
- `MathLibrary.DLL`：程式庫檔案，其中包含要在執行階段呼叫的方法。 在此範例中，DLL 包含兩個方法︰`Add` 和 `Multiply`。  
  
- `Add`：包含 `Add` 方法的原始程式檔。 它會傳回其參數的總和。 包含 `Add` 方法的 `AddClass` 類別是命名空間 `UtilityMethods` 的成員。  
  
- `Mult`：包含 `Multiply` 方法的原始程式碼。 它會傳回其參數的乘積。 包含 `Multiply` 方法的 `MultiplyClass` 類別也是命名空間 `UtilityMethods` 的成員。  
  
- `TestCode`：包含 `Main` 方法的檔案。 它使用 DLL 檔案中的方法來計算執行階段引數的總和與乘積。  
  
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
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../index.md)
- [.NET 中的組件](../../../../standard/assembly/index.md)
- [建立類別以包裝 DLL 函式](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
