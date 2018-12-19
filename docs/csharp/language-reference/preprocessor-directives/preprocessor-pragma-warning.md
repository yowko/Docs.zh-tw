---
title: '##pragma warning - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 3b50585e0ae0964cf19379573bd85923daa552f4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242715"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="fa2da-102">#pragma warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fa2da-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="fa2da-103">`#pragma warning` 可以啟用或停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="fa2da-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2da-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa2da-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa2da-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa2da-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="fa2da-106">警告編號的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="fa2da-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="fa2da-107">"CS" 前置詞是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="fa2da-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="fa2da-108">未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。</span><span class="sxs-lookup"><span data-stu-id="fa2da-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa2da-109">若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出] 視窗中尋找警告編號。</span><span class="sxs-lookup"><span data-stu-id="fa2da-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa2da-110">範例</span><span class="sxs-lookup"><span data-stu-id="fa2da-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa2da-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa2da-111">See Also</span></span>

- [<span data-ttu-id="fa2da-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="fa2da-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fa2da-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fa2da-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fa2da-114">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="fa2da-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="fa2da-115">C# 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="fa2da-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
