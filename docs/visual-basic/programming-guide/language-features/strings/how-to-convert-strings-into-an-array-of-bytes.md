---
title: "如何：在 Visual Basic 中將字串轉換為位元組陣列"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6d527434dc0a61c9c771b42d05c1ee316094e7fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為位元組陣列
本主題說明如何將字串轉換成位元組陣列。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Text.Encoding.GetBytes%2A>方法<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>編碼類別，以將字串轉換成位元組陣列。  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 您可以從數個將字串轉換成位元組陣列的編碼選項進行選擇：  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>： 取得 ASCII （7 位元） 字元的編碼方式設定。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>： 取得使用位元組由大到小的位元組順序的 utf-16 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>： 取得系統目前的 ANSI 字碼頁的編碼方式。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>： 取得位元組由小到大位元組順序的 utf-16 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>： 取得使用位元組由小到大順序 utf-32 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>： 取得 utf-7 格式的編碼方式。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>： 取得 utf-8 格式的編碼方式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [如何： 將位元組陣列轉換成 Visual Basic 中的字串](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
