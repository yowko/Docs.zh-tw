---
title: 如何：存取字串中的字元
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352467"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="bd6ee-102">如何：在 Visual Basic 中存取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="bd6ee-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="bd6ee-103">這個範例示範如何使用 <xref:System.String.Chars%2A> 屬性來存取字串中指定位置的字元。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd6ee-104">範例</span><span class="sxs-lookup"><span data-stu-id="bd6ee-104">Example</span></span>  
 <span data-ttu-id="bd6ee-105">如果您的字串中有字元的資料，以及字串內這些字元的位置，有時會很有説明。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="bd6ee-106">您可以將字串視為字元陣列（`Char` 實例）;您可以透過 <xref:System.String.Chars%2A> 屬性來參考該字元的索引，藉此抓取特定的字元。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="bd6ee-107"><xref:System.String.Chars%2A> 屬性的 `index` 參數是以零為基底。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bd6ee-108">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="bd6ee-108">Robust Programming</span></span>  
 <span data-ttu-id="bd6ee-109"><xref:System.String.Chars%2A> 屬性會傳回指定位置的字元。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="bd6ee-110">不過，某些 Unicode 字元可以用一個以上的字元來表示。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="bd6ee-111">如需如何使用 Unicode 字元的詳細資訊，請參閱[如何：將字串轉換為字元陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="bd6ee-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="bd6ee-112">如果 `index` 參數大於或等於字串的長度，或如果小於零，<xref:System.String.Chars%2A> 屬性會擲回 <xref:System.IndexOutOfRangeException> 例外狀況</span><span class="sxs-lookup"><span data-stu-id="bd6ee-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6ee-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd6ee-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="bd6ee-114">如何：將字串轉換為字元陣列</span><span class="sxs-lookup"><span data-stu-id="bd6ee-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="bd6ee-115">在 Visual Basic 中的字串和其他資料類型之間進行轉換</span><span class="sxs-lookup"><span data-stu-id="bd6ee-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="bd6ee-116">字串</span><span class="sxs-lookup"><span data-stu-id="bd6ee-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
