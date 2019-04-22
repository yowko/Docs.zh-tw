---
title: HOW TO：在 Visual Basic 中的字串中的存取字元
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 840a769b0bb322ef7b878a312437c5ec200ab074
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834487"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="dd5cb-102">HOW TO：在 Visual Basic 中的字串中的存取字元</span><span class="sxs-lookup"><span data-stu-id="dd5cb-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="dd5cb-103">此範例示範如何使用<xref:System.String.Chars%2A>屬性來存取字串中指定的位置處的字元。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd5cb-104">範例</span><span class="sxs-lookup"><span data-stu-id="dd5cb-104">Example</span></span>  
 <span data-ttu-id="dd5cb-105">有時候最好擁有您的字串與這些字元在字串中的位置中的字元資料。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="dd5cb-106">您可以將字串視為字元陣列 (`Char`執行個體)，您可以藉由參考到該字元的索引來擷取特定字元<xref:System.String.Chars%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="dd5cb-107">`index`參數<xref:System.String.Chars%2A>屬性是以零為起始。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dd5cb-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="dd5cb-108">Robust Programming</span></span>  
 <span data-ttu-id="dd5cb-109"><xref:System.String.Chars%2A>屬性會傳回指定位置處的字元。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="dd5cb-110">不過，某些 Unicode 字元可以表示多個字元。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="dd5cb-111">如需有關如何使用 Unicode 字元的詳細資訊，請參閱[How to:將字串轉換為字元陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="dd5cb-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="dd5cb-112"><xref:System.String.Chars%2A>屬性會擲回<xref:System.IndexOutOfRangeException>例外狀況如果`index`參數是否大於或等於字串的長度，或如果它小於零</span><span class="sxs-lookup"><span data-stu-id="dd5cb-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5cb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5cb-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="dd5cb-114">如何：將字串轉換為字元陣列</span><span class="sxs-lookup"><span data-stu-id="dd5cb-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="dd5cb-115">在 Visual Basic 中的字串和其他資料類型之間進行轉換</span><span class="sxs-lookup"><span data-stu-id="dd5cb-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="dd5cb-116">字串</span><span class="sxs-lookup"><span data-stu-id="dd5cb-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
