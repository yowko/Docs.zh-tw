---
title: 不正確的檔名或數目
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585563"
---
# <a name="bad-file-name-or-number"></a>不正確的檔名或數目
嘗試存取指定的檔案時發生錯誤。 此錯誤的可能原因包括：  
  
-   陳述式中未指定檔名或數目與檔案參考`FileOpen`或陳述式中指定`FileOpen`陳述式，但卻是之後關閉。  
  
-   陳述式所參考的檔案與超出範圍的檔案數字的數字。  
  
-   陳述式參考的檔案名稱或不是有效的數字。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認檔案名稱指定在`FileOpen`陳述式。 請注意，如果您叫用`FileClose`陳述式沒有引數，您可能會不小心關閉所有開啟的檔案。  
  
2.  如果您的程式碼會利用演算法產生檔案數目，請確定使用數字。  
  
3.  請檢查檔案名稱，以確保它們符合作業系統慣例。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
