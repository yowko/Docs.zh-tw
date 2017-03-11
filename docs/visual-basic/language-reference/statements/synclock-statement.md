---
title: "SyncLock Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.SyncLock"
  - "SyncLock"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "threading [Visual Basic], locks"
  - "SyncLock statement"
  - "locks, threads"
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# SyncLock Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在執行陳述式區塊之前，取得此區塊的獨佔鎖定。  
  
## 語法  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## 組件  
 `lockobject`  
 必要項。  判定為物件參考的運算式。  
  
 `block`  
 選擇項。  要在取得鎖定時執行的陳述式區塊。  
  
 `End SyncLock`  
 結束 `SyncLock` 區塊。  
  
## 備註  
 `SyncLock` 陳述式可確保多個執行緒不會同時執行陳述式區塊。  `SyncLock` 可防止每個執行緒進入區塊，直到沒有其他執行緒在執行該區塊為止。  
  
 `SyncLock` 的最常見用法就是保護資料，使其不會讓多個執行緒同時更新。  如果操作資料的陳述式必須在不受干擾的情況下完成，請將它們放在 `SyncLock` 區塊內。  
  
 獨佔鎖定所保護的陳述式區塊有時稱為「*關鍵區段*」\(Critical Section\)。  
  
## 規則  
  
-   分支。  您無法從區塊外部分支進入 `SyncLock` 區塊。  
  
-   鎖定物件值。  `lockobject` 的值不能是 `Nothing`。  您必須先建立鎖定物件，然後才能在 `SyncLock` 陳述式中使用它。  
  
     執行 `SyncLock` 區塊時，您無法變更 `lockobject` 的值。  這個機制需要鎖定物件保持不變。  
  
-   您可以在 `SyncLock` 區塊無法使用 [等候](../../../visual-basic/language-reference/operators/await-operator.md) 運算子。  
  
## 行為  
  
-   機制。  當執行緒到達 `SyncLock` 陳述式時，它會評估 `lockobject` 運算式並暫止執行，直到它對運算式所傳回的物件取得獨佔鎖定為止。  當其他執行緒到達 `SyncLock` 陳述式時，它不會取得鎖定，直到第一個執行緒執行 `End SyncLock` 陳述式為止。  
  
-   保護資料。  如果 `lockobject` 是 `Shared` 變數，則獨佔鎖定會防止類別中任何執行個體的執行緒，在當其他執行緒執行 `SyncLock` 區塊時執行這個區塊。  這可保護共用於所有執行個體之間的資料。  
  
     如果 `lockobject` 是執行個體變數 \(Instance Variable\) \(不是 `Shared`\)，則鎖定會防止在目前執行個體中執行之執行緒會與相同執行個體中的其他執行緒同時執行 `SyncLock` 區塊。  這可保護個別執行個體所維護的資料。  
  
-   取得和釋放。  `SyncLock` 區塊的行為如同 `Try...Finally` 語法結構一般，其中 `Try` 區塊會對 `lockobject` 取得獨佔鎖定，而 `Finally` 區塊則會釋放它。  因為如此，所以不管您如何結束區塊，`SyncLock` 區塊都保證會釋放鎖定。  即使在未處理例外狀況的情況下也是一樣。  
  
-   Framework 呼叫。  `SyncLock` 會呼叫 <xref:System.Threading> 命名空間中 `Monitor` 類別的 `Enter` 和 `Exit` 方法，藉以取得和釋放獨佔鎖定。  
  
## 程式設計作法  
 `lockobject` 運算式應該一律會判定為專屬於您類別的物件。  您應該宣告 `Private` 物件變數，以保護屬於目前執行個體的資料，或宣告 `Private Shared` 物件變數，以保護所有執行個體通用的資料。  
  
 您不該使用 `Me` 關鍵字，提供執行個體資料的鎖定物件。  如果類別之外的程式碼具有類別執行個體的參考，則它可以使用該參考做為 `SyncLock` 區塊 \(完全不同於您的區塊\) 的鎖定物件，保護不同的資料。  如此一來，您的類別和其他類別可以阻止彼此執行其不相關的 `SyncLock` 區塊。  同樣地，字串鎖定可能會有問題，因為使用相同字串的處理序中的任何其他程式碼將會共用相同的鎖定。  
  
 您也不該使用 `Me.GetType` 方法，提供共用資料的鎖定物件。  這是因為 `GetType` 一律會針對指定的類別名稱傳回相同的 `Type` 物件。  外部程式碼可以在您的類別上呼叫 `GetType`，並取得所用的相同鎖定物件。  這將導致兩個類別阻止彼此執行其 `SyncLock` 區塊。  
  
## 範例  
  
### 描述  
 下列範例會顯示維護簡單訊息清單的類別。  它將訊息保存在陣列中，並將該陣列的最後使用項目保存在變數中。  `addAnotherMessage` 程序會增加最後一個項目並儲存新的訊息。  這兩個作業會受到 `SyncLock` 和 `End SyncLock` 陳述式的保護，因為一旦增加了最後一個項目，就必須先儲存新訊息，然後任何其他執行緒才能再增加最後一個項目。  
  
 如果 `simpleMessageList` 類別在其所有執行個體間共用了一份訊息清單，則變數 `messagesList` 和 `messagesLast` 將宣告為 `Shared`。  在這種情況下，變數 `messagesLock` 也應該是 `Shared`，使得每個執行個體使用單一鎖定物件。  
  
### 程式碼  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/synclock-statement_1.vb)]  
  
### 描述  
 下列的範例會使用執行緒與 `SyncLock`。  只要 `SyncLock` 陳述式存在，此陳述式區塊就是關鍵區段，而且 `balance` 永遠不會成為負數。  您可以取消 `SyncLock` 和 `End SyncLock` 陳述式的註解，以查看省略 `SyncLock` 關鍵字的效果。  
  
### 程式碼  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/synclock-statement_2.vb)]  
  
### 註解  
  
## 請參閱  
 <xref:System.Threading>   
 <xref:System.Threading.Monitor>   
 [執行緒同步處理](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)   
 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)