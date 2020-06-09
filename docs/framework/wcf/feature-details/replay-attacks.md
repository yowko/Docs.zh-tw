---
title: 重新執行攻擊
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 47a4726859605415b4e3e1b4d523f2f8059a3989
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586295"
---
# <a name="replay-attacks"></a>重新執行攻擊
當攻擊者複製兩方之間的訊息資料流程，並將資料流程重新執行至一或多個合作物件時，就會發生重新執行*攻擊*。 除非緩解攻擊，否則受到攻擊的電腦會將資料流當成合法訊息來處理，導致發生一連串負面的影響，例如項目的重複排序。  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>繫結可能受制於反映攻擊  
 *反映攻擊*會將訊息重新執行回傳送者，就好像它們是來自接收者做為回復一樣。 Windows Communication Foundation （WCF）機制中的標準重新執行*偵測*不會自動處理這種情況。  
  
 預設會緩和反映攻擊，因為 WCF 服務模型會新增帶正負號的訊息識別碼來要求訊息，並預期回應訊息中會有已簽署的 `relates-to` 標頭。 如此一來，要求訊息便無法當成回應來重新執行。 在安全訊息 (RM) 案例中，反映攻擊的緩解原因為：  
  
- 建立順序與建立順序回應訊息結構描述是不一樣的。  
  
- 在 Simplex 順序中，用戶端所傳送的順序訊息無法返回重新執行，因為用戶端無法理解此類訊息。  
  
- 在雙工順序中，兩個順序識別碼必須是唯一的。 因此，傳出的順序訊息無法返回當成傳入順序訊息來重新執行 (所有的順序標頭與本文都會一併簽署)。  
  
 唯一會受到反映攻擊影響的繫結就是不含 WS-Addressing 的繫結：已經停用 WS-Addressing 並使用對稱式金鑰安全性的自訂繫結。 <xref:System.ServiceModel.BasicHttpBinding> 依預設不會使用 WS-Addressing，但是它在使用對稱式金鑰安全性時，不會讓本身受到此攻擊的影響。  
  
 自訂繫結的緩解作業不是要建立安全性內容或是要求 WS-Addressing 標頭。  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web 伺服陣列：攻擊者對多個節點重新執行要求  
 用戶端會使用已在 Web 伺服陣列上實作的服務。 攻擊者會針對伺服陣列中另一個節點重新執行已經傳送至某個伺服陣列節點的要求。 此外，如果服務重新啟動，則會清除重新執行快取，讓攻擊者重新執行要求 (快取中包含已使用、先前看到的訊息簽章值並避免重新執行，以讓簽章只能使用一次。 Web 伺服陣列不會共用重新執行快取)。  
  
 風險降低的方式包括：  
  
- 使用訊息模式安全性搭配具狀態的安全性內容權杖 (包含或不包含啟用的安全對話)。 如需詳細資訊，請參閱[如何：為安全會話建立安全性內容權杖](how-to-create-a-security-context-token-for-a-secure-session.md)。  
  
- 設定服務使用傳輸層級安全性。  
  
## <a name="see-also"></a>請參閱

- [安全性考量](security-considerations-in-wcf.md)
- [資訊洩漏](information-disclosure.md)
- [權限提高](elevation-of-privilege.md)
- [拒絕服務](denial-of-service.md)
- [竄改](tampering.md)
- [不支援的案例](unsupported-scenarios.md)
