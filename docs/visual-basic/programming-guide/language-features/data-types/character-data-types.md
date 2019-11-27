---
title: 字元資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346387"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="260de-102">字元資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="260de-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="260de-103">Visual Basic 提供*字元資料類型*，以處理可列印和可顯示的字元。</span><span class="sxs-lookup"><span data-stu-id="260de-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="260de-104">雖然兩者都處理 Unicode 字元，但 `Char` 保留單一字元，而 `String` 包含不限數目的字元。</span><span class="sxs-lookup"><span data-stu-id="260de-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="260de-105">如需顯示 Visual Basic 資料類型並存比較的資料表，請參閱[資料類型](../../../../visual-basic/language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="260de-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="260de-106">Char 類型</span><span class="sxs-lookup"><span data-stu-id="260de-106">Char Type</span></span>  
 <span data-ttu-id="260de-107">`Char` 資料類型是單一的雙位元組（16位） Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="260de-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="260de-108">如果變數一律只儲存一個字元，請將它宣告為 `Char`。</span><span class="sxs-lookup"><span data-stu-id="260de-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="260de-109">例如：</span><span class="sxs-lookup"><span data-stu-id="260de-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="260de-110">`Char` 或 `String` 變數中的每個可能值都是 Unicode 字元集中的程式*代碼點*或字元碼。</span><span class="sxs-lookup"><span data-stu-id="260de-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="260de-111">Unicode 字元包括基本 ASCII 字元集、其他各種字母字母、重音、貨幣符號、分數、變音符號和數學和技術符號。</span><span class="sxs-lookup"><span data-stu-id="260de-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="260de-112">Unicode 字元集會針對*代理配對*保留 D800 到 DFFF （55296到 55551 decimal）的程式碼點，其需要 2 16 位值來表示單一程式碼點。</span><span class="sxs-lookup"><span data-stu-id="260de-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="260de-113">`Char` 變數不能保存代理配對，而 `String` 使用兩個位置來保存這種配對。</span><span class="sxs-lookup"><span data-stu-id="260de-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="260de-114">如需詳細資訊，請參閱[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="260de-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="260de-115">字串類型</span><span class="sxs-lookup"><span data-stu-id="260de-115">String Type</span></span>  
 <span data-ttu-id="260de-116">`String` 資料類型是零個或多個兩個位元組（16位） Unicode 字元的序列。</span><span class="sxs-lookup"><span data-stu-id="260de-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="260de-117">如果變數可以包含不限數量的字元，請將它宣告為 `String`。</span><span class="sxs-lookup"><span data-stu-id="260de-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="260de-118">例如：</span><span class="sxs-lookup"><span data-stu-id="260de-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="260de-119">如需詳細資訊，請參閱[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="260de-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260de-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="260de-120">See also</span></span>

- [<span data-ttu-id="260de-121">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="260de-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="260de-122">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="260de-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="260de-123">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="260de-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="260de-124">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="260de-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="260de-125">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="260de-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="260de-126">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="260de-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="260de-127">類型字元</span><span class="sxs-lookup"><span data-stu-id="260de-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
