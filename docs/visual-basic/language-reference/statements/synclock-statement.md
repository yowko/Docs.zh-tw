---
title: SyncLock 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352810"
---
# <a name="synclock-statement"></a>SyncLock 陳述式
在執行區塊之前，取得語句區塊的獨佔鎖定。  
  
## <a name="syntax"></a>語法  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>組件  
 `lockobject`  
 必要。 評估為物件參考的運算式。  
  
 `block`  
 選擇性。 取得鎖定時要執行的語句區塊。  
  
 `End SyncLock`  
 終止 `SyncLock` 區塊。  
  
## <a name="remarks"></a>備註  
 `SyncLock` 語句可確保多個執行緒不會同時執行語句區塊。 `SyncLock` 可防止每個執行緒進入區塊，直到沒有其他執行緒正在執行它為止。  
  
 `SyncLock` 最常見的用法是保護資料，使其不會同時由一個以上的執行緒更新。 如果運算元據的語句必須在不中斷的情況下進入完成，請將它們放在 `SyncLock` 區塊內。  
  
 獨佔鎖定所保護的語句區塊有時稱為*重要區段*。  
  
## <a name="rules"></a>規則  
  
- 分支. 您無法從區塊外部分支到 `SyncLock` 區塊。  
  
- 鎖定物件值。 `lockobject` 的值無法 `Nothing`。 您必須先建立鎖定物件，才能在 `SyncLock` 語句中使用它。  
  
     執行 `SyncLock` 區塊時，您無法變更 `lockobject` 的值。 此機制會要求鎖定物件保持不變。  
  
- 您不能在 `SyncLock` 區塊中使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)運算子。  
  
## <a name="behavior"></a>行為  
  
- 機構. 當執行緒到達 `SyncLock` 語句時，它會評估 `lockobject` 運算式並暫停執行，直到它取得運算式所傳回之物件的獨佔鎖定為止。 當另一個執行緒到達 `SyncLock` 語句時，它就不會取得鎖定，直到第一個執行緒執行 `End SyncLock` 語句為止。  
  
- 受保護的資料。 如果 `lockobject` 是 `Shared` 變數，獨佔鎖定會防止在任何其他執行緒執行時，類別的任何實例中的執行緒執行 `SyncLock` 區塊。 這會保護所有實例之間共用的資料。  
  
     如果 `lockobject` 是執行個體變數（而非 `Shared`），鎖定會防止在目前實例中執行的執行緒，與相同實例中的另一個執行緒同時執行 `SyncLock` 區塊。 這會保護個別實例維護的資料。  
  
- 取得與發行。 `SyncLock` 區塊的行為就像是 `Try...Finally` 結構，`Try` 區塊會在 `lockobject` 上取得獨佔鎖定，而 `Finally` 區塊則會釋放它。 因此，不論您結束區塊的方式為何，`SyncLock` 區塊都會保證鎖定的版本。 即使是未處理的例外狀況，也是如此。  
  
- 架構呼叫。 `SyncLock` 區塊會藉由呼叫 <xref:System.Threading> 命名空間中 `Monitor` 類別的 `Enter` 和 `Exit` 方法，來取得和釋放獨佔鎖定。  
  
## <a name="programming-practices"></a>程式設計實務  
 `lockobject` 運算式應一律評估為僅屬於您類別的物件。 您應該宣告 `Private` 物件變數來保護屬於目前實例的資料，或 `Private Shared` 物件變數來保護所有實例的通用資料。  
  
 您不應該使用 `Me` 關鍵字來提供實例資料的鎖定物件。 如果您類別的外部程式碼具有類別實例的參考，它可以使用該參考做為 `SyncLock` 區塊與您完全不同的鎖定物件，以保護不同的資料。 如此一來，您的類別和其他類別可能會彼此封鎖，使其無法執行其不相關的 `SyncLock` 區塊。 同樣地，鎖定字串可能會造成問題，因為使用相同字串之進程中的任何其他程式碼將會共用相同的鎖定。  
  
 您也不應該使用 `Me.GetType` 方法來提供共用資料的鎖定物件。 這是因為 `GetType` 一律會針對指定的類別名稱傳回相同的 `Type` 物件。 外部程式碼可以在您的類別上呼叫 `GetType`，並取得您所使用的相同鎖定物件。 這會導致兩個類別從其 `SyncLock` 區塊彼此封鎖。  
  
## <a name="examples"></a>範例  
  
### <a name="description"></a>描述  
 下列範例顯示維護簡單訊息清單的類別。 它會將訊息保留在陣列中，並將該陣列的最後一個使用中元素放在變數中。 `addAnotherMessage` 程式會遞增最後一個元素，並儲存新的訊息。 這兩個作業會受到 `SyncLock` 和 `End SyncLock` 語句的保護，因為一旦最後一個專案已遞增，就必須先儲存新的訊息，其他執行緒才能再次遞增最後一個元素。  
  
 如果 `simpleMessageList` 類別在其所有實例之間共用一個訊息清單，`messagesList` 和 `messagesLast` 的變數會宣告為 `Shared`。 在此情況下，`messagesLock` 變數也應該 `Shared`，以便每個實例都使用單一鎖定物件。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>描述  
 下列範例會使用執行緒和 `SyncLock`。 只要有 `SyncLock` 語句，語句區塊就是關鍵區段，`balance` 絕對不會成為負數。 您可以將 `SyncLock` 和 `End SyncLock` 語句標記為批註，以查看離開 `SyncLock` 關鍵字的效果。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>註解  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [同步處理原始物件概觀](../../../standard/threading/overview-of-synchronization-primitives.md)
