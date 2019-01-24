---
title: HOW TO：將字串轉換成 Visual Basic 中的位元組陣列
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 83efc9e6b4d4433d5416f2f8b2612c76581586e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648478"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>HOW TO：將字串轉換成 Visual Basic 中的位元組陣列
本主題說明如何將字串轉換成位元組陣列。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Text.Encoding.GetBytes%2A>方法的<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼將字串轉換成位元組陣列的類別。  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 您可以選擇數個編碼的選項，以將字串轉換成位元組陣列：  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：取得 ASCII (7 位元) 字元集 (Character Set) 的編碼方式。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：取得位元組由大到小位元組順序，使用 utf-16 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：取得系統的目前的 ANSI 字碼頁的編碼方式。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：取得位元組由小到大的順序，使用 utf-16 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：取得位元組由小到大的順序，使用 UTF-32 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：取得 UTF-7 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：取得 UTF-8 格式的編碼方式。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [如何：將位元組陣列轉換成 Visual Basic 中的字串](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
