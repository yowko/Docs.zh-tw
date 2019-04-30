---
title: HOW TO：將位元組陣列轉換成 Visual Basic 中的字串
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: f0676548bea2d4037f66fb15498c175b2d110d8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024621"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>HOW TO：將位元組陣列轉換成 Visual Basic 中的字串
本主題說明如何從位元組陣列的位元組轉換為字串。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Text.Encoding.GetString%2A>方法的<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼類別，以從位元組陣列的所有位元組都轉換為字串。  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 您可以選擇數個編碼的選項，以位元組陣列轉換為字串：  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：取得 ASCII (7 位元) 字元集 (Character Set) 的編碼方式。  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：取得位元組由大到小位元組順序，使用 utf-16 格式的編碼方式。  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：取得系統的目前的 ANSI 字碼頁的編碼方式。  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：取得位元組由小到大的順序，使用 utf-16 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：取得位元組由小到大的順序，使用 UTF-32 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：取得 UTF-7 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：取得 UTF-8 格式的編碼方式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [如何：將字串轉換成 Visual Basic 中的位元組陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
