---
title: "如何：在 Visual Basic 中將位元組陣列轉換為字串"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4133109ef334c7e87884deb7db963db3291da1d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="83fd8-102">如何：在 Visual Basic 中將位元組陣列轉換為字串</span><span class="sxs-lookup"><span data-stu-id="83fd8-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="83fd8-103">本主題說明如何將位元組從位元組陣列轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="83fd8-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83fd8-104">範例</span><span class="sxs-lookup"><span data-stu-id="83fd8-104">Example</span></span>  
 <span data-ttu-id="83fd8-105">這個範例會使用<xref:System.Text.Encoding.GetString%2A>方法<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼類別，以位元組陣列中的所有位元組都轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="83fd8-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 <span data-ttu-id="83fd8-106">您可以從數個位元組陣列轉換為字串的編碼選項進行選擇：</span><span class="sxs-lookup"><span data-stu-id="83fd8-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="83fd8-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>： 取得 ASCII （7 位元） 字元的編碼方式設定。</span><span class="sxs-lookup"><span data-stu-id="83fd8-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="83fd8-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>： 取得使用位元組由大到小的位元組順序的 utf-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83fd8-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="83fd8-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>： 取得系統目前的 ANSI 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83fd8-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="83fd8-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>： 取得位元組由小到大位元組順序的 utf-16 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83fd8-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="83fd8-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>： 取得使用位元組由小到大順序 utf-32 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83fd8-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="83fd8-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>： 取得 utf-7 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83fd8-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="83fd8-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>： 取得 utf-8 格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83fd8-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83fd8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83fd8-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [<span data-ttu-id="83fd8-115">如何： 將字串轉換成 Visual Basic 中的位元組陣列</span><span class="sxs-lookup"><span data-stu-id="83fd8-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
