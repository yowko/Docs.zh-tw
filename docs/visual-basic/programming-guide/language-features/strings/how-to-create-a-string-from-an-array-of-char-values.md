---
title: 如何：使用字元值陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: bf37ceba901e712df10ad4b39f9ad74194843136
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346776"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="4ba82-102">如何：使用字元值陣列建立字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ba82-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="4ba82-103">這個範例會從個別字元建立字串 "abcd"。</span><span class="sxs-lookup"><span data-stu-id="4ba82-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ba82-104">範例</span><span class="sxs-lookup"><span data-stu-id="4ba82-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="4ba82-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4ba82-105">Compile the code</span></span>  
 <span data-ttu-id="4ba82-106">這個方法沒有特殊需求。</span><span class="sxs-lookup"><span data-stu-id="4ba82-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="4ba82-107">語法 `"a"c`，其中單一 `c` 遵循引號中的單一字元，用來建立字元常值。</span><span class="sxs-lookup"><span data-stu-id="4ba82-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4ba82-108">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="4ba82-108">Robust Programming</span></span>  
 <span data-ttu-id="4ba82-109">使用字串時，字串中的 Null 字元（相當於 `Chr(0)`）會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="4ba82-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="4ba82-110">Null 字元將會包含在字串中，但在某些情況下，將不會顯示 null 字元之後的字元。</span><span class="sxs-lookup"><span data-stu-id="4ba82-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba82-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ba82-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="4ba82-112">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="4ba82-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="4ba82-113">資料類型</span><span class="sxs-lookup"><span data-stu-id="4ba82-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
