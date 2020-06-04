---
title: 跨繼承的介面 '<membername>' 和 '<interfacename1>' 的 '<interfacename2>' 是模稜兩可的
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: f242db9e02a1983e731dce280be0e8f8a8b12712
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397268"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="05c53-102">跨繼承的介面 '\<membername>' 和 '\<interfacename1>' 的 '\<interfacename2>' 是模稜兩可的</span><span class="sxs-lookup"><span data-stu-id="05c53-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>
<span data-ttu-id="05c53-103">介面會從多個介面繼承兩個或多個具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="05c53-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="05c53-104">**錯誤識別碼：** BC30685</span><span class="sxs-lookup"><span data-stu-id="05c53-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05c53-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="05c53-105">To correct this error</span></span>  
  
- <span data-ttu-id="05c53-106">將值轉換成您想要使用的基底介面;例如：</span><span class="sxs-lookup"><span data-stu-id="05c53-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```vb  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="05c53-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05c53-107">See also</span></span>

- [<span data-ttu-id="05c53-108">介面</span><span class="sxs-lookup"><span data-stu-id="05c53-108">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
