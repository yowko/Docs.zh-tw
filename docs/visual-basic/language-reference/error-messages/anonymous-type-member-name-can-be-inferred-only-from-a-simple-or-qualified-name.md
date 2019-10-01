---
title: 只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 38f669fe183ac79ebed6e5a122bc70aedc9bb753
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701219"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="d1f5f-102">只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="d1f5f-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="d1f5f-103">您無法從複雜運算式推斷匿名型別成員名稱。</span><span class="sxs-lookup"><span data-stu-id="d1f5f-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="d1f5f-104">如需匿名型別可以和無法推斷成員名稱和類型之來源的詳細資訊，請參閱 @no__t 0How 至：在匿名型別宣告中推斷屬性名稱和類型 @ no__t-0。</span><span class="sxs-lookup"><span data-stu-id="d1f5f-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="d1f5f-105">**錯誤識別碼：** BC36556</span><span class="sxs-lookup"><span data-stu-id="d1f5f-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1f5f-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d1f5f-106">To correct this error</span></span>  
  
- <span data-ttu-id="d1f5f-107">將運算式指派給成員名稱，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="d1f5f-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```vb  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1f5f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1f5f-108">See also</span></span>

- [<span data-ttu-id="d1f5f-109">匿名類型</span><span class="sxs-lookup"><span data-stu-id="d1f5f-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- <span data-ttu-id="d1f5f-110">[如何：在匿名型別宣告中推斷屬性名稱和類型 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="d1f5f-110">[How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>
