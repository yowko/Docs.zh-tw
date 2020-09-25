---
description: '#warning - C# 參考'
title: '#warning - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 9ade723bdca17597dcd56240f506e60f2debf6be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186415"
---
# <a name="warning-c-reference"></a><span data-ttu-id="328ee-103">#warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="328ee-103">#warning (C# Reference)</span></span>

<span data-ttu-id="328ee-104">`#warning` 可讓您從程式碼中的特定位置產生 [CS1030](../../misc/cs1030.md) 層級一的編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="328ee-104">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="328ee-105">例如：</span><span class="sxs-lookup"><span data-stu-id="328ee-105">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="328ee-106">備註</span><span class="sxs-lookup"><span data-stu-id="328ee-106">Remarks</span></span>

 <span data-ttu-id="328ee-107">`#warning` 常見於條件指示詞中。</span><span class="sxs-lookup"><span data-stu-id="328ee-107">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="328ee-108">也可以使用 [#error](./preprocessor-error.md) 產生使用者定義錯誤。</span><span class="sxs-lookup"><span data-stu-id="328ee-108">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="328ee-109">範例</span><span class="sxs-lookup"><span data-stu-id="328ee-109">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="328ee-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="328ee-110">See also</span></span>

- [<span data-ttu-id="328ee-111">C # 參考</span><span class="sxs-lookup"><span data-stu-id="328ee-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="328ee-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="328ee-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="328ee-113">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="328ee-113">C# Preprocessor Directives</span></span>](./index.md)
