---
title: 晚期繫結多載解析無法套用至&#39;&lt;程序名稱&gt;&#39;因為進行存取的執行個體為介面類型
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: db0ce88f63be8d58cc1c1abf91eda6a0e56456c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651509"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="e2933-102">晚期繫結多載解析無法套用至&#39;&lt;程序名稱&gt;&#39;因為進行存取的執行個體為介面類型</span><span class="sxs-lookup"><span data-stu-id="e2933-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="e2933-103">編譯器嘗試解析其參考的多載的屬性或程序，但參考會失敗，因為引數的型別是`Object`和參考的物件具有介面的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e2933-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="e2933-104">`Object`引數會強制編譯器解析為晚期繫結參考。</span><span class="sxs-lookup"><span data-stu-id="e2933-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="e2933-105">在這些情況下，編譯器會解析而不是透過基礎的介面實作的類別透過多載。</span><span class="sxs-lookup"><span data-stu-id="e2933-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="e2933-106">如果類別重新命名其中一個多載版本，編譯器不會將該版本是多載，因為它的名稱不同。</span><span class="sxs-lookup"><span data-stu-id="e2933-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="e2933-107">這也會導致編譯器忽略已重新命名的版本，當它可能已解析參考正確的選擇。</span><span class="sxs-lookup"><span data-stu-id="e2933-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="e2933-108">**錯誤 ID:** BC30933</span><span class="sxs-lookup"><span data-stu-id="e2933-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e2933-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e2933-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e2933-110">使用`CType`要轉型的引數，從`Object`您想要呼叫的多載簽章所指定的型別。</span><span class="sxs-lookup"><span data-stu-id="e2933-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="e2933-111">請注意，它無法協助參考將物件轉換為基礎的介面。</span><span class="sxs-lookup"><span data-stu-id="e2933-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="e2933-112">您必須轉換為避免此錯誤的引數。</span><span class="sxs-lookup"><span data-stu-id="e2933-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2933-113">範例</span><span class="sxs-lookup"><span data-stu-id="e2933-113">Example</span></span>  
 <span data-ttu-id="e2933-114">下列範例示範呼叫多載的`Sub`在編譯時期會造成這個錯誤的程序。</span><span class="sxs-lookup"><span data-stu-id="e2933-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e2933-115">在上述範例中，如果編譯器允許在呼叫`s1`解析度寫入時，需要透過類別的地方`c1`而不是介面`i1`。</span><span class="sxs-lookup"><span data-stu-id="e2933-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="e2933-116">這表示編譯器不會考慮`s2`因為其名稱中的不同`c1`，即使它是正確的選擇，因為所定義`i1`。</span><span class="sxs-lookup"><span data-stu-id="e2933-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="e2933-117">您可以藉由變更下列幾行程式碼的其中一種方法的呼叫來更正此錯誤：</span><span class="sxs-lookup"><span data-stu-id="e2933-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="e2933-118">每個上述幾行程式碼明確轉換`Object`變數`o1`其中一個多載所定義的參數類型。</span><span class="sxs-lookup"><span data-stu-id="e2933-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2933-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2933-119">See also</span></span>
- [<span data-ttu-id="e2933-120">程序多載化</span><span class="sxs-lookup"><span data-stu-id="e2933-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="e2933-121">多載解析</span><span class="sxs-lookup"><span data-stu-id="e2933-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="e2933-122">CType 函式</span><span class="sxs-lookup"><span data-stu-id="e2933-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
