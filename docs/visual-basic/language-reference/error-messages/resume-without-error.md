---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870834"
---
# <a name="resume-without-error"></a>無錯繼續

`Resume`語句出現在錯誤處理常式代碼之外，或即使沒有任何錯誤，程式碼也會跳到錯誤處理常式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請將 `Resume` 語句移至錯誤處理常式，或將其刪除。  
  
2. 跳至標籤不能跨程式進行，所以請在程式中搜尋識別錯誤處理常式的標籤。 如果您發現重複的標籤指定為 `GoTo` 不是語句之語句的目標 `On Error GoTo` ，請變更行標籤以同意其預定的目標。  
  
## <a name="see-also"></a>另請參閱

- [Resume 陳述式](../statements/resume-statement.md)
- [On Error 陳述式](../statements/on-error-statement.md)
