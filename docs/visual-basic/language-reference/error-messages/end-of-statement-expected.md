---
title: 必須有陳述式結尾
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a>必須有陳述式結尾
陳述式語法完成，但其他的程式設計項目項目完成陳述式後面。 需要在每個陳述式結尾行結束字元。
  
 行結束字元會分成幾行中的 Visual Basic 來源檔案中的字元。 行結束字元的範例包括 Unicode 歸位字元傳回字元 (& HD)、 Unicode 換行字元 (& HA) 和 Unicode 歸位字元後面接著 Unicode 換行字元。 如需行結束字元的詳細資訊，請參閱[Visual Basic 語言規格](../../../visual-basic/reference/language-specification/index.md)。
  
 **錯誤 ID:** BC30205
  
## <a name="to-correct-this-error"></a>更正這個錯誤
  
1.  檢查是否兩個不同的陳述式裡的同一行。
  
2.  完成陳述式的項目之後插入的行結束字元。
  
## <a name="see-also"></a>另請參閱  
 [操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
