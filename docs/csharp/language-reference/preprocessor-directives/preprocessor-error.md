---
title: '#error - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: b335dfeed23d43938c66f0753590af55ac99b12a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235580"
---
# <a name="error-c-reference"></a><span data-ttu-id="cad04-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cad04-102">#error (C# Reference)</span></span>
<span data-ttu-id="cad04-103">`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="cad04-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="cad04-104">例如: </span><span class="sxs-lookup"><span data-stu-id="cad04-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="cad04-105">備註</span><span class="sxs-lookup"><span data-stu-id="cad04-105">Remarks</span></span>  
 <span data-ttu-id="cad04-106">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="cad04-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="cad04-107">也可以使用 [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="cad04-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cad04-108">範例</span><span class="sxs-lookup"><span data-stu-id="cad04-108">Example</span></span>  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cad04-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="cad04-109">See Also</span></span>

- [<span data-ttu-id="cad04-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cad04-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="cad04-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cad04-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cad04-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="cad04-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
