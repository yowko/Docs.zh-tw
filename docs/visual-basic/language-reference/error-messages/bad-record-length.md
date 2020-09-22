---
title: 不正確的資料錄長度
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 6967015572b2567f52697f7ddcb1ff594013a2c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869255"
---
# <a name="bad-record-length"></a>不正確的資料錄長度

可能導致本錯誤的原因包括：  
  
- 、或語句中指定的記錄變數長度 `FileGet` ， `FileGetObject` `FilePut` `FilePutObject` 與對應的語句中所指定的長度不同 `FileOpen` 。  
  
- 或語句中的 `FilePut` 變數 `FilePutObject` 為或包含可變長度的字串。  
  
- 或中的變數 `FilePut` `FilePutObject` 為或包含 `Variant` 類型。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定定義記錄變數型別的使用者定義型別中的固定長度變數大小總和，與語句子句中所述的值相同 `FileOpen` `Len` 。  
  
2. 如果或語句中的 `FilePut` 變數 `FilePutObject` 為或包含可變長度的字串，請確定變數長度字串至少為2個字元，且小於語句的子句中指定的記錄長度 `Len` `FileOpen` 。  
  
3. 如果或中的變數 `FilePut` `FilePutObject` 為或包含， `Variant` 請確定可變長度字串的長度至少為4個位元組，且小於語句的子句中指定的記錄長度 `Len` `FileOpen` 。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
