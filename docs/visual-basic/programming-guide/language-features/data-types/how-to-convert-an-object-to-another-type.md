---
title: 如何：在 Visual Basic 中將物件轉換成其他類型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: f168b3021ee1dbe3c82edc22fc779767c30446b8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912009"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="4194d-102">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="4194d-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="4194d-103">您將轉換`Object`變數設為另一個資料類型，例如使用轉換關鍵字[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)。</span><span class="sxs-lookup"><span data-stu-id="4194d-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4194d-104">範例</span><span class="sxs-lookup"><span data-stu-id="4194d-104">Example</span></span>  
 <span data-ttu-id="4194d-105">下列範例會將轉換`Object`變數設為`Integer`和`String`。</span><span class="sxs-lookup"><span data-stu-id="4194d-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="4194d-106">如果您知道的內容`Object`變數是特定的資料類型，最好是將變數轉換成該資料型別。</span><span class="sxs-lookup"><span data-stu-id="4194d-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="4194d-107">如果您繼續使用`Object`變數，您會產生其中一個*boxing*並*unboxing* （適用於實值型別） 或*晚期繫結*（適用於參考型別）。</span><span class="sxs-lookup"><span data-stu-id="4194d-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="4194d-108">這些作業全部需要額外的執行時間，並讓您的效能降低。</span><span class="sxs-lookup"><span data-stu-id="4194d-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4194d-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4194d-109">Compiling the Code</span></span>  
 <span data-ttu-id="4194d-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4194d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="4194d-111"><xref:System?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="4194d-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4194d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4194d-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="4194d-113">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="4194d-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="4194d-114">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="4194d-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="4194d-115">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="4194d-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="4194d-116">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="4194d-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="4194d-117">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="4194d-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="4194d-118">結構</span><span class="sxs-lookup"><span data-stu-id="4194d-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="4194d-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="4194d-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="4194d-120">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="4194d-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
