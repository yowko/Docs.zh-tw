---
title: 如何：在 Visual Basic 中將位元組陣列轉換為字串
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: c22ae89322230d8a98ae3ae2c1485e73456e0a7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>如何：在 Visual Basic 中將位元組陣列轉換為字串
本主題說明如何將位元組從位元組陣列轉換成字串。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Text.Encoding.GetString%2A>方法<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼類別，以位元組陣列中的所有位元組都轉換為字串。  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 您可以從數個位元組陣列轉換為字串的編碼選項進行選擇：  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>： 取得 ASCII （7 位元） 字元的編碼方式設定。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>： 取得使用位元組由大到小的位元組順序的 utf-16 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>： 取得系統目前的 ANSI 字碼頁的編碼方式。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>： 取得位元組由小到大位元組順序的 utf-16 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>： 取得使用位元組由小到大順序 utf-32 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>： 取得 utf-7 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>： 取得 utf-8 格式的編碼方式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [如何： 將字串轉換成 Visual Basic 中的位元組陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
