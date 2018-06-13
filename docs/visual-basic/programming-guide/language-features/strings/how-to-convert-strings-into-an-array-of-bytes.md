---
title: 如何：在 Visual Basic 中將字串轉換為位元組陣列
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: da4a47b955b91f4bb39ecd7832da30d76e75d553
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647949"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="a0c64-102">如何：在 Visual Basic 中將字串轉換為位元組陣列</span><span class="sxs-lookup"><span data-stu-id="a0c64-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="a0c64-103">本主題說明如何將字串轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="a0c64-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c64-104">範例</span><span class="sxs-lookup"><span data-stu-id="a0c64-104">Example</span></span>  
 <span data-ttu-id="a0c64-105">這個範例會使用<xref:System.Text.Encoding.GetBytes%2A>方法<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼類別，以將字串轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="a0c64-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 <span data-ttu-id="a0c64-106">您可以從數個將字串轉換成位元組陣列的編碼選項進行選擇：</span><span class="sxs-lookup"><span data-stu-id="a0c64-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="a0c64-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>： 取得 ASCII （7 位元） 字元的編碼方式設定。</span><span class="sxs-lookup"><span data-stu-id="a0c64-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="a0c64-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>： 取得使用位元組由大到小的位元組順序的 utf-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a0c64-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="a0c64-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>： 取得系統目前的 ANSI 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a0c64-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="a0c64-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>： 取得位元組由小到大位元組順序的 utf-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a0c64-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="a0c64-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>： 取得使用位元組由小到大順序 utf-32 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a0c64-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="a0c64-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>： 取得 utf-7 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a0c64-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="a0c64-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>： 取得 utf-8 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a0c64-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c64-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c64-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [<span data-ttu-id="a0c64-115">如何： 將位元組陣列轉換成 Visual Basic 中的字串</span><span class="sxs-lookup"><span data-stu-id="a0c64-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
