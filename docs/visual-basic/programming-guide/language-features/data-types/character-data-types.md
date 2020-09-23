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
ms.openlocfilehash: 5fde5eff40d83bdd7d90cd611bd6749106db6e16
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077172"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="222dc-102">字元資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="222dc-102">Character Data Types (Visual Basic)</span></span>

<span data-ttu-id="222dc-103">Visual Basic 提供 *字元資料類型* 來處理可列印和可顯示的字元。</span><span class="sxs-lookup"><span data-stu-id="222dc-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="222dc-104">雖然它們都處理 Unicode 字元，但會保留一個字元，而不會 `Char` `String` 包含不定數目的字元。</span><span class="sxs-lookup"><span data-stu-id="222dc-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="222dc-105">如需顯示 Visual Basic 資料類型之並列比較的資料表，請參閱 [資料類型](../../../language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="222dc-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="222dc-106">Char 類型</span><span class="sxs-lookup"><span data-stu-id="222dc-106">Char Type</span></span>  

 <span data-ttu-id="222dc-107">`Char`資料類型是單一雙位元組 (16 位) Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="222dc-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="222dc-108">如果變數永遠只儲存一個字元，請將它宣告為 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="222dc-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="222dc-109">例如：</span><span class="sxs-lookup"><span data-stu-id="222dc-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="222dc-110">或變數中的每個可能值 `Char` `String` 都是 Unicode 字元集中的程式 *代碼點*或字元碼。</span><span class="sxs-lookup"><span data-stu-id="222dc-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="222dc-111">Unicode 字元包括基本的 ASCII 字元集、各種其他字母字母、重音、貨幣符號、分數、變音符號，以及數學和技術符號。</span><span class="sxs-lookup"><span data-stu-id="222dc-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="222dc-112">Unicode 字元集會保留程式碼點 D800 至 DFFF (55296 至 55551 decimal) 用於 *代理配對*，這需要 2 16 位值以表示單一程式碼點。</span><span class="sxs-lookup"><span data-stu-id="222dc-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="222dc-113">`Char`變數無法保存代理組，而且會 `String` 使用兩個位置來保存這類配對。</span><span class="sxs-lookup"><span data-stu-id="222dc-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="222dc-114">如需詳細資訊，請參閱 [Char 資料型別](../../../language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="222dc-114">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="222dc-115">字串類型</span><span class="sxs-lookup"><span data-stu-id="222dc-115">String Type</span></span>  

 <span data-ttu-id="222dc-116">`String`資料類型是零或多個雙位元組 (16 位) Unicode 字元的序列。</span><span class="sxs-lookup"><span data-stu-id="222dc-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="222dc-117">如果變數可以包含不限數量的字元，請將它宣告為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="222dc-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="222dc-118">例如：</span><span class="sxs-lookup"><span data-stu-id="222dc-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="222dc-119">如需詳細資訊，請參閱 [字串資料類型](../../../language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="222dc-119">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222dc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="222dc-120">See also</span></span>

- [<span data-ttu-id="222dc-121">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="222dc-121">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="222dc-122">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="222dc-122">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="222dc-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="222dc-123">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="222dc-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="222dc-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="222dc-125">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="222dc-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="222dc-126">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="222dc-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="222dc-127">類型字元</span><span class="sxs-lookup"><span data-stu-id="222dc-127">Type Characters</span></span>](type-characters.md)
