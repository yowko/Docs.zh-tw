---
title: '#error (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259875"
---
# <a name="error-c-reference"></a><span data-ttu-id="2a734-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2a734-102">#error (C# Reference)</span></span>
<span data-ttu-id="2a734-103">`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a734-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="2a734-104">例如: </span><span class="sxs-lookup"><span data-stu-id="2a734-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a734-105">備註</span><span class="sxs-lookup"><span data-stu-id="2a734-105">Remarks</span></span>  
 <span data-ttu-id="2a734-106">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="2a734-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="2a734-107">也可以使用 [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="2a734-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a734-108">範例</span><span class="sxs-lookup"><span data-stu-id="2a734-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a734-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a734-109">See Also</span></span>

- [<span data-ttu-id="2a734-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2a734-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2a734-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2a734-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2a734-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="2a734-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
