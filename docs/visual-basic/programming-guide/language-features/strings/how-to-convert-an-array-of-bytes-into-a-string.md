---
title: 如何：將位元組陣列轉換成字串
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 8c1d9d1d2e89390873bc1c3dbb9623f047433a9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351982"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>如何：在 Visual Basic 中將位元組陣列轉換為字串
本主題說明如何將位元組陣列中的位元組轉換成字串。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> 編碼類別的 <xref:System.Text.Encoding.GetString%2A> 方法，將位元組陣列中的所有位元組轉換成字串。  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 您可以從數種編碼選項中進行選擇，將位元組陣列轉換成字串：  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：取得 ASCII （7位）字元集的編碼方式。  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：使用位元組由大到小的順序，取得 UTF-16 格式的編碼方式。  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：取得系統目前 ANSI 字碼頁的編碼方式。  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：使用以位元組由小到大的順序，取得 UTF-16 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：使用以位元組由小到大的順序，取得 UTF-32 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：取得 UTF-7 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：取得 UTF-8 格式的編碼方式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [如何：在 Visual Basic 中將字串轉換為位元組陣列](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
