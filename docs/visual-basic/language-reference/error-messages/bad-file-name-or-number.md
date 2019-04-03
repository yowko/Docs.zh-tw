---
title: 不正確的檔名或數目
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: b6da1031b60a4cd73c53588cf18992797c3fddab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839063"
---
# <a name="bad-file-name-or-number"></a>不正確的檔名或數目
嘗試存取指定的檔案時發生錯誤。 此錯誤的可能原因包括：  
  
-   陳述式所參考的檔案中未指定檔案名稱或數字`FileOpen`中指定陳述式或`FileOpen`陳述式，但卻是之後關閉。  
  
-   陳述式所參考的檔案，以超出範圍的檔案數字的數字。  
  
-   陳述式參考的檔案名稱或不是有效的數字。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定檔案名稱已在指定`FileOpen`陳述式。 請注意，如果您叫用`FileClose`陳述式不含引數，您可能不小心關閉所有開啟的檔案。  
  
2.  如果您的程式碼以演算法產生的檔案數字，確定數字都有效。  
  
3.  請檢查檔案名稱，以確保它們符合作業系統的慣例。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
