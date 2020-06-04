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
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404157"
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
 結束 `SyncLock` 區塊。  
  
## <a name="remarks"></a>備註  
 `SyncLock`語句可確保多個執行緒不會同時執行語句區塊。 `SyncLock`防止每個執行緒進入區塊，直到沒有其他執行緒正在執行它為止。  
  
 最常見的用法 `SyncLock` 是保護資料，使其不會同時由一個以上的執行緒更新。 如果運算元據的語句必須在不中斷的情況下進入完成，請將它們放在 `SyncLock` 區塊內。  
  
 獨佔鎖定所保護的語句區塊有時稱為*重要區段*。  
  
## <a name="rules"></a>規則  
  
- 分支. 您無法 `SyncLock` 從區塊外部分支到區塊。  
  
- 鎖定物件值。 的值 `lockobject` 不能是 `Nothing` 。 您必須先建立鎖定物件，然後才能在語句中使用它 `SyncLock` 。  
  
     在執行區塊時，您無法變更的值 `lockobject` `SyncLock` 。 此機制會要求鎖定物件保持不變。  
  
- 您無法在區塊中使用[Await](../operators/await-operator.md)運算子 `SyncLock` 。  
  
## <a name="behavior"></a>行為  
  
- 機構. 當執行緒到達語句時 `SyncLock` ，它會評估 `lockobject` 運算式並暫停執行，直到它取得運算式所傳回之物件的獨佔鎖定為止。 當另一個執行緒到達 `SyncLock` 語句時，它不會取得鎖定，直到第一個執行緒執行 `End SyncLock` 語句為止。  
  
- 受保護的資料。 如果 `lockobject` 是 `Shared` 變數，獨佔鎖定會防止類別的任何實例中的執行緒在 `SyncLock` 執行任何其他執行緒時執行區塊。 這會保護所有實例之間共用的資料。  
  
     如果 `lockobject` 是執行個體變數（而非 `Shared` ），鎖定會防止在目前實例中執行的執行緒，與 `SyncLock` 相同實例中的另一個執行緒同時執行區塊。 這會保護個別實例維護的資料。  
  
- 取得與發行。 `SyncLock`區塊的行為就像是 `Try...Finally` 區塊取得獨佔鎖定的結構 `Try` `lockobject` ，而 `Finally` 區塊則會釋放它。 因此，不論 `SyncLock` 您離開區塊的方式為何，區塊都會保證鎖定的版本。 即使是未處理的例外狀況，也是如此。  
  
- 架構呼叫。 `SyncLock`區塊會 `Enter` `Exit` `Monitor` 在命名空間中呼叫類別的和方法，以取得和釋放獨佔鎖定 <xref:System.Threading> 。  
  
## <a name="programming-practices"></a>程式設計實務  
 `lockobject`運算式應一律評估為僅屬於您的類別的物件。 您應該宣告 `Private` 物件變數來保護屬於目前實例的資料，或使用 `Private Shared` 物件變數來保護所有實例的通用資料。  
  
 您不應該使用 `Me` 關鍵字來提供實例資料的鎖定物件。 如果您類別的外部程式碼具有類別實例的參考，它可以使用該參考當做區塊的鎖定物件， `SyncLock` 完全不同于您的，以保護不同的資料。 如此一來，您的類別和另一個類別可能會彼此封鎖，使其無法執行其不相關的 `SyncLock` 區塊。 同樣地，鎖定字串可能會造成問題，因為使用相同字串之進程中的任何其他程式碼將會共用相同的鎖定。  
  
 您也不應該使用 `Me.GetType` 方法來提供共用資料的鎖定物件。 這是因為 `GetType` 一律會 `Type` 針對指定的類別名稱傳回相同的物件。 外部程式碼可以 `GetType` 在您的類別上呼叫，並取得您所使用的相同鎖定物件。 這會導致兩個類別從其區塊彼此封鎖 `SyncLock` 。  
  
## <a name="examples"></a>範例  
  
### <a name="description"></a>描述  
 下列範例顯示維護簡單訊息清單的類別。 它會將訊息保留在陣列中，並將該陣列的最後一個使用中元素放在變數中。 程式會 `addAnotherMessage` 遞增最後一個元素，並儲存新的訊息。 這兩個作業會受到 `SyncLock` 和語句的保護 `End SyncLock` ，因為一旦最後一個專案遞增，就必須先儲存新的訊息，其他執行緒才能再次遞增最後一個元素。  
  
 如果 `simpleMessageList` 類別在其所有實例之間共用一個訊息清單，則變數 `messagesList` 和會宣告 `messagesLast` 為 `Shared` 。 在此情況下，變數 `messagesLock` 也應該是 `Shared` ，以便每個實例都使用單一鎖定物件。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>Description  
 下列範例會使用執行緒和 `SyncLock` 。 只要 `SyncLock` 語句存在，語句區塊就是關鍵區段，而且 `balance` 永遠不會成為負數。 您可以將 `SyncLock` 和語句標記 `End SyncLock` 為批註，以查看省略關鍵字的效果 `SyncLock` 。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>註解  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [同步處理原始物件概觀](../../../standard/threading/overview-of-synchronization-primitives.md)
