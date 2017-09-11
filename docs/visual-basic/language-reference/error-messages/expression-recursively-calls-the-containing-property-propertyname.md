---
title: "運算式會遞迴地呼叫包含的屬性 &quot;&lt;propertyname&gt;&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
dev_langs:
- VB
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c7168ab2a2ec5eb0c0d423120b67c10b117c14b2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="f20a3-102">運算式會遞迴地呼叫包含的屬性 '&lt;propertyname&gt;'</span><span class="sxs-lookup"><span data-stu-id="f20a3-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="f20a3-103">中的陳述式`Set`屬性定義的程序將值儲存到屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f20a3-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="f20a3-104">保留的屬性值的建議的方法是定義`Private`屬性的容器中的變數並將它用於兩者`Get`和`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="f20a3-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="f20a3-105">`Set`程序應該然後將內送值儲存在這個`Private`變數。</span><span class="sxs-lookup"><span data-stu-id="f20a3-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="f20a3-106">`Get`程序的行為類似`Function`程序，以便將值指派給屬性的名稱並將控制權傳回所遇到`End Get`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f20a3-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="f20a3-107">建議的方法，不過，是要包含`Private`變數中的值為[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f20a3-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="f20a3-108">`Set`程序的行為類似`Sub`程序，不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="f20a3-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="f20a3-109">因此，程序或屬性名稱有內沒有特殊意義`Set`程序中，而且您無法將值儲存到其中。</span><span class="sxs-lookup"><span data-stu-id="f20a3-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="f20a3-110">下列範例說明可能會造成這個錯誤，後面接著的建議方法的方法。</span><span class="sxs-lookup"><span data-stu-id="f20a3-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```  
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
  
 <span data-ttu-id="f20a3-111">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="f20a3-111">By default, this message is a warning.</span></span> <span data-ttu-id="f20a3-112">如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="f20a3-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f20a3-113">**錯誤識別碼︰** BC42026</span><span class="sxs-lookup"><span data-stu-id="f20a3-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f20a3-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f20a3-114">To correct this error</span></span>  
  
-   <span data-ttu-id="f20a3-115">請重寫的屬性定義，以使用建議的方法，在上述範例中所示。</span><span class="sxs-lookup"><span data-stu-id="f20a3-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f20a3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f20a3-116">See Also</span></span>  
 <span data-ttu-id="f20a3-117">[Property 程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f20a3-117">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="f20a3-118"> [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f20a3-118"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="f20a3-119"> [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f20a3-119"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
