---
title: 如何：存取字串中的字元
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 4ea37c4393a8ece5513327b22c6c0ba4b027c781
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059180"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="ad1cf-102">如何：在 Visual Basic 中存取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="ad1cf-102">How to: Access Characters in Strings in Visual Basic</span></span>

<span data-ttu-id="ad1cf-103">這個範例示範如何使用 <xref:System.String.Chars%2A> 屬性來存取字串中指定位置的字元。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad1cf-104">範例</span><span class="sxs-lookup"><span data-stu-id="ad1cf-104">Example</span></span>  

 <span data-ttu-id="ad1cf-105">有時候您的字串中的字元和字串內的字元位置會有很大的説明。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="ad1cf-106">您可以將字串視為 (實例) 的字元陣列 `Char` ; 您可以透過屬性參考該字元的索引來抓取特定字元 <xref:System.String.Chars%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="ad1cf-107">`index`屬性的參數 <xref:System.String.Chars%2A> 是以零為基底。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ad1cf-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="ad1cf-108">Robust Programming</span></span>  

 <span data-ttu-id="ad1cf-109">屬性會傳回 <xref:System.String.Chars%2A> 指定位置的字元。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="ad1cf-110">不過，某些 Unicode 字元可以用一個以上的字元來表示。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="ad1cf-111">如需如何使用 Unicode 字元的詳細資訊，請參閱 [如何：將字串轉換為字元陣列](how-to-convert-a-string-to-an-array-of-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="ad1cf-112"><xref:System.String.Chars%2A> <xref:System.IndexOutOfRangeException> 如果 `index` 參數大於或等於字串的長度，或小於零，屬性會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ad1cf-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1cf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad1cf-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="ad1cf-114">如何：將字串轉換為字元陣列</span><span class="sxs-lookup"><span data-stu-id="ad1cf-114">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="ad1cf-115">在 Visual Basic 中的字串和其他資料類型之間進行轉換</span><span class="sxs-lookup"><span data-stu-id="ad1cf-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="ad1cf-116">字串</span><span class="sxs-lookup"><span data-stu-id="ad1cf-116">Strings</span></span>](index.md)
