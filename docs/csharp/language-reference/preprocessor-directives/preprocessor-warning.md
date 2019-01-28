---
title: '#warning - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 55768a354b2841021607ed40b4ef87b9767edcad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620314"
---
# <a name="warning-c-reference"></a><span data-ttu-id="4b0ec-102">#warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4b0ec-102">#warning (C# Reference)</span></span>
<span data-ttu-id="4b0ec-103">`#warning` 可讓您從程式碼中的特定位置產生 [CS1030](../../misc/cs1030.md) 層級一的編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="4b0ec-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="4b0ec-104">例如：</span><span class="sxs-lookup"><span data-stu-id="4b0ec-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b0ec-105">備註</span><span class="sxs-lookup"><span data-stu-id="4b0ec-105">Remarks</span></span>
 <span data-ttu-id="4b0ec-106">`#warning` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="4b0ec-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="4b0ec-107">也可以使用 [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md) 產生使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b0ec-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b0ec-108">範例</span><span class="sxs-lookup"><span data-stu-id="4b0ec-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="4b0ec-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b0ec-109">See also</span></span>

- [<span data-ttu-id="4b0ec-110">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4b0ec-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4b0ec-111">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4b0ec-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4b0ec-112">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="4b0ec-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
