---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 5e45f713a433365b4bbc8286154a3b877b08ec59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resume-without-error"></a>無錯繼續
A`Resume`陳述式出現在錯誤處理程式碼中，外部或程式碼已跳入錯誤處理常式，即使沒有錯誤。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移動`Resume`陳述式 into 錯誤處理常式，或將它刪除。  
  
2.  跳至標籤不會發生跨程序，因此搜尋的程序識別的錯誤處理常式的標籤。 如果您發現重複的標籤，指定為目標的`GoTo`陳述式不`On Error GoTo`陳述式中，變更線條標籤，以符合所要的目標。  
  
## <a name="see-also"></a>另請參閱  
 [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
