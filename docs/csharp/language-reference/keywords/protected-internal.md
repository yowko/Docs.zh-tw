---
description: protected internal - C# 參考
title: protected internal - C# 參考
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: f22de104154df74f02c048b1209eeac754a03e64
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536794"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="7efa6-103">protected internal (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7efa6-103">protected internal (C# Reference)</span></span>

<span data-ttu-id="7efa6-104">`protected internal` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7efa6-104">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="7efa6-105">protected internal 成員可以從目前的組件或衍生自包含類別的類型存取。</span><span class="sxs-lookup"><span data-stu-id="7efa6-105">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="7efa6-106">如需 `protected internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="7efa6-106">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="7efa6-107">範例</span><span class="sxs-lookup"><span data-stu-id="7efa6-107">Example</span></span>

<span data-ttu-id="7efa6-108">基底類別的 protected internal 成員可以從其包含組件內的任何類型存取。</span><span class="sxs-lookup"><span data-stu-id="7efa6-108">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="7efa6-109">它也可以在位於另一個組件的衍生類別內存取，但只能是在透過衍生類別類型的變數進行存取之時。</span><span class="sxs-lookup"><span data-stu-id="7efa6-109">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="7efa6-110">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="7efa6-110">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="7efa6-111">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。</span><span class="sxs-lookup"><span data-stu-id="7efa6-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="7efa6-112">第一個檔案包含公用的基底類別 `BaseClass`，以及另一個類別 `TestAccess`。</span><span class="sxs-lookup"><span data-stu-id="7efa6-112">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="7efa6-113">`BaseClass` 擁有 protected internal 成員 `myValue`，它是由 `TestAccess` 類型存取。</span><span class="sxs-lookup"><span data-stu-id="7efa6-113">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="7efa6-114">在第二個檔案中，嘗試透過 `BaseClass` 的執行個體存取 `myValue` 會產生錯誤，而透過衍生類別 `DerivedClass` 的執行個體存取這個成員時會成功。</span><span class="sxs-lookup"><span data-stu-id="7efa6-114">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="7efa6-115">結構成員不可以是 `protected internal`，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="7efa6-115">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7efa6-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="7efa6-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7efa6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7efa6-117">See also</span></span>

- [<span data-ttu-id="7efa6-118">C # 參考</span><span class="sxs-lookup"><span data-stu-id="7efa6-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7efa6-119">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7efa6-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7efa6-120">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="7efa6-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7efa6-121">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="7efa6-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="7efa6-122">協助工具層級</span><span class="sxs-lookup"><span data-stu-id="7efa6-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="7efa6-123">修飾詞</span><span class="sxs-lookup"><span data-stu-id="7efa6-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7efa6-124">public</span><span class="sxs-lookup"><span data-stu-id="7efa6-124">public</span></span>](public.md)
- [<span data-ttu-id="7efa6-125">private</span><span class="sxs-lookup"><span data-stu-id="7efa6-125">private</span></span>](private.md)
- [<span data-ttu-id="7efa6-126">internal</span><span class="sxs-lookup"><span data-stu-id="7efa6-126">internal</span></span>](internal.md)
- <span data-ttu-id="7efa6-127">[internal virtual 關鍵字的安全性考量](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7efa6-127">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
