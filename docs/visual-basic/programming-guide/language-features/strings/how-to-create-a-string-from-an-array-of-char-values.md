---
title: 如何：使用字元值陣列建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071153"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="68d43-102">如何：使用字元值陣列建立字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68d43-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="68d43-103">此範例會從個別字元建立 "abcd" 字串。</span><span class="sxs-lookup"><span data-stu-id="68d43-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68d43-104">範例</span><span class="sxs-lookup"><span data-stu-id="68d43-104">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="68d43-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="68d43-105">Compile the code</span></span>  

 <span data-ttu-id="68d43-106">這個方法沒有特殊需求。</span><span class="sxs-lookup"><span data-stu-id="68d43-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="68d43-107">語法 `"a"c` （單一 `c` 字元後面接著單引號）是用來建立字元常值。</span><span class="sxs-lookup"><span data-stu-id="68d43-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="68d43-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="68d43-108">Robust Programming</span></span>  

 <span data-ttu-id="68d43-109">使用字串時，Null 字元 (相當於 `Chr(0)` 字串中的) 會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="68d43-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="68d43-110">字串中會包含 null 字元，但在某些情況下，將不會顯示在 null 字元之後的字元。</span><span class="sxs-lookup"><span data-stu-id="68d43-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d43-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68d43-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="68d43-112">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="68d43-112">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="68d43-113">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="68d43-113">Data Types</span></span>](../data-types/index.md)
