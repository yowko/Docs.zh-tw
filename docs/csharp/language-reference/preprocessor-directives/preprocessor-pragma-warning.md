---
title: "#<a name=\"pragma-warning-c-reference\"></a>pragma 警告 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 75c11acfd096d36c96ceb9e9c5c0d16e47e58fa1
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="d14ef-102">#pragma warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d14ef-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="d14ef-103">`#pragma warning` 可以啟用或停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="d14ef-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="d14ef-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d14ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="d14ef-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="d14ef-106">警告編號的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="d14ef-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="d14ef-107">"CS" 前置詞是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d14ef-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="d14ef-108">未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。</span><span class="sxs-lookup"><span data-stu-id="d14ef-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d14ef-109">若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出] 視窗中尋找警告編號。</span><span class="sxs-lookup"><span data-stu-id="d14ef-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d14ef-110">範例</span><span class="sxs-lookup"><span data-stu-id="d14ef-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d14ef-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d14ef-111">See Also</span></span>  
 <span data-ttu-id="d14ef-112">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d14ef-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d14ef-113">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d14ef-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d14ef-114">[C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="d14ef-114">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 [<span data-ttu-id="d14ef-115">C# 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="d14ef-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)

