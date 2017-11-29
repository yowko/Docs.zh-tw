---
title: "字元資料類型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1066444ba3a98f26fc2a35135a50b2954c6b992
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="7f3a4-102">字元資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f3a4-102">Character Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="7f3a4-103">提供*字元資料類型*處理可列印及可顯示的字元。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-103"> provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="7f3a4-104">雖然它們都使用 Unicode 字元處理`Char`保存單一字元，而`String`包含了不定數量的字元。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="7f3a4-105">顯示並行所比較資料表[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-105">For a table that displays a side-by-side comparison of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="7f3a4-106">Char 類型</span><span class="sxs-lookup"><span data-stu-id="7f3a4-106">Char Type</span></span>  
 <span data-ttu-id="7f3a4-107">`Char`資料類型是單一的兩個位元組 （16 位元） 的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="7f3a4-108">如果變數一律會儲存一個字元，將它宣告為`Char`。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="7f3a4-109">例如: </span><span class="sxs-lookup"><span data-stu-id="7f3a4-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 <span data-ttu-id="7f3a4-110">中的每個可能值`Char`或`String`變數是*程式碼點*，或在 Unicode 字元集的字元碼。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="7f3a4-111">Unicode 字元包括基本的 ASCII 字元集、 各種其他字母字元、 重音符號、 貨幣符號、 分數、 變音符號和數學和技術的符號。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f3a4-112">Unicode 字元集字碼元素 D800 到 DFFF (透過 55551 十進位 55296) 的保留*surrogate 字組*，而這需要兩個 16 位元值來表示單一字碼指標。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="7f3a4-113">A`Char`變數無法容納 surrogate 字組和`String`用來保留此類配對的兩個位置。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="7f3a4-114">如需詳細資訊，請參閱[Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="7f3a4-115">字串類型</span><span class="sxs-lookup"><span data-stu-id="7f3a4-115">String Type</span></span>  
 <span data-ttu-id="7f3a4-116">`String`資料型別是一串零或多個兩個位元組 （16 位元） 的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="7f3a4-117">如果變數可以包含任何數目的字元，將它宣告為`String`。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="7f3a4-118">例如: </span><span class="sxs-lookup"><span data-stu-id="7f3a4-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 <span data-ttu-id="7f3a4-119">如需詳細資訊，請參閱[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="7f3a4-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f3a4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f3a4-120">See Also</span></span>  
 [<span data-ttu-id="7f3a4-121">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="7f3a4-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="7f3a4-122">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="7f3a4-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="7f3a4-123">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="7f3a4-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="7f3a4-124">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="7f3a4-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="7f3a4-125">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="7f3a4-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="7f3a4-126">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="7f3a4-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="7f3a4-127">類型字元</span><span class="sxs-lookup"><span data-stu-id="7f3a4-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
