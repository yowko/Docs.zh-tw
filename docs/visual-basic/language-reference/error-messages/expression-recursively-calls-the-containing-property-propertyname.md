---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: c05a7d9b021192d53a30e49f52abc08d9b153156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874247"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="354c1-102">運算式會遞迴地呼叫包含的屬性 '\<propertyname>'</span><span class="sxs-lookup"><span data-stu-id="354c1-102">Expression recursively calls the containing property '\<propertyname>'</span></span>

<span data-ttu-id="354c1-103">屬性定義的程式中的語句會將 `Set` 值儲存到屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="354c1-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="354c1-104">保留屬性值的建議方法是在 `Private` 屬性的容器中定義變數，並在和程式中使用它 `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="354c1-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="354c1-105">然後，程式 `Set` 應該將傳入值儲存在此 `Private` 變數中。</span><span class="sxs-lookup"><span data-stu-id="354c1-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="354c1-106">`Get`程式的行為就像程式一樣 `Function` ，因此它可以將值指派給屬性名稱，並藉由遇到語句來傳回控制項 `End Get` 。</span><span class="sxs-lookup"><span data-stu-id="354c1-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="354c1-107">不過，建議的方法是 `Private` 在 [Return 語句](../statements/return-statement.md)中包含變數作為值。</span><span class="sxs-lookup"><span data-stu-id="354c1-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="354c1-108">程式的 `Set` 行為就像是 `Sub` 不會傳回值的程式。</span><span class="sxs-lookup"><span data-stu-id="354c1-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="354c1-109">因此，程式或屬性名稱在程式內沒有特殊意義 `Set` ，而且您無法將值儲存到其中。</span><span class="sxs-lookup"><span data-stu-id="354c1-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="354c1-110">下列範例說明可能會導致此錯誤的方法，後面接著建議的方法。</span><span class="sxs-lookup"><span data-stu-id="354c1-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="354c1-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="354c1-111">By default, this message is a warning.</span></span> <span data-ttu-id="354c1-112">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱設定 [Visual Basic 中的警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="354c1-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="354c1-113">**錯誤識別碼：** BC42026</span><span class="sxs-lookup"><span data-stu-id="354c1-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="354c1-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="354c1-114">To correct this error</span></span>  
  
- <span data-ttu-id="354c1-115">重寫屬性定義以使用建議的方法，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="354c1-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354c1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="354c1-116">See also</span></span>

- [<span data-ttu-id="354c1-117">屬性程序</span><span class="sxs-lookup"><span data-stu-id="354c1-117">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="354c1-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="354c1-118">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="354c1-119">Set 語句</span><span class="sxs-lookup"><span data-stu-id="354c1-119">Set Statement</span></span>](../statements/set-statement.md)
