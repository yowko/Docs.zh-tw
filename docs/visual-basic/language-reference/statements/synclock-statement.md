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
ms.openlocfilehash: cf2aad9ec2ba67200d175fbcddfcb49afeac6efc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604974"
---
# <a name="synclock-statement"></a>SyncLock 陳述式
取得陳述式區塊的獨佔鎖定之前執行的區塊。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>組件  
 `lockobject`  
 必要。 評估為物件參考的運算式。  
  
 `block`  
 選擇性。 屬於已取得鎖定時要執行的陳述式區塊。  
  
 `End SyncLock`  
 終止`SyncLock`區塊。  
  
## <a name="remarks"></a>備註  
 `SyncLock`陳述式可確保多個執行緒不會在同時執行的陳述式區塊。 `SyncLock` 每個執行緒可防止輸入區塊，直到沒有其他執行緒正在執行它。  
  
 最常見的用法`SyncLock`是為了防止資料由多個執行緒同時更新。 如果操作資料的陳述式必須移至不受干擾完成，請將它們放在`SyncLock`區塊。  
  
 有時稱為陳述式區塊的獨佔鎖定所保護*關鍵區段*。  
  
## <a name="rules"></a>規則  
  
-   分支。 您無法分支到`SyncLock`封鎖到區塊之外。  
  
-   鎖定物件的值。 值`lockobject`不可`Nothing`。 您必須建立之鎖定物件，再使用它在`SyncLock`陳述式。  
  
     您無法變更的值`lockobject`執行時`SyncLock`區塊。 這個機制需要之鎖定物件維持不變。  
  
-   您無法使用[Await](../../../visual-basic/language-reference/operators/await-operator.md)中的運算子`SyncLock`區塊。  
  
## <a name="behavior"></a>行為  
  
-   機制。 當執行緒到達`SyncLock`陳述式，它會評估`lockobject`運算式並暫止執行，直到它取得運算式所傳回的物件上的獨佔鎖定。 當另一個執行緒到達`SyncLock`陳述式，它不會取得鎖定的第一個執行緒執行直到`End SyncLock`陳述式。  
  
-   受保護的資料。 如果`lockobject`是`Shared`變數的獨佔鎖定可防止任何類別執行個體中的執行緒執行`SyncLock`封鎖其他任何執行緒執行它時。 如此可保護的所有執行個體之間共用的資料。  
  
     如果`lockobject`是執行個體變數 (不`Shared`)，鎖定可預防執行目前的執行個體中執行的執行緒`SyncLock`封鎖在相同的執行個體中的另一個執行緒在同時間。 如此可保護的個別執行個體所保留的資料。  
  
-   取得和釋放。 A`SyncLock`區塊的行為類似`Try...Finally`所在建構`Try`區塊上取得的獨佔鎖定`lockobject`和`Finally`區塊釋放它。 因為這個緣故，`SyncLock`區塊保證會釋放鎖定，不論您如何結束區塊。 這是即使有未處理的例外狀況，則為 true。  
  
-   架構會呼叫。 `SyncLock`區塊會取得和釋放獨佔鎖定，藉由呼叫`Enter`和`Exit`方法`Monitor`類別<xref:System.Threading>命名空間。  
  
## <a name="programming-practices"></a>程式設計做法  
 `lockobject`運算式應該一律等於專屬於您的類別的物件。 您應該宣告`Private`物件變數，以保護資料屬於目前的執行個體，或`Private Shared`物件變數，以保護資料通用於所有執行個體。  
  
 您不應該使用`Me`關鍵字來提供鎖定物件執行個體資料。 如果您的類別之外的程式碼類別的執行個體的參考，它可以使用該參考的鎖定物件為`SyncLock`區塊完全不同於您，保護不同的資料。 如此一來，您的類別和其他類別可能會彼此封鎖無法執行其相關`SyncLock`區塊。 同樣地，字串鎖定可能會有問題，因為處理序使用相同的字串中的任何其他程式碼會共用相同的鎖定。  
  
 您也不應該使用`Me.GetType`方法以提供所需的鎖定物件的共用資料。 這是因為`GetType`一律傳回相同`Type`指定的類別名稱的物件。 外部程式碼可以呼叫`GetType`針對您的類別，並取得您正在使用相同的鎖定物件。 這會導致封鎖彼此從兩個類別其`SyncLock`區塊。  
  
## <a name="examples"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會維護訊息的簡單清單的類別。 陣列中保留訊息和最後一個變數中使用該陣列的項目。 `addAnotherMessage`程序遞增的最後一個元素，並將新的訊息。 這兩項作業會受到`SyncLock`和`End SyncLock`陳述式，因為其他任何執行緒可以一次遞增的最後一個元素之前，一旦已遞增的最後一個元素，必須儲存新的訊息。  
  
 如果`simpleMessageList`類別共用所有的執行個體，變數之間的訊息傳遞一份清單`messagesList`和`messagesLast`會宣告為`Shared`。 在此情況下，變數`messagesLock`也應該`Shared`，因此會有每個執行個體所使用的單一鎖定物件。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>描述  
 下列範例會使用執行緒和`SyncLock`。 只要`SyncLock`陳述式存在，陳述式區塊是關鍵區段和`balance`絕對不會是負數值。 您可以註解`SyncLock`和`End SyncLock`陳述式，以查看留下的效果`SyncLock`關鍵字。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>註解  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [執行緒同步處理](../../programming-guide/concepts/threading/thread-synchronization.md)  
 [執行緒處理](../../programming-guide/concepts/threading/index.md)
