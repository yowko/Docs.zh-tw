---
title: "字元資料類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data types [Visual Basic], character
- String data type, character data types
- character data types [Visual Basic]
- Char data type, character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3407f614d5898f4fccf04e0363ec31669661b60a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="864ad-102">字元資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="864ad-102">Character Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="864ad-103">提供*字元資料類型*應付可顯示的可列印字元。</span><span class="sxs-lookup"><span data-stu-id="864ad-103"> provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="864ad-104">雖然兩者處理 Unicode 字元`Char`保存單一字元，而`String`包含任何數目的字元。</span><span class="sxs-lookup"><span data-stu-id="864ad-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="864ad-105">顯示並行所比較之資料表的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="864ad-105">For a table that displays a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="864ad-106">Char 類型</span><span class="sxs-lookup"><span data-stu-id="864ad-106">Char Type</span></span>  
 <span data-ttu-id="864ad-107">`Char`資料型別是單一的兩個位元組 （16 位元） 的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="864ad-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="864ad-108">如果變數只會儲存一個字元，將它宣告為`Char`。</span><span class="sxs-lookup"><span data-stu-id="864ad-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="864ad-109">例如: </span><span class="sxs-lookup"><span data-stu-id="864ad-109">For example:</span></span>  
  
 <span data-ttu-id="864ad-110">[!code-vb[VbVbalrCharTypes #&1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="864ad-110">[!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="864ad-111">在每個可能值`Char`或`String`變數是*程式碼點*，或在 Unicode 字元集的字元碼。</span><span class="sxs-lookup"><span data-stu-id="864ad-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="864ad-112">Unicode 字元包含基本 ASCII 字元集、 各種其他字母字元、 腔調字、 貨幣符號、 分數、 變音符號和數學和技術的符號。</span><span class="sxs-lookup"><span data-stu-id="864ad-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="864ad-113">Unicode 字元集字碼元素 D800 到 DFFF (55296 透過 55551 十進位) 的保留*surrogate 配對*，而這需要兩個 16 位元的值代表單一字碼指標。</span><span class="sxs-lookup"><span data-stu-id="864ad-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="864ad-114">A`Char`變數不能保留 surrogate 字組和`String`會使用兩個位置來容納這些組。</span><span class="sxs-lookup"><span data-stu-id="864ad-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="864ad-115">如需詳細資訊，請參閱[Char 資料型別](../../../../visual-basic/language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="864ad-115">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="864ad-116">字串型別</span><span class="sxs-lookup"><span data-stu-id="864ad-116">String Type</span></span>  
 <span data-ttu-id="864ad-117">`String`資料型別是一串零個或兩個位元組 （16 位元） Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="864ad-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="864ad-118">如果變數可以包含任何數目的字元，將它宣告為`String`。</span><span class="sxs-lookup"><span data-stu-id="864ad-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="864ad-119">例如: </span><span class="sxs-lookup"><span data-stu-id="864ad-119">For example:</span></span>  
  
 <span data-ttu-id="864ad-120">[!code-vb[VbVbalrCharTypes #&2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="864ad-120">[!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="864ad-121">如需詳細資訊，請參閱[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="864ad-121">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864ad-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="864ad-122">See Also</span></span>  
 <span data-ttu-id="864ad-123">[基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="864ad-123">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="864ad-124"> [複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="864ad-124"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="864ad-125"> [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="864ad-125"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="864ad-126"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="864ad-126"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="864ad-127"> [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="864ad-127"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="864ad-128"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="864ad-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="864ad-129"> [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="864ad-129"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
