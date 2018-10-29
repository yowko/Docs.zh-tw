---
title: 必須有陳述式結尾
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 8df756009ebe3a0613ec47018d938151829214df
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198259"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="f6c18-102">必須有陳述式結尾</span><span class="sxs-lookup"><span data-stu-id="f6c18-102">End of statement expected</span></span>
<span data-ttu-id="f6c18-103">陳述式語法上完成，但其他程式設計項目會遵循完成陳述式的項目。</span><span class="sxs-lookup"><span data-stu-id="f6c18-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="f6c18-104">需要在每個陳述式結尾的行結束字元。</span><span class="sxs-lookup"><span data-stu-id="f6c18-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="f6c18-105">行結束字元會分成幾行中的 Visual Basic 原始程式檔中的字元。</span><span class="sxs-lookup"><span data-stu-id="f6c18-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="f6c18-106">範例的行結束字元是 Unicode 歸位字元傳回字元 （HD），Unicode 換行字元 （& HA），和 Unicode 歸位字元後面接著 Unicode 換行字元。</span><span class="sxs-lookup"><span data-stu-id="f6c18-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="f6c18-107">如需行結束字元的詳細資訊，請參閱[Visual Basic 語言規格](~/_vblang/spec/lexical-grammar.md#line-terminators)。</span><span class="sxs-lookup"><span data-stu-id="f6c18-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="f6c18-108">**錯誤 ID:** BC30205</span><span class="sxs-lookup"><span data-stu-id="f6c18-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6c18-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f6c18-109">To correct this error</span></span>
  
1.  <span data-ttu-id="f6c18-110">檢查看看是否兩個不同的陳述式不小心存放在同一行。</span><span class="sxs-lookup"><span data-stu-id="f6c18-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="f6c18-111">完成陳述式的項目之後插入的行結束字元。</span><span class="sxs-lookup"><span data-stu-id="f6c18-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f6c18-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6c18-112">See Also</span></span>  
 [<span data-ttu-id="f6c18-113">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="f6c18-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="f6c18-114">陳述式</span><span class="sxs-lookup"><span data-stu-id="f6c18-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
