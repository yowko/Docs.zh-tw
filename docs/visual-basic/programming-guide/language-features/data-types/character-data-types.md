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
ms.openlocfilehash: 33dd4c62776ae8c5ec0ce0a6d0858a7ed0d047fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401988"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="334cd-102">字元資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="334cd-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="334cd-103">Visual Basic 提供*字元資料類型*，以處理可列印和可顯示的字元。</span><span class="sxs-lookup"><span data-stu-id="334cd-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="334cd-104">雖然兩者都處理 Unicode 字元，但會 `Char` 保留單一字元，而 `String` 包含不限數目的字元。</span><span class="sxs-lookup"><span data-stu-id="334cd-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="334cd-105">如需顯示 Visual Basic 資料類型並存比較的資料表，請參閱[資料類型](../../../language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="334cd-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="334cd-106">Char 類型</span><span class="sxs-lookup"><span data-stu-id="334cd-106">Char Type</span></span>  
 <span data-ttu-id="334cd-107">`Char`資料類型是單一的雙位元組（16位） Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="334cd-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="334cd-108">如果變數一律只儲存一個字元，請將它宣告為 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="334cd-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="334cd-109">例如：</span><span class="sxs-lookup"><span data-stu-id="334cd-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="334cd-110">或變數中的每個可能值 `Char` `String` 都是 Unicode 字元集中的程式*代碼點*或字元碼。</span><span class="sxs-lookup"><span data-stu-id="334cd-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="334cd-111">Unicode 字元包括基本 ASCII 字元集、其他各種字母字母、重音、貨幣符號、分數、變音符號和數學和技術符號。</span><span class="sxs-lookup"><span data-stu-id="334cd-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="334cd-112">Unicode 字元集會針對*代理配對*保留 D800 到 DFFF （55296到 55551 decimal）的程式碼點，其需要 2 16 位值來表示單一程式碼點。</span><span class="sxs-lookup"><span data-stu-id="334cd-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="334cd-113">`Char`變數不能保存代理配對，而且會 `String` 使用兩個位置來保存這種配對。</span><span class="sxs-lookup"><span data-stu-id="334cd-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="334cd-114">如需詳細資訊，請參閱[Char Data Type](../../../language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="334cd-114">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="334cd-115">字串類型</span><span class="sxs-lookup"><span data-stu-id="334cd-115">String Type</span></span>  
 <span data-ttu-id="334cd-116">`String`資料類型是零個或多個兩個位元組（16位） Unicode 字元的序列。</span><span class="sxs-lookup"><span data-stu-id="334cd-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="334cd-117">如果變數可以包含不限數量的字元，請將它宣告為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="334cd-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="334cd-118">例如：</span><span class="sxs-lookup"><span data-stu-id="334cd-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="334cd-119">如需詳細資訊，請參閱[String Data Type](../../../language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="334cd-119">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334cd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="334cd-120">See also</span></span>

- [<span data-ttu-id="334cd-121">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="334cd-121">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="334cd-122">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="334cd-122">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="334cd-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="334cd-123">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="334cd-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="334cd-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="334cd-125">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="334cd-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="334cd-126">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="334cd-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="334cd-127">類型字元</span><span class="sxs-lookup"><span data-stu-id="334cd-127">Type Characters</span></span>](type-characters.md)
