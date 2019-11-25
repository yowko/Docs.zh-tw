---
title: 'How to: Create a C-C++ Union by Using Attributes'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: acb8dc781e2872ae46e5aa058a98b3dd98f3e064
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349503"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="8a161-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a161-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="8a161-103">您可以使用屬性，自訂如何在記憶體中配置結構。</span><span class="sxs-lookup"><span data-stu-id="8a161-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="8a161-104">例如，您可以使用 `StructLayout(LayoutKind.Explicit)` 和 `FieldOffset` 屬性，以 C/C++ 建立所謂的等位。</span><span class="sxs-lookup"><span data-stu-id="8a161-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="8a161-105">範例</span><span class="sxs-lookup"><span data-stu-id="8a161-105">Example</span></span>

<span data-ttu-id="8a161-106">在此程式碼片段中，`TestUnion` 的所有欄位都在記憶體的同一位置開始。</span><span class="sxs-lookup"><span data-stu-id="8a161-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a><span data-ttu-id="8a161-107">範例</span><span class="sxs-lookup"><span data-stu-id="8a161-107">Example</span></span>

<span data-ttu-id="8a161-108">以下是另一個範例，欄位從明確設定的不同位置開始。</span><span class="sxs-lookup"><span data-stu-id="8a161-108">The following is another example where fields start at different explicitly set locations.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

<span data-ttu-id="8a161-109">`i1` 和 `i2` 這兩個整數欄位和 `lg` 共用相同的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="8a161-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="8a161-110">使用平台叫用時，這種結構配置控制項很有用。</span><span class="sxs-lookup"><span data-stu-id="8a161-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a161-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a161-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="8a161-112">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8a161-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="8a161-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8a161-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="8a161-114">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a161-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="8a161-115">屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a161-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="8a161-116">建立自訂屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a161-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="8a161-117">使用反映存取屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a161-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
