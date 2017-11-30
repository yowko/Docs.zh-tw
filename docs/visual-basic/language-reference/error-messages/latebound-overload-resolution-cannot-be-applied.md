---
title: "晚期繫結多載解析無法套用至 &#39;&lt;程序名稱&gt;&#39;，因為存取的執行個體為介面類型"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="f64df-102">晚期繫結多載解析無法套用至 &#39;&lt;程序名稱&gt;&#39;，因為存取的執行個體為介面類型</span><span class="sxs-lookup"><span data-stu-id="f64df-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="f64df-103">編譯器正在嘗試將參考解析成的多載的屬性或程序，但參考失敗，因為引數是型別`Object`和參考的物件具有介面的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f64df-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="f64df-104">`Object`引數會強制編譯器解析參考為晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="f64df-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="f64df-105">在這些情況下，編譯器就會透過實作類別而不是透過基礎介面的多載解析。</span><span class="sxs-lookup"><span data-stu-id="f64df-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="f64df-106">如果類別重新命名其中一個多載版本，編譯器不會將該版本，要多載，因為其名稱都不相同。</span><span class="sxs-lookup"><span data-stu-id="f64df-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="f64df-107">這會導致編譯器忽略已重新命名的版本時，它可能已解析參考正確的選擇。</span><span class="sxs-lookup"><span data-stu-id="f64df-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="f64df-108">**錯誤 ID:** BC30933</span><span class="sxs-lookup"><span data-stu-id="f64df-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f64df-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f64df-109">To correct this error</span></span>  
  
-   <span data-ttu-id="f64df-110">使用`CType`轉換引數從`Object`指定您想要呼叫的多載簽章的型別。</span><span class="sxs-lookup"><span data-stu-id="f64df-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="f64df-111">請注意，它不會協助參考物件轉換為基礎的介面。</span><span class="sxs-lookup"><span data-stu-id="f64df-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="f64df-112">您必須轉換為避免此錯誤的引數。</span><span class="sxs-lookup"><span data-stu-id="f64df-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f64df-113">範例</span><span class="sxs-lookup"><span data-stu-id="f64df-113">Example</span></span>  
 <span data-ttu-id="f64df-114">下列範例會示範呼叫多載的`Sub`在編譯時期會造成這個錯誤的程序。</span><span class="sxs-lookup"><span data-stu-id="f64df-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
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
  
 <span data-ttu-id="f64df-115">在上述範例中，如果編譯器允許呼叫`s1`當寫入時，解析度也不會透過類別發生`c1`而不是介面`i1`。</span><span class="sxs-lookup"><span data-stu-id="f64df-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="f64df-116">這表示編譯器不會考慮`s2`因為其名稱中不同`c1`，即使它是正確的選擇，因為所定義`i1`。</span><span class="sxs-lookup"><span data-stu-id="f64df-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="f64df-117">您可以更正錯誤，請變更下列程式碼的呼叫：</span><span class="sxs-lookup"><span data-stu-id="f64df-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="f64df-118">上述程式碼行的每個明確轉換`Object`變數`o1`其中一個多載定義的參數型別。</span><span class="sxs-lookup"><span data-stu-id="f64df-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64df-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f64df-119">See Also</span></span>  
 [<span data-ttu-id="f64df-120">程序多載化</span><span class="sxs-lookup"><span data-stu-id="f64df-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="f64df-121">多載解析</span><span class="sxs-lookup"><span data-stu-id="f64df-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [<span data-ttu-id="f64df-122">CType 函式</span><span class="sxs-lookup"><span data-stu-id="f64df-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
