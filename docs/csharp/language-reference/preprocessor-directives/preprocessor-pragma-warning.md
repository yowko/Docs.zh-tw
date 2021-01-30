---
description: '##pragma warning - C# 參考'
title: '##pragma warning - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215988"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="0d6e7-103">#pragma warning (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0d6e7-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="0d6e7-104">`#pragma warning` 可以啟用或停用特定警告。</span><span class="sxs-lookup"><span data-stu-id="0d6e7-104">`#pragma warning` can enable or disable certain warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d6e7-105">語法</span><span class="sxs-lookup"><span data-stu-id="0d6e7-105">Syntax</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a><span data-ttu-id="0d6e7-106">參數</span><span class="sxs-lookup"><span data-stu-id="0d6e7-106">Parameters</span></span>

 <span data-ttu-id="0d6e7-107">`warning-list` 以逗號分隔的警告編號清單。</span><span class="sxs-lookup"><span data-stu-id="0d6e7-107">`warning-list` A comma-separated list of warning numbers.</span></span> <span data-ttu-id="0d6e7-108">"CS" 前置詞是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0d6e7-108">The "CS" prefix is optional.</span></span>

 <span data-ttu-id="0d6e7-109">未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。</span><span class="sxs-lookup"><span data-stu-id="0d6e7-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="0d6e7-110">若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出] 視窗中尋找警告編號。</span><span class="sxs-lookup"><span data-stu-id="0d6e7-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

## <a name="example"></a><span data-ttu-id="0d6e7-111">範例</span><span class="sxs-lookup"><span data-stu-id="0d6e7-111">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0d6e7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d6e7-112">See also</span></span>

- [<span data-ttu-id="0d6e7-113">C # 參考</span><span class="sxs-lookup"><span data-stu-id="0d6e7-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d6e7-114">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0d6e7-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0d6e7-115">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="0d6e7-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="0d6e7-116">C # 編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="0d6e7-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
- [<span data-ttu-id="0d6e7-117">如何隱藏程式碼分析警告</span><span class="sxs-lookup"><span data-stu-id="0d6e7-117">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
