---
title: '#error (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23528ae81e4ddca23c67c937ca2588ab4c982e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="error-c-reference"></a><span data-ttu-id="cbeb4-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cbeb4-102">#error (C# Reference)</span></span>
<span data-ttu-id="cbeb4-103">`#error` 可讓您從程式碼中的特定位置產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cbeb4-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="cbeb4-104">例如: </span><span class="sxs-lookup"><span data-stu-id="cbeb4-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="cbeb4-105">備註</span><span class="sxs-lookup"><span data-stu-id="cbeb4-105">Remarks</span></span>  
 <span data-ttu-id="cbeb4-106">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="cbeb4-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="cbeb4-107">也可以使用 [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="cbeb4-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbeb4-108">範例</span><span class="sxs-lookup"><span data-stu-id="cbeb4-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbeb4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbeb4-109">See Also</span></span>  
 [<span data-ttu-id="cbeb4-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cbeb4-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cbeb4-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cbeb4-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cbeb4-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="cbeb4-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
