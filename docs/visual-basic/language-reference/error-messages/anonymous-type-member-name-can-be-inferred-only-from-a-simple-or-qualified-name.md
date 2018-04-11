---
title: 只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7068928a17ee5fdb7bf6b5e0a40aaa7e5ef32f11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="61fe4-102">只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="61fe4-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="61fe4-103">您無法推斷匿名類型成員名稱，從複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="61fe4-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="61fe4-104">如需來源匿名型別可以和無法推斷成員的名稱和類型的詳細資訊，請參閱[How to： 推斷屬性名稱和匿名類型宣告中的型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="61fe4-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="61fe4-105">**錯誤 ID:** BC36556</span><span class="sxs-lookup"><span data-stu-id="61fe4-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="61fe4-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="61fe4-106">To correct this error</span></span>  
  
-   <span data-ttu-id="61fe4-107">將運算式指派給成員名稱，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="61fe4-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61fe4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61fe4-108">See Also</span></span>  
 [<span data-ttu-id="61fe4-109">匿名類型</span><span class="sxs-lookup"><span data-stu-id="61fe4-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="61fe4-110">如何：在匿名類型宣告中推斷屬性名稱和類型</span><span class="sxs-lookup"><span data-stu-id="61fe4-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
