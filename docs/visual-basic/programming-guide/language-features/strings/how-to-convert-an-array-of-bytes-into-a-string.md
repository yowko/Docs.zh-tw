---
title: 如何：將位元組陣列轉換為字串
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 6dbbaafedeca4d2cea625a300d764f61bb575750
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410615"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="4c121-102">如何：在 Visual Basic 中將位元組陣列轉換為字串</span><span class="sxs-lookup"><span data-stu-id="4c121-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="4c121-103">本主題說明如何將位元組陣列中的位元組轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="4c121-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c121-104">範例</span><span class="sxs-lookup"><span data-stu-id="4c121-104">Example</span></span>  
 <span data-ttu-id="4c121-105">這個範例會使用 <xref:System.Text.Encoding.GetString%2A> <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding 類別的方法，將位元組陣列中的所有位元組轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="4c121-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="4c121-106">您可以從數種編碼選項中進行選擇，將位元組陣列轉換成字串：</span><span class="sxs-lookup"><span data-stu-id="4c121-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
- <span data-ttu-id="4c121-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：取得 ASCII （7位）字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4c121-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="4c121-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：使用位元組由大到小的順序，取得 UTF-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4c121-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="4c121-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：取得系統目前 ANSI 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4c121-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="4c121-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：取得 UTF-16 格式的編碼方式，使用位元組由小到大的順序。</span><span class="sxs-lookup"><span data-stu-id="4c121-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="4c121-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：使用以位元組由小到大的順序，取得 UTF-32 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4c121-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="4c121-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：取得 UTF-7 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4c121-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="4c121-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：取得 UTF-8 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4c121-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c121-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c121-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="4c121-115">如何：在 Visual Basic 中將字串轉換為位元組陣列</span><span class="sxs-lookup"><span data-stu-id="4c121-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](how-to-convert-strings-into-an-array-of-bytes.md)
