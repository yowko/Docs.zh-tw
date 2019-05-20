---
title: protected internal - C# 參考
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 2a06165714095a65c23826543c309a82c43c2f9a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633316"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="f12a0-102">protected internal (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f12a0-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="f12a0-103">`protected internal` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="f12a0-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="f12a0-104">protected internal 成員可以從目前的組件或衍生自包含類別的類型存取。</span><span class="sxs-lookup"><span data-stu-id="f12a0-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="f12a0-105">如需 `protected internal` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f12a0-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="f12a0-106">範例</span><span class="sxs-lookup"><span data-stu-id="f12a0-106">Example</span></span>

<span data-ttu-id="f12a0-107">基底類別的 protected internal 成員可以從其包含組件內的任何類型存取。</span><span class="sxs-lookup"><span data-stu-id="f12a0-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="f12a0-108">它也可以在位於另一個組件的衍生類別內存取，但只能是在透過衍生類別類型的變數進行存取之時。</span><span class="sxs-lookup"><span data-stu-id="f12a0-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="f12a0-109">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="f12a0-109">For example, consider the following code segment:</span></span>

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
        BaseClass baseObject = new BaseClass();
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
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="f12a0-110">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。</span><span class="sxs-lookup"><span data-stu-id="f12a0-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="f12a0-111">第一個檔案包含公用的基底類別 `BaseClass`，以及另一個類別 `TestAccess`。</span><span class="sxs-lookup"><span data-stu-id="f12a0-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="f12a0-112">`BaseClass` 擁有 protected internal 成員 `myValue`，它是由 `TestAccess` 類型存取。</span><span class="sxs-lookup"><span data-stu-id="f12a0-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="f12a0-113">在第二個檔案中，嘗試透過 `BaseClass` 的執行個體存取 `myValue` 會產生錯誤，而透過衍生類別 `DerivedClass` 的執行個體存取這個成員時會成功。</span><span class="sxs-lookup"><span data-stu-id="f12a0-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="f12a0-114">結構成員不可以是 `protected internal`，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="f12a0-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f12a0-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f12a0-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f12a0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f12a0-116">See also</span></span>

- [<span data-ttu-id="f12a0-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f12a0-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f12a0-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f12a0-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f12a0-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f12a0-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f12a0-120">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="f12a0-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="f12a0-121">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="f12a0-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="f12a0-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="f12a0-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="f12a0-123">public</span><span class="sxs-lookup"><span data-stu-id="f12a0-123">public</span></span>](public.md)
- [<span data-ttu-id="f12a0-124">private</span><span class="sxs-lookup"><span data-stu-id="f12a0-124">private</span></span>](private.md)
- [<span data-ttu-id="f12a0-125">internal</span><span class="sxs-lookup"><span data-stu-id="f12a0-125">internal</span></span>](internal.md)
- <span data-ttu-id="f12a0-126">[internal virtual 關鍵字的安全性考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f12a0-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
