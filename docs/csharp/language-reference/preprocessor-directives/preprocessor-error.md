---
title: '#error (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="error-c-reference"></a><span data-ttu-id="0f361-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0f361-102">#error (C# Reference)</span></span>
<span data-ttu-id="0f361-103">`#error` 可讓您從程式碼中的特定位置產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f361-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="0f361-104">例如: </span><span class="sxs-lookup"><span data-stu-id="0f361-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="0f361-105">備註</span><span class="sxs-lookup"><span data-stu-id="0f361-105">Remarks</span></span>  
 <span data-ttu-id="0f361-106">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="0f361-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="0f361-107">也可以使用 [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="0f361-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f361-108">範例</span><span class="sxs-lookup"><span data-stu-id="0f361-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f361-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f361-109">See Also</span></span>  
 [<span data-ttu-id="0f361-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0f361-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0f361-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0f361-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0f361-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="0f361-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
