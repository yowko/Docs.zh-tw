---
title: sizeof (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: f2507dd8528e2e66016524873ada890227a74ed8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487191"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="c452c-102">sizeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c452c-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="c452c-103">用來取得 Unmanaged 類型的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="c452c-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="c452c-104">Unmanaged 類型包括：</span><span class="sxs-lookup"><span data-stu-id="c452c-104">Unmanaged types include:</span></span>

-   <span data-ttu-id="c452c-105">下表列出的簡單型別：</span><span class="sxs-lookup"><span data-stu-id="c452c-105">The simple types that are listed in the following table:</span></span>
  
   |<span data-ttu-id="c452c-106">運算式</span><span class="sxs-lookup"><span data-stu-id="c452c-106">Expression</span></span>|<span data-ttu-id="c452c-107">常數值</span><span class="sxs-lookup"><span data-stu-id="c452c-107">Constant value</span></span>|  
   |----------------|--------------------|  
   |`sizeof(sbyte)`|<span data-ttu-id="c452c-108">1</span><span class="sxs-lookup"><span data-stu-id="c452c-108">1</span></span>|  
   |`sizeof(byte)`|<span data-ttu-id="c452c-109">1</span><span class="sxs-lookup"><span data-stu-id="c452c-109">1</span></span>|  
   |`sizeof(short)`|<span data-ttu-id="c452c-110">2</span><span class="sxs-lookup"><span data-stu-id="c452c-110">2</span></span>|  
   |`sizeof(ushort)`|<span data-ttu-id="c452c-111">2</span><span class="sxs-lookup"><span data-stu-id="c452c-111">2</span></span>|  
   |`sizeof(int)`|<span data-ttu-id="c452c-112">4</span><span class="sxs-lookup"><span data-stu-id="c452c-112">4</span></span>|  
   |`sizeof(uint)`|<span data-ttu-id="c452c-113">4</span><span class="sxs-lookup"><span data-stu-id="c452c-113">4</span></span>|  
   |`sizeof(long)`|<span data-ttu-id="c452c-114">8</span><span class="sxs-lookup"><span data-stu-id="c452c-114">8</span></span>|  
   |`sizeof(ulong)`|<span data-ttu-id="c452c-115">8</span><span class="sxs-lookup"><span data-stu-id="c452c-115">8</span></span>|  
   |`sizeof(char)`|<span data-ttu-id="c452c-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="c452c-116">2 (Unicode)</span></span>|  
   |`sizeof(float)`|<span data-ttu-id="c452c-117">4</span><span class="sxs-lookup"><span data-stu-id="c452c-117">4</span></span>|  
   |`sizeof(double)`|<span data-ttu-id="c452c-118">8</span><span class="sxs-lookup"><span data-stu-id="c452c-118">8</span></span>|  
   |`sizeof(decimal)`|<span data-ttu-id="c452c-119">16</span><span class="sxs-lookup"><span data-stu-id="c452c-119">16</span></span>|  
   |`sizeof(bool)`|<span data-ttu-id="c452c-120">1</span><span class="sxs-lookup"><span data-stu-id="c452c-120">1</span></span>| 
  
-   <span data-ttu-id="c452c-121">列舉類型。</span><span class="sxs-lookup"><span data-stu-id="c452c-121">Enum types.</span></span>
  
-   <span data-ttu-id="c452c-122">指標類型。</span><span class="sxs-lookup"><span data-stu-id="c452c-122">Pointer types.</span></span>
  
-   <span data-ttu-id="c452c-123">未包含本身為參考型別或建構類型的任何執行個體欄位或自動實作執行個體屬性的使用者定義結構。</span><span class="sxs-lookup"><span data-stu-id="c452c-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>
  
 <span data-ttu-id="c452c-124">下列範例示範如何擷取 `int` 的大小：</span><span class="sxs-lookup"><span data-stu-id="c452c-124">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="c452c-125">備註</span><span class="sxs-lookup"><span data-stu-id="c452c-125">Remarks</span></span>  
 <span data-ttu-id="c452c-126">從 C# 2.0 版開始，將 `sizeof` 套用至簡單型別或列舉類型不再需要於[不安全](unsafe.md)的內容中編譯該程式碼。</span><span class="sxs-lookup"><span data-stu-id="c452c-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>
  
 <span data-ttu-id="c452c-127">無法多載 `sizeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="c452c-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="c452c-128">`sizeof` 運算子所傳回值的類型為 `int`。</span><span class="sxs-lookup"><span data-stu-id="c452c-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="c452c-129">上表所顯示的常數值會替代為將特定簡單型別當做運算元的 `sizeof` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c452c-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>  
    
 <span data-ttu-id="c452c-130">對於所有其他類型 (包含結構)，`sizeof` 運算子都只能用於 unsafe 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c452c-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="c452c-131">雖然您可以使用 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法，但是這種方法所傳回的值不一定與 `sizeof` 所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="c452c-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="c452c-132">封送處理類型之後，<xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 會傳回大小，而 `sizeof` 會傳回 Common Language Runtime 所配置的大小，包括任何填補字元。</span><span class="sxs-lookup"><span data-stu-id="c452c-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c452c-133">範例</span><span class="sxs-lookup"><span data-stu-id="c452c-133">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c452c-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c452c-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c452c-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="c452c-135">See Also</span></span>

- [<span data-ttu-id="c452c-136">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c452c-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c452c-137">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c452c-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c452c-138">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c452c-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c452c-139">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="c452c-139">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [<span data-ttu-id="c452c-140">enum</span><span class="sxs-lookup"><span data-stu-id="c452c-140">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
- [<span data-ttu-id="c452c-141">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="c452c-141">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="c452c-142">結構</span><span class="sxs-lookup"><span data-stu-id="c452c-142">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [<span data-ttu-id="c452c-143">常數</span><span class="sxs-lookup"><span data-stu-id="c452c-143">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
