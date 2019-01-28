---
title: '#error - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559331"
---
# <a name="error-c-reference"></a><span data-ttu-id="6f4d1-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6f4d1-102">#error (C# Reference)</span></span>
<span data-ttu-id="6f4d1-103">`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f4d1-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="6f4d1-104">例如：</span><span class="sxs-lookup"><span data-stu-id="6f4d1-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="6f4d1-105">備註</span><span class="sxs-lookup"><span data-stu-id="6f4d1-105">Remarks</span></span>  
 <span data-ttu-id="6f4d1-106">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="6f4d1-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="6f4d1-107">也可以使用 [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="6f4d1-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f4d1-108">範例</span><span class="sxs-lookup"><span data-stu-id="6f4d1-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f4d1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4d1-109">See also</span></span>

- [<span data-ttu-id="6f4d1-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6f4d1-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="6f4d1-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6f4d1-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6f4d1-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="6f4d1-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
