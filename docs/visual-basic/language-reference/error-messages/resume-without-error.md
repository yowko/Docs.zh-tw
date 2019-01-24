---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 55295997e5e534b091063815d5ad1a37b81638ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686617"
---
# <a name="resume-without-error"></a>無錯繼續
A`Resume`陳述式出現在錯誤處理程式碼中，外部或程式碼已跳入錯誤處理常式，即使不發生任何錯誤。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移動`Resume`陳述式至錯誤處理常式，或將它刪除。  
  
2.  會跳至標籤不會發生跨程序，因此搜尋標籤可識別的錯誤處理常式的程序。 如果您發現重複的標籤為目標的指定`GoTo`陳述式不`On Error GoTo`陳述式中，變更線條標籤，以符合所要的目標。  
  
## <a name="see-also"></a>另請參閱
- [Resume 陳述式](../../../visual-basic/language-reference/statements/resume-statement.md)
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
