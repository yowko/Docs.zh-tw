---
title: "'System.Nullable(Of T)' 的方法不可以當做 'AddressOf' 運算子的運算元使用。"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 54d66a60d20a6add4c2b4a160f87b58b5a1d00e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920883"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="b2cf6-102">'System.Nullable(Of T)' 的方法不可以當做 'AddressOf' 運算子的運算元使用。</span><span class="sxs-lookup"><span data-stu-id="b2cf6-102">Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>
<span data-ttu-id="b2cf6-103">陳述式會使用`AddressOf`運算子和運算元表示的程序<xref:System.Nullable%601>結構。</span><span class="sxs-lookup"><span data-stu-id="b2cf6-103">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>  
  
 <span data-ttu-id="b2cf6-104">**錯誤 ID:** BC32126</span><span class="sxs-lookup"><span data-stu-id="b2cf6-104">**Error ID:** BC32126</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2cf6-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b2cf6-105">To correct this error</span></span>  
  
- <span data-ttu-id="b2cf6-106">取代中的程序名稱`AddressOf`子句和運算元，不是成員<xref:System.Nullable%601>。</span><span class="sxs-lookup"><span data-stu-id="b2cf6-106">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>  
  
- <span data-ttu-id="b2cf6-107">撰寫的類別，包裝的方法<xref:System.Nullable%601>您想要使用。</span><span class="sxs-lookup"><span data-stu-id="b2cf6-107">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="b2cf6-108">在下列範例中，`NullableWrapper`類別會定義名為的新方法`GetValueOrDefault`。</span><span class="sxs-lookup"><span data-stu-id="b2cf6-108">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="b2cf6-109">因為這個新的方法不是隸屬<xref:System.Nullable%601>，它可以套用至`nullInstance`，可為 null 的類型，以形成的引數的執行個體`AddressOf`。</span><span class="sxs-lookup"><span data-stu-id="b2cf6-109">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2cf6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2cf6-110">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="b2cf6-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="b2cf6-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="b2cf6-112">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="b2cf6-112">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="b2cf6-113">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2cf6-113">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
