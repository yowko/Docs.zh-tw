---
title: HOW TO：從 Char 值 (Visual Basic) 的陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 0d3a4caf0967ab77de7d91470e43e52521dbd2da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975507"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="1e9ce-102">HOW TO：從 Char 值 (Visual Basic) 的陣列建立字串</span><span class="sxs-lookup"><span data-stu-id="1e9ce-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="1e9ce-103">此範例會建立從個別字元的字串"abcd"。</span><span class="sxs-lookup"><span data-stu-id="1e9ce-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e9ce-104">範例</span><span class="sxs-lookup"><span data-stu-id="1e9ce-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e9ce-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1e9ce-105">Compiling the Code</span></span>  
 <span data-ttu-id="1e9ce-106">這個方法沒有任何特殊的需求。</span><span class="sxs-lookup"><span data-stu-id="1e9ce-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="1e9ce-107">語法`"a"c`，其中單一`c`會遵循在引號內的單一字元，用來建立字元常值。</span><span class="sxs-lookup"><span data-stu-id="1e9ce-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1e9ce-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1e9ce-108">Robust Programming</span></span>  
 <span data-ttu-id="1e9ce-109">Null 字元 (等於`Chr(0)`) 字串中會導致非預期的結果時使用的字串。</span><span class="sxs-lookup"><span data-stu-id="1e9ce-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="1e9ce-110">Null 字元會包含字串，但在某些情況下不會顯示在 null 字元後面的字元。</span><span class="sxs-lookup"><span data-stu-id="1e9ce-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9ce-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9ce-111">See also</span></span>
- <xref:System.String>
- [<span data-ttu-id="1e9ce-112">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="1e9ce-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="1e9ce-113">資料類型</span><span class="sxs-lookup"><span data-stu-id="1e9ce-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
