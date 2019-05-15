---
title: HOW TO：建立和使用組件使用命令列 (Visual Basic)
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: a30d4b3ea203a8b4d3ba621fc7b0310477ddf10d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592680"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>HOW TO：建立和使用組件使用命令列 (Visual Basic)
組件又稱為動態連結程式庫 (DLL)，會在執行階段連結到您的程式。 為了示範如何建立和使用 DLL，請考慮下列案例：  
  
- `MathLibrary.DLL`：程式庫檔案，其中包含要在執行階段呼叫的方法。 在此範例中，DLL 包含兩個方法︰`Add` 和 `Multiply`。  
  
- `Add`：包含 `Add` 方法的原始程式檔。 它會傳回其參數的總和。 包含 `Add` 方法的 `AddClass` 類別是命名空間 `UtilityMethods` 的成員。  
  
- `Mult`：包含 `Multiply` 方法的原始程式碼。 它會傳回其參數的乘積。 包含 `Multiply` 方法的 `MultiplyClass` 類別也是命名空間 `UtilityMethods` 的成員。  
  
- `TestCode`：包含 `Main` 方法的檔案。 它使用 DLL 檔案中的方法來計算執行階段引數的總和與乘積。  
  
## <a name="example"></a>範例  
  
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
  
 此檔案包含使用 DLL 方法 `Add` 和 `Multiply` 的演算法。 一開始會剖析從命令列輸入的引數 `num1` 和 `num2`。 然後會使用 `AddClass` 類別中的 `Add` 方法計算總和，並使用 `MultiplyClass` 類別中的 `Multiply` 方法計算乘積。  
  
 請注意，`Imports`檔案的開頭的陳述式可讓您使用未限定的類別名稱，如下所示，在編譯時期參考 DLL 方法：  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 否則，您必須使用完整名稱，如下所示：  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>執行  
 若要執行此程式，請輸入 EXE 檔案的名稱，後面接著兩個數字，如下所示：  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>另請參閱

- [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
- [.NET 中的組件](../../../../standard/assembly/index.md)
- [建立類別以包裝 DLL 函式](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
