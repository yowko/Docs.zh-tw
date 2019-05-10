---
title: 無法將匿名類型轉換為運算式樹狀架構，因為該類型含有的欄位是用來初始化其他欄位
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: 045061f403b301d460bc85d161c1d6dee9c7d9f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602395"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="a3e19-102">無法將匿名類型轉換為運算式樹狀架構，因為該類型含有的欄位是用來初始化其他欄位</span><span class="sxs-lookup"><span data-stu-id="a3e19-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="a3e19-103">匿名類型的一個屬性用來初始化匿名類型的另一個屬性時，編譯器不接受匿名轉換為運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="a3e19-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="a3e19-104">例如，在下列程式碼中，`Prop1`宣告的初始化清單中，然後再做為初始值`Prop2`。</span><span class="sxs-lookup"><span data-stu-id="a3e19-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a3e19-105">**錯誤 ID:** BC36548</span><span class="sxs-lookup"><span data-stu-id="a3e19-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a3e19-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a3e19-106">To correct this error</span></span>  
  
- <span data-ttu-id="a3e19-107">將指定的初始值`Prop1`給區域變數。</span><span class="sxs-lookup"><span data-stu-id="a3e19-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="a3e19-108">將該變數指派給兩者`Prop1`和`Prop2`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a3e19-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3e19-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3e19-109">See also</span></span>

- [<span data-ttu-id="a3e19-110">匿名類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3e19-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="a3e19-111">運算式樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3e19-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="a3e19-112">如何：使用運算式樹狀架構建置動態查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3e19-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
