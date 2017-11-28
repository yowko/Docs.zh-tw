---
title: "如何：使用屬性建立 C-C++ 等位 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 450fb922079ca6737b8db7754f25435b9c3b884b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="063b1-102">如何：使用屬性建立 C/C++ 等位 (C#)</span><span class="sxs-lookup"><span data-stu-id="063b1-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="063b1-103">您可以使用屬性，自訂如何在記憶體中配置結構。</span><span class="sxs-lookup"><span data-stu-id="063b1-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="063b1-104">例如，您可以使用 `StructLayout(LayoutKind.Explicit)` 和 `FieldOffset` 屬性，以 C/C++ 建立所謂的等位。</span><span class="sxs-lookup"><span data-stu-id="063b1-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="063b1-105">範例</span><span class="sxs-lookup"><span data-stu-id="063b1-105">Example</span></span>  
 <span data-ttu-id="063b1-106">在此程式碼片段中，`TestUnion` 的所有欄位都在記憶體的同一位置開始。</span><span class="sxs-lookup"><span data-stu-id="063b1-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a><span data-ttu-id="063b1-107">範例</span><span class="sxs-lookup"><span data-stu-id="063b1-107">Example</span></span>  
 <span data-ttu-id="063b1-108">以下是另一個範例，欄位從明確設定的不同位置開始。</span><span class="sxs-lookup"><span data-stu-id="063b1-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 <span data-ttu-id="063b1-109">`i1` 和 `i2` 這兩個整數欄位和 `lg` 共用相同的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="063b1-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="063b1-110">使用平台叫用時，這種結構配置控制項很有用。</span><span class="sxs-lookup"><span data-stu-id="063b1-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063b1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="063b1-111">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="063b1-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="063b1-112">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="063b1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="063b1-113">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="063b1-114">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="063b1-114">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="063b1-115">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="063b1-115">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="063b1-116">建立自訂屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="063b1-116">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="063b1-117">使用反射存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="063b1-117">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
