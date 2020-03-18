---
title: '#error - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173402"
---
# <a name="error-c-reference"></a><span data-ttu-id="79285-102">#error (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="79285-102">#error (C# Reference)</span></span>
<span data-ttu-id="79285-103">`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="79285-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="79285-104">例如：</span><span class="sxs-lookup"><span data-stu-id="79285-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="79285-105">備註</span><span class="sxs-lookup"><span data-stu-id="79285-105">Remarks</span></span>  
 <span data-ttu-id="79285-106">`#error` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="79285-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="79285-107">也可以使用 [#warning](./preprocessor-warning.md) 產生使用者定義警告。</span><span class="sxs-lookup"><span data-stu-id="79285-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79285-108">範例</span><span class="sxs-lookup"><span data-stu-id="79285-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79285-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79285-109">See also</span></span>

- [<span data-ttu-id="79285-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="79285-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79285-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="79285-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79285-112">C# 預處理器指令</span><span class="sxs-lookup"><span data-stu-id="79285-112">C# Preprocessor Directives</span></span>](./index.md)
