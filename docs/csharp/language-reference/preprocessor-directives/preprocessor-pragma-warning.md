---
title: '#pragma 警告 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5330b448dc2b328992b2d29699557d20df56dee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="93646-102">#pragma warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="93646-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="93646-103">`#pragma warning` 可以啟用或停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="93646-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93646-104">語法</span><span class="sxs-lookup"><span data-stu-id="93646-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93646-105">參數</span><span class="sxs-lookup"><span data-stu-id="93646-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="93646-106">警告編號的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="93646-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="93646-107">"CS" 前置詞是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="93646-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="93646-108">未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。</span><span class="sxs-lookup"><span data-stu-id="93646-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93646-109">若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出] 視窗中尋找警告編號。</span><span class="sxs-lookup"><span data-stu-id="93646-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93646-110">範例</span><span class="sxs-lookup"><span data-stu-id="93646-110">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="93646-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93646-111">See Also</span></span>  
 [<span data-ttu-id="93646-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="93646-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="93646-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="93646-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="93646-114">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="93646-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="93646-115">C# 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="93646-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
