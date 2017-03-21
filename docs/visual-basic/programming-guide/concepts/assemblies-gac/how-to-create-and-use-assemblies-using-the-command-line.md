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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 363bca806736e5540165ea96e9b4fe60d0968098
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>如何︰ 建立和使用組件︰ 使用命令列 (Visual Basic)
組件或動態連結程式庫 (DLL)，會在執行階段連結至您的程式。 為了示範建置和使用 DLL，請考慮下列案例︰  
  
-   `MathLibrary.DLL`︰ 包含要在執行階段呼叫的方法程式庫檔案。 在此範例中，DLL 包含兩個方法︰`Add`和`Multiply`。  
  
-   `Add`: 包含方法的原始程式檔`Add`。 它會傳回其參數的總和。 類別`AddClass`，其中包含方法`Add`命名空間的成員`UtilityMethods`。  
  
-   `Mult`: 包含方法的原始程式碼`Multiply`。 它會傳回其參數的乘積。 類別`MultiplyClass`，其中包含方法`Multiply`也是命名空間的成員`UtilityMethods`。  
  
-   `TestCode`︰ 檔案包含`Main`方法。 它使用中的 DLL 檔案的方式來計算總和及產品的執行階段引數。  
  
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
  
 這個檔案包含 DLL 的方法，會使用的演算法`Add`和`Multiply`。 一開始的剖析引數從命令列中，輸入`num1`和`num2`。 接著它會使用計算總和`Add`方法`AddClass`類別，並使用產品`Multiply`方法`MultiplyClass`類別。  
  
 請注意，`Imports`檔案的開頭的陳述式可讓您使用不合格的類別名稱，如下所示，在編譯時期參考 DLL 方法︰  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 否則，您必須使用完整限定的名稱，如下所示︰  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>執行  
 若要執行程式時，輸入兩個數字，後面，如下所示的 EXE 檔案名稱︰  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要建置檔案`MathLibrary.DLL`，編譯兩個檔案`Add`和`Mult`使用下列命令列。  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md)編譯器選項會指示編譯器輸出的 DLL，而不是 EXE 檔案。 [/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md)編譯器選項後面接著檔案名稱用來指定 DLL 的檔案名稱。 否則，編譯器會使用第一個檔案 (`Add.vb`) 做為 DLL 的名稱。  
  
 若要建置的可執行檔， `TestCode.exe`，請使用下列命令列︰  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 **/Out**編譯器選項會指示編譯器輸出的 EXE 檔案，並指定輸出檔案的名稱 (`TestCode.exe`)。 這個編譯器選項是選擇性的。 [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)編譯器選項會指定此程式所使用的 DLL 檔案。  
  
 如需從命令列建置的詳細資訊，請參閱和[從命令列建置](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [建立類別以包裝 DLL 函式](http://msdn.microsoft.com/library/e08e4c34-0223-45f7-aa55-a3d8dd979b0f)
