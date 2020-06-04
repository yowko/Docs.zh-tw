---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e3a9f4cf2f4105d2c449813bf0c593860df7d1f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409500"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="73bf1-102">運算式會遞迴地呼叫包含的屬性 '\<propertyname>'</span><span class="sxs-lookup"><span data-stu-id="73bf1-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="73bf1-103">屬性定義的程式中的語句會將 `Set` 值儲存至屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="73bf1-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="73bf1-104">保存屬性值的建議方法是 `Private` 在屬性的容器中定義變數，並在和程式中使用它 `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="73bf1-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="73bf1-105">`Set`然後，此程式應該將傳入的值儲存在此變數中 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="73bf1-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="73bf1-106">此程式的 `Get` 行為就像 `Function` 程式，因此可以藉由遇到語句，將值指派給屬性名稱，並傳回控制權 `End Get` 。</span><span class="sxs-lookup"><span data-stu-id="73bf1-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="73bf1-107">不過，建議的方法是在 `Private` [Return 語句](../statements/return-statement.md)中包含變數作為值。</span><span class="sxs-lookup"><span data-stu-id="73bf1-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="73bf1-108">此程式的 `Set` 行為就像是 `Sub` 不會傳回值的程式。</span><span class="sxs-lookup"><span data-stu-id="73bf1-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="73bf1-109">因此，程式或屬性名稱在程式中沒有特殊意義 `Set` ，而且您無法在其中儲存值。</span><span class="sxs-lookup"><span data-stu-id="73bf1-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="73bf1-110">下列範例說明可能造成此錯誤的方法，後面接著建議的方法。</span><span class="sxs-lookup"><span data-stu-id="73bf1-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="73bf1-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="73bf1-111">By default, this message is a warning.</span></span> <span data-ttu-id="73bf1-112">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="73bf1-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="73bf1-113">**錯誤識別碼：** BC42026</span><span class="sxs-lookup"><span data-stu-id="73bf1-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73bf1-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="73bf1-114">To correct this error</span></span>  
  
- <span data-ttu-id="73bf1-115">重寫屬性定義，以使用上述範例中所述的建議方法。</span><span class="sxs-lookup"><span data-stu-id="73bf1-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bf1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73bf1-116">See also</span></span>

- [<span data-ttu-id="73bf1-117">屬性程序</span><span class="sxs-lookup"><span data-stu-id="73bf1-117">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="73bf1-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="73bf1-118">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="73bf1-119">Set 語句</span><span class="sxs-lookup"><span data-stu-id="73bf1-119">Set Statement</span></span>](../statements/set-statement.md)
