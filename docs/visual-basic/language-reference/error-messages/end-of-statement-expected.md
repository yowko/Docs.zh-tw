---
title: 必須有陳述式結尾
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 9141400afc651629df381e0a655e2d7b9da2e45d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874414"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="b20fc-102">必須有陳述式結尾</span><span class="sxs-lookup"><span data-stu-id="b20fc-102">End of statement expected</span></span>

<span data-ttu-id="b20fc-103">語句的語法已完成，但其他程式設計專案會在完成語句的元素之後。</span><span class="sxs-lookup"><span data-stu-id="b20fc-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="b20fc-104">在每個語句的結尾都需要行結束字元。</span><span class="sxs-lookup"><span data-stu-id="b20fc-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="b20fc-105">行結束字元會將 Visual Basic 原始程式檔的字元分成幾行。</span><span class="sxs-lookup"><span data-stu-id="b20fc-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="b20fc-106">行結束字元的範例有 Unicode 換行字元 ( # B0 HD) 、Unicode 換行字元 ( # B1 HA) ，以及 unicode 換行字元（後面接著 Unicode 換行字元）。</span><span class="sxs-lookup"><span data-stu-id="b20fc-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="b20fc-107">如需行結束字元的詳細資訊，請參閱 [Visual Basic 語言規格](~/_vblang/spec/lexical-grammar.md#line-terminators)。</span><span class="sxs-lookup"><span data-stu-id="b20fc-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="b20fc-108">**錯誤識別碼：** BC30205</span><span class="sxs-lookup"><span data-stu-id="b20fc-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b20fc-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b20fc-109">To correct this error</span></span>
  
1. <span data-ttu-id="b20fc-110">檢查是否有兩個不同的語句不小心放在同一行上。</span><span class="sxs-lookup"><span data-stu-id="b20fc-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2. <span data-ttu-id="b20fc-111">在完成語句的元素之後插入行結束字元。</span><span class="sxs-lookup"><span data-stu-id="b20fc-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b20fc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b20fc-112">See also</span></span>

- [<span data-ttu-id="b20fc-113">作法：程式碼中的 Break 及 Combine 陳述式</span><span class="sxs-lookup"><span data-stu-id="b20fc-113">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="b20fc-114">陳述式</span><span class="sxs-lookup"><span data-stu-id="b20fc-114">Statements</span></span>](../../programming-guide/language-features/statements.md)
