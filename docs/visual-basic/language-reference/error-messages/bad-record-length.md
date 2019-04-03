---
title: 不正確的資料錄長度
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: f3df7819da0afddd7f238f282d496136d89cb052
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833473"
---
# <a name="bad-record-length"></a>不正確的資料錄長度
可能導致本錯誤的原因包括：  
  
-   中指定的記錄變數的長度`FileGet`， `FileGetObject`，`FilePut`或是`FilePutObject`陳述式與對應中指定的長度不同`FileOpen`陳述式。  
  
-   中的變數`FilePut`或`FilePutObject`陳述式或包含可變長度字串。  
  
-   中的變數`FilePut`或是`FilePutObject`是或包含`Variant`型別。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定記錄變數的型別定義的使用者定義型別中的固定長度變數的大小的總和為相同值中所述`FileOpen`陳述式的`Len`子句。  
  
2.  如果中的變數`FilePut`或是`FilePutObject`陳述式或包含可變長度字串，請確定可變長度字串中指定的記錄長度少於至少 2 個字元`Len`子句`FileOpen`陳述式。  
  
3.  如果中的變數`FilePut`或是`FilePutObject`是或包含`Variant`確定可變長度的字串是至少 4 個位元組中指定的記錄長度少於`Len`子句`FileOpen`陳述式。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
