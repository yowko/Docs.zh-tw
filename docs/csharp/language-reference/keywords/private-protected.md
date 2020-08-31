---
description: private protected - C# 參考
title: private protected - C# 參考
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: d83fd2a570b735a029bd2a79ad24e30d235dc5fb
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117957"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="03ea0-103">private protected (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="03ea0-103">private protected (C# Reference)</span></span>

<span data-ttu-id="03ea0-104">`private protected` 關鍵字組合是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03ea0-104">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="03ea0-105">從包含類別衍生的類型可以存取 private protected 成員，但只能在其包含的組件內存取。</span><span class="sxs-lookup"><span data-stu-id="03ea0-105">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="03ea0-106">如需 `private protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="03ea0-106">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="03ea0-107">`private protected` 存取修飾詞適用於 C# 7.2 版及更新版本。</span><span class="sxs-lookup"><span data-stu-id="03ea0-107">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="03ea0-108">範例</span><span class="sxs-lookup"><span data-stu-id="03ea0-108">Example</span></span>

<span data-ttu-id="03ea0-109">只有當變數的靜態類型是在衍生的類別類型時，才能從包含組件的衍生類型中存取基底類別的 private protected 成員。</span><span class="sxs-lookup"><span data-stu-id="03ea0-109">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="03ea0-110">例如，請考慮下列程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="03ea0-110">For example, consider the following code segment:</span></span>

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

<span data-ttu-id="03ea0-111">此範例包含兩個檔案：`Assembly1.cs` 和 `Assembly2.cs`。</span><span class="sxs-lookup"><span data-stu-id="03ea0-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="03ea0-112">第一個檔案包含公用的基底類別 `BaseClass`，以及從其衍生的類型 `DerivedClass1`。</span><span class="sxs-lookup"><span data-stu-id="03ea0-112">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="03ea0-113">`BaseClass` 擁有 private protected 成員 `myValue`，`DerivedClass1` 會以兩種方式嘗試存取它。</span><span class="sxs-lookup"><span data-stu-id="03ea0-113">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="03ea0-114">第一次嘗試透過 `BaseClass` 的執行個體存取 `myValue` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="03ea0-114">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="03ea0-115">不過，嘗試將它當作 `DerivedClass1` 中的繼承成員使用會成功。</span><span class="sxs-lookup"><span data-stu-id="03ea0-115">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="03ea0-116">在第二個檔案中，嘗試當作 `DerivedClass2` 的繼承成員存取 `myValue` 會產生錯誤，因為它只能由 Assembly1 中的衍生類型存取。</span><span class="sxs-lookup"><span data-stu-id="03ea0-116">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="03ea0-117">如果 `Assembly1.cs` 包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 該名稱 `Assembly2` ，則衍生類別 `DerivedClass1` 將可存取中宣告的 `private protected` 成員 `BaseClass` 。</span><span class="sxs-lookup"><span data-stu-id="03ea0-117">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="03ea0-118">`InternalsVisibleTo` 讓 `private protected` 其他元件中的衍生類別可以看到成員。</span><span class="sxs-lookup"><span data-stu-id="03ea0-118">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="03ea0-119">結構成員不可以是 `private protected`，因為無法繼承結構。</span><span class="sxs-lookup"><span data-stu-id="03ea0-119">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03ea0-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="03ea0-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03ea0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03ea0-121">See also</span></span>

- [<span data-ttu-id="03ea0-122">C # 參考</span><span class="sxs-lookup"><span data-stu-id="03ea0-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03ea0-123">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="03ea0-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03ea0-124">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="03ea0-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03ea0-125">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="03ea0-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="03ea0-126">協助工具層級</span><span class="sxs-lookup"><span data-stu-id="03ea0-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="03ea0-127">修飾詞</span><span class="sxs-lookup"><span data-stu-id="03ea0-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="03ea0-128">public</span><span class="sxs-lookup"><span data-stu-id="03ea0-128">public</span></span>](public.md)
- [<span data-ttu-id="03ea0-129">私人</span><span class="sxs-lookup"><span data-stu-id="03ea0-129">private</span></span>](private.md)
- [<span data-ttu-id="03ea0-130">internal</span><span class="sxs-lookup"><span data-stu-id="03ea0-130">internal</span></span>](internal.md)
- <span data-ttu-id="03ea0-131">[internal virtual 關鍵字的安全性考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="03ea0-131">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
