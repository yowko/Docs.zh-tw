---
title: HOW TO：將位元組陣列轉換成 Visual Basic 中的字串
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 577cce6322bf80bf2abdb963f07938b1a8b5d174
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718347"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="abc9b-102">HOW TO：將位元組陣列轉換成 Visual Basic 中的字串</span><span class="sxs-lookup"><span data-stu-id="abc9b-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="abc9b-103">本主題說明如何從位元組陣列的位元組轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="abc9b-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abc9b-104">範例</span><span class="sxs-lookup"><span data-stu-id="abc9b-104">Example</span></span>  
 <span data-ttu-id="abc9b-105">這個範例會使用<xref:System.Text.Encoding.GetString%2A>方法的<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼類別，以從位元組陣列的所有位元組都轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="abc9b-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 <span data-ttu-id="abc9b-106">您可以選擇數個編碼的選項，以位元組陣列轉換為字串：</span><span class="sxs-lookup"><span data-stu-id="abc9b-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="abc9b-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：取得 ASCII (7 位元) 字元集 (Character Set) 的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="abc9b-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：取得位元組由大到小位元組順序，使用 utf-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="abc9b-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：取得系統的目前的 ANSI 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="abc9b-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：取得位元組由小到大的順序，使用 utf-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="abc9b-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：取得位元組由小到大的順序，使用 UTF-32 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="abc9b-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：取得 UTF-7 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="abc9b-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：取得 UTF-8 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="abc9b-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc9b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc9b-114">See also</span></span>
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="abc9b-115">如何：將字串轉換成 Visual Basic 中的位元組陣列</span><span class="sxs-lookup"><span data-stu-id="abc9b-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
