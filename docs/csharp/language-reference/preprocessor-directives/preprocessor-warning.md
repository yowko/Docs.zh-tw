---
title: "#<a name=\"warning-c-reference\"></a>warning (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#warning'
helpviewer_keywords: '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a><span data-ttu-id="e5d45-102">#warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e5d45-102">#warning (C# Reference)</span></span>
<span data-ttu-id="e5d45-103">`#warning` 可讓您從程式碼中的特定位置產生層級一的警告。</span><span class="sxs-lookup"><span data-stu-id="e5d45-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="e5d45-104">例如: </span><span class="sxs-lookup"><span data-stu-id="e5d45-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="e5d45-105">備註</span><span class="sxs-lookup"><span data-stu-id="e5d45-105">Remarks</span></span>  
 <span data-ttu-id="e5d45-106">`#warning` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="e5d45-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="e5d45-107">也可以使用 [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md) 產生使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="e5d45-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5d45-108">範例</span><span class="sxs-lookup"><span data-stu-id="e5d45-108">Example</span></span>  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5d45-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5d45-109">See Also</span></span>  
 [<span data-ttu-id="e5d45-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e5d45-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e5d45-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e5d45-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e5d45-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="e5d45-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
