---
title: 無錯繼續
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400366"
---
# <a name="resume-without-error"></a>無錯繼續
`Resume`語句出現在錯誤處理常式代碼之外，或程式碼即使沒有錯誤也會跳入錯誤處理常式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請將 `Resume` 語句移至錯誤處理常式，或將它刪除。  
  
2. 跳到標籤不能在整個程式中發生，因此請搜尋程式中的標籤，找出錯誤處理常式。 如果您發現重複的標籤指定為 `GoTo` 不是語句的語句目標 `On Error GoTo` ，請將行標籤變更為同意其預期的目標。  
  
## <a name="see-also"></a>另請參閱

- [Resume 陳述式](../statements/resume-statement.md)
- [On Error 陳述式](../statements/on-error-statement.md)
