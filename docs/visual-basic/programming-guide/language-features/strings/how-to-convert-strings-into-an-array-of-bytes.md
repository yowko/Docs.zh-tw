---
title: 如何：將字串轉換為位元組陣列
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 3ee1d5e1e31054f23f4510c7a112d8e3473bcdd7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410602"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為位元組陣列
本主題說明如何將字串轉換為位元組陣列。  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Text.Encoding.GetBytes%2A> <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding 類別的方法，將字串轉換為位元組陣列。  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 您可以從數種編碼選項中進行選擇，將字串轉換為位元組陣列：  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>：取得 ASCII （7位）字元集的編碼方式。  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>：使用位元組由大到小的順序，取得 UTF-16 格式的編碼方式。  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>：取得系統目前 ANSI 字碼頁的編碼方式。  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>：取得 UTF-16 格式的編碼方式，使用位元組由小到大的順序。  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>：使用以位元組由小到大的順序，取得 UTF-32 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>：取得 UTF-7 格式的編碼方式。  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>：取得 UTF-8 格式的編碼方式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [如何：在 Visual Basic 中將位元組陣列轉換為字串](how-to-convert-an-array-of-bytes-into-a-string.md)
