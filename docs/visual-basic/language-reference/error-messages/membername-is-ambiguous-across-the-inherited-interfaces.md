---
title: 跨繼承的介面 '<membername>' 和 '<interfacename1>' 的 '<interfacename2>' 是模稜兩可的
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 4415608bcfca63b43b3d9ebf17ce622ccd418775
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820837"
---
# <a name="membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="9442b-102">'\<成員名稱 >' 模稜兩可，跨繼承介面\<介面名稱 1>.< >' 和'\<介面名稱 2&gt >'</span><span class="sxs-lookup"><span data-stu-id="9442b-102">'\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>
<span data-ttu-id="9442b-103">此介面會繼承自多個介面的兩個或多個具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="9442b-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>  
  
 <span data-ttu-id="9442b-104">**錯誤 ID:** BC30685</span><span class="sxs-lookup"><span data-stu-id="9442b-104">**Error ID:** BC30685</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9442b-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9442b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="9442b-106">將值轉換成您想要使用的基底介面例如：</span><span class="sxs-lookup"><span data-stu-id="9442b-106">Cast the value to the base interface that you want to use; for example:</span></span>  
  
    ```  
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
  
## <a name="see-also"></a><span data-ttu-id="9442b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9442b-107">See also</span></span>

- [<span data-ttu-id="9442b-108">介面</span><span class="sxs-lookup"><span data-stu-id="9442b-108">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
