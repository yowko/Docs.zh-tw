---
title: '#warning - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608519"
---
# <a name="warning-c-reference"></a><span data-ttu-id="5132e-102">#warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5132e-102">#warning (C# Reference)</span></span>
<span data-ttu-id="5132e-103">`#warning` 可讓您從程式碼中的特定位置產生 [CS1030](../../misc/cs1030.md) 層級一的編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="5132e-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="5132e-104">例如：</span><span class="sxs-lookup"><span data-stu-id="5132e-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="5132e-105">備註</span><span class="sxs-lookup"><span data-stu-id="5132e-105">Remarks</span></span>
 <span data-ttu-id="5132e-106">`#warning` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="5132e-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="5132e-107">也可以使用 [#error](./preprocessor-error.md) 產生使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="5132e-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5132e-108">範例</span><span class="sxs-lookup"><span data-stu-id="5132e-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="5132e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5132e-109">See also</span></span>

- [<span data-ttu-id="5132e-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5132e-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5132e-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5132e-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5132e-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="5132e-112">C# Preprocessor Directives</span></span>](./index.md)
