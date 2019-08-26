---
title: '##pragma warning - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: dc221235e78a187f921815ed6e6c7750778014d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922268"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="49c3d-102">#pragma warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="49c3d-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="49c3d-103">`#pragma warning` 可以啟用或停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="49c3d-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="49c3d-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="49c3d-105">參數</span><span class="sxs-lookup"><span data-stu-id="49c3d-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="49c3d-106">警告編號的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="49c3d-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="49c3d-107">"CS" 前置詞是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="49c3d-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="49c3d-108">未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。</span><span class="sxs-lookup"><span data-stu-id="49c3d-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49c3d-109">若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出]  視窗中尋找警告編號。</span><span class="sxs-lookup"><span data-stu-id="49c3d-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49c3d-110">範例</span><span class="sxs-lookup"><span data-stu-id="49c3d-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49c3d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49c3d-111">See also</span></span>

- [<span data-ttu-id="49c3d-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="49c3d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="49c3d-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="49c3d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="49c3d-114">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="49c3d-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="49c3d-115">C# 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="49c3d-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
