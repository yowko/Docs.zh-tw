---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698573"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="8f2fe-102">運算式會遞迴地呼叫包含屬性 ' @no__t 0propertyname > '</span><span class="sxs-lookup"><span data-stu-id="8f2fe-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="8f2fe-103">屬性定義的 `Set` 程式中的語句會將值儲存在屬性名稱中。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="8f2fe-104">保存屬性值的建議方法是在屬性的容器中定義 @no__t 0 變數，並同時在 `Get` 和 @no__t 2 程式中使用它。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="8f2fe-105">@No__t 0 程式應該會將傳入的值儲存在此 @no__t 1 變數中。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="8f2fe-106">@No__t-0 程式的行為就像是 @no__t 1 程式，因此它可以藉由遇到 @no__t 2 語句，將值指派給屬性名稱，並傳回控制權。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="8f2fe-107">不過，建議的方法是在[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)中包含 `Private` 變數做為值。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="8f2fe-108">@No__t-0 程式的行為就像是不會傳回值的 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="8f2fe-109">因此，程式或屬性名稱在 `Set` 程式中沒有特殊意義，而且您無法在其中儲存值。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="8f2fe-110">下列範例說明可能造成此錯誤的方法，後面接著建議的方法。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```vb  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 <span data-ttu-id="8f2fe-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-111">By default, this message is a warning.</span></span> <span data-ttu-id="8f2fe-112">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8f2fe-113">**錯誤識別碼：** BC42026</span><span class="sxs-lookup"><span data-stu-id="8f2fe-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8f2fe-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8f2fe-114">To correct this error</span></span>  
  
- <span data-ttu-id="8f2fe-115">重寫屬性定義，以使用上述範例中所述的建議方法。</span><span class="sxs-lookup"><span data-stu-id="8f2fe-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2fe-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f2fe-116">See also</span></span>

- [<span data-ttu-id="8f2fe-117">屬性程序</span><span class="sxs-lookup"><span data-stu-id="8f2fe-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="8f2fe-118">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="8f2fe-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="8f2fe-119">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="8f2fe-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
