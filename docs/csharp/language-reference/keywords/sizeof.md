---
title: sizeof - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 8bb6d4a37b2eea3060921937cf15a1fdd1be97b4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634002"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="96d28-102">sizeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="96d28-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="96d28-103">用來取得 Unmanaged 類型的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="96d28-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="96d28-104">Unmanaged 類型包括：</span><span class="sxs-lookup"><span data-stu-id="96d28-104">Unmanaged types include:</span></span>

- <span data-ttu-id="96d28-105">下表列出的簡單型別：</span><span class="sxs-lookup"><span data-stu-id="96d28-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="96d28-106">運算式</span><span class="sxs-lookup"><span data-stu-id="96d28-106">Expression</span></span>|<span data-ttu-id="96d28-107">常數值</span><span class="sxs-lookup"><span data-stu-id="96d28-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="96d28-108">1</span><span class="sxs-lookup"><span data-stu-id="96d28-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="96d28-109">1</span><span class="sxs-lookup"><span data-stu-id="96d28-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="96d28-110">2</span><span class="sxs-lookup"><span data-stu-id="96d28-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="96d28-111">2</span><span class="sxs-lookup"><span data-stu-id="96d28-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="96d28-112">4</span><span class="sxs-lookup"><span data-stu-id="96d28-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="96d28-113">4</span><span class="sxs-lookup"><span data-stu-id="96d28-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="96d28-114">8</span><span class="sxs-lookup"><span data-stu-id="96d28-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="96d28-115">8</span><span class="sxs-lookup"><span data-stu-id="96d28-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="96d28-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="96d28-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="96d28-117">4</span><span class="sxs-lookup"><span data-stu-id="96d28-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="96d28-118">8</span><span class="sxs-lookup"><span data-stu-id="96d28-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="96d28-119">16</span><span class="sxs-lookup"><span data-stu-id="96d28-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="96d28-120">1</span><span class="sxs-lookup"><span data-stu-id="96d28-120">1</span></span>|

- <span data-ttu-id="96d28-121">列舉類型。</span><span class="sxs-lookup"><span data-stu-id="96d28-121">Enum types.</span></span>

- <span data-ttu-id="96d28-122">指標類型。</span><span class="sxs-lookup"><span data-stu-id="96d28-122">Pointer types.</span></span>

- <span data-ttu-id="96d28-123">未包含本身為參考型別或建構類型的任何執行個體欄位或自動實作執行個體屬性的使用者定義結構。</span><span class="sxs-lookup"><span data-stu-id="96d28-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="96d28-124">下列範例示範如何擷取 `int` 的大小：</span><span class="sxs-lookup"><span data-stu-id="96d28-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="96d28-125">備註</span><span class="sxs-lookup"><span data-stu-id="96d28-125">Remarks</span></span>

<span data-ttu-id="96d28-126">從 C# 2.0 版開始，將 `sizeof` 套用至簡單型別或列舉類型不再需要於[不安全](unsafe.md)的內容中編譯該程式碼。</span><span class="sxs-lookup"><span data-stu-id="96d28-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="96d28-127">無法多載 `sizeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="96d28-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="96d28-128">`sizeof` 運算子所傳回值的類型為 `int`。</span><span class="sxs-lookup"><span data-stu-id="96d28-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="96d28-129">上表所顯示的常數值會替代為將特定簡單型別當做運算元的 `sizeof` 運算式。</span><span class="sxs-lookup"><span data-stu-id="96d28-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="96d28-130">對於所有其他類型 (包含結構)，`sizeof` 運算子都只能用於 unsafe 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="96d28-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="96d28-131">雖然您可以使用 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法，但是這種方法所傳回的值不一定與 `sizeof` 所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="96d28-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="96d28-132">封送處理類型之後，<xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 會傳回大小，而 `sizeof` 會傳回 Common Language Runtime 所配置的大小，包括任何填補字元。</span><span class="sxs-lookup"><span data-stu-id="96d28-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="96d28-133">範例</span><span class="sxs-lookup"><span data-stu-id="96d28-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="96d28-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="96d28-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="96d28-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96d28-135">See also</span></span>

- [<span data-ttu-id="96d28-136">C# 參考</span><span class="sxs-lookup"><span data-stu-id="96d28-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="96d28-137">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="96d28-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="96d28-138">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="96d28-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="96d28-139">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="96d28-139">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="96d28-140">enum</span><span class="sxs-lookup"><span data-stu-id="96d28-140">enum</span></span>](enum.md)
- [<span data-ttu-id="96d28-141">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="96d28-141">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="96d28-142">結構</span><span class="sxs-lookup"><span data-stu-id="96d28-142">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="96d28-143">常數</span><span class="sxs-lookup"><span data-stu-id="96d28-143">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)
