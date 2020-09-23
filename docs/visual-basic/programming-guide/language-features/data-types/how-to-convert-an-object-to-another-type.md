---
title: 作法：將物件轉換成其他類型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: b89e996324d9ec22fc243b59502f3d36fefdee60
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090218"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="b0cb0-102">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="b0cb0-102">How to: Convert an Object to Another Type in Visual Basic</span></span>

<span data-ttu-id="b0cb0-103">您可以 `Object` 使用轉換關鍵字（例如 [CType 函數](../../../language-reference/functions/ctype-function.md)）將變數轉換成另一種資料類型。</span><span class="sxs-lookup"><span data-stu-id="b0cb0-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0cb0-104">範例</span><span class="sxs-lookup"><span data-stu-id="b0cb0-104">Example</span></span>  

 <span data-ttu-id="b0cb0-105">下列範例會將 `Object` 變數轉換成 `Integer` 和 `String` 。</span><span class="sxs-lookup"><span data-stu-id="b0cb0-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="b0cb0-106">如果您知道變數的內容 `Object` 是特定的資料類型，最好將變數轉換成該資料類型。</span><span class="sxs-lookup"><span data-stu-id="b0cb0-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="b0cb0-107">如果您繼續使用此 `Object` 變數，則會產生) 的數值型別或*晚期繫結* (（) 的參考型別）的 (的*裝箱*和*取消*加入。</span><span class="sxs-lookup"><span data-stu-id="b0cb0-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="b0cb0-108">這些作業都需要花費更多的執行時間，並讓您的效能變慢。</span><span class="sxs-lookup"><span data-stu-id="b0cb0-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="b0cb0-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b0cb0-109">Compile the code</span></span>  

 <span data-ttu-id="b0cb0-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b0cb0-110">This example requires:</span></span>  
  
- <span data-ttu-id="b0cb0-111"><xref:System?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="b0cb0-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cb0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0cb0-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="b0cb0-113">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="b0cb0-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="b0cb0-114">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="b0cb0-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b0cb0-115">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="b0cb0-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="b0cb0-116">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="b0cb0-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="b0cb0-117">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="b0cb0-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="b0cb0-118">結構</span><span class="sxs-lookup"><span data-stu-id="b0cb0-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="b0cb0-119">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="b0cb0-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="b0cb0-120">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="b0cb0-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
