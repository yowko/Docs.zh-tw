---
title: 如何：將物件轉換成另一種類型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341578"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="50c40-102">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="50c40-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="50c40-103">您可以使用轉換關鍵字（例如[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)），將 `Object` 變數轉換成另一個資料類型。</span><span class="sxs-lookup"><span data-stu-id="50c40-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50c40-104">範例</span><span class="sxs-lookup"><span data-stu-id="50c40-104">Example</span></span>  
 <span data-ttu-id="50c40-105">下列範例會將 `Object` 變數轉換成 `Integer` 和 `String`。</span><span class="sxs-lookup"><span data-stu-id="50c40-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="50c40-106">如果您知道 `Object` 變數的內容是特定的資料類型，最好將變數轉換成該資料類型。</span><span class="sxs-lookup"><span data-stu-id="50c40-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="50c40-107">如果您繼續使用 `Object` 變數，則會產生*裝箱*和*取消裝箱*（適用于實值型別）或*晚期繫結*（針對引用型別）。</span><span class="sxs-lookup"><span data-stu-id="50c40-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="50c40-108">這些作業都需要額外的執行時間，讓您的效能變慢。</span><span class="sxs-lookup"><span data-stu-id="50c40-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="50c40-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="50c40-109">Compile the code</span></span>  
 <span data-ttu-id="50c40-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="50c40-110">This example requires:</span></span>  
  
- <span data-ttu-id="50c40-111"><xref:System?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="50c40-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c40-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="50c40-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="50c40-113">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="50c40-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="50c40-114">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="50c40-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="50c40-115">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="50c40-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="50c40-116">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="50c40-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="50c40-117">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="50c40-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="50c40-118">結構</span><span class="sxs-lookup"><span data-stu-id="50c40-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="50c40-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="50c40-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="50c40-120">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="50c40-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
