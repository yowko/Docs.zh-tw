---
title: "使用交易範圍實作隱含交易  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 使用交易範圍實作隱含交易 
<xref:System.Transactions.TransactionScope> 類別提供一個簡單的方式，讓您不用與交易互動，即可將一段程式碼標記為參與交易。交易範圍可以自動選取並管理環境交易。由於 <xref:System.Transactions.TransactionScope> 類別非常容易使用且很有效率，在您開發交易應用程式時，建議您善加利用。  
  
 此外，您不需要特別針對交易登記資源。任何的 <xref:System.Transactions> 資源管理員 \(例如 SQL Server 2005\) 都可以偵測到範圍所建立的環境交易並自動加以登記。  
  
## 建立交易範圍  
 下列範例說明了 <xref:System.Transactions.TransactionScope> 類別的簡易用途。  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 交易範圍會在您建立全新的 <xref:System.Transactions.TransactionScope> 物件時立刻啟動。如程式碼範例所示，建議您建立包含一段 **using** 陳述式的範圍。C\# 與 Visual Basic 都提供使用 **using** 陳述式，其作用就像是 **try...finally** 區塊，可確保妥善處理範圍。  
  
 當具現化 <xref:System.Transactions.TransactionScope> 時，交易管理員會決定要參與哪個交易。一旦決定後，範圍永遠會參與該交易。此決策是根據兩個因素而定：環境交易是否存在，以及建構函式中的 **TransactionScopeOption** 參數值。環境交易就是要在其中執行程式碼的交易。您可以呼叫 <xref:System.Transactions.Transaction> 類別的靜態 <xref:System.Transactions.Transaction.Current%2A> 屬性，取得環境交易的參考。如需如何使用此參數的詳細資訊，請參閱本主題中「使用 TransactionScopeOption 管理交易流程」一節。  
  
## 完成交易範圍  
 當您的應用程式完成所有要在交易中執行的工作後，您應該只呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法一次，以通知交易管理員可以接受認可交易。將 <xref:System.Transactions.TransactionScope.Complete%2A> 呼叫放在 **using** 區塊中做為最後一個陳述式是很好的作法。  
  
 無法呼叫這個方法會使交易中止，因為交易管理員會將此解譯為系統錯誤，或是相當於在交易範圍內所擲回的例外狀況。不過，呼叫此方法並不保證會認可交易，這只是將您的狀態告知交易管理員的方式。在呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法後，您便無法再透過 <xref:System.Transactions.Transaction.Current%2A> 屬性存取環境交易，且嘗試這麼做會導致擲回例外狀況。  
  
 如果 <xref:System.Transactions.TransactionScope> 物件建立了交易，則資源管理員的實際交易認可工作會在 **using** 區塊的最後一行程式碼發生。如果該物件沒有建立交易，則每當 <xref:System.Transactions.CommittableTransaction> 物件的擁有者呼叫 <xref:System.Transactions.CommittableTransaction.Commit%2A> 時，便會發生認可。此時，交易管理員會呼叫資源管理員，並根據是否在 <xref:System.Transactions.TransactionScope> 物件上呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 方法而定，通知資源管理員認可或復原交易。  
  
 **using** 陳述式可確保會呼叫 <xref:System.Transactions.TransactionScope> 物件的 <xref:System.Transactions.TransactionScope.Dispose%2A> 方法，即使發生例外狀況也一樣。<xref:System.Transactions.TransactionScope.Dispose%2A> 方法會標記交易範圍的結尾。在呼叫這個方法後發生的例外狀況不太可能會影響交易。這個方法也會將環境交易還原至其先前狀態。  
  
 如果範圍建立了交易，而且交易中止，則會擲回 <xref:System.Transactions.TransactionAbortedException>。如果交易管理員無法做出認可決定，則會擲回 <xref:System.Transactions.TransactionIndoubtException>。如果認可交易，則不會擲回例外狀況。  
  
## 復原交易  
 如果您想復原交易，就不應該呼叫交易範圍內的 <xref:System.Transactions.TransactionScope.Complete%2A> 方法。例如，您可以擲回範圍內的例外狀況。這樣可復原在範圍內參與的交易。  
  
##  <a name="ManageTxFlow"></a> 使用 TransactionScopeOption 管理交易流程  
 您可以從使用本身範圍的方法中，呼叫使用 <xref:System.Transactions.TransactionScope> 的方法來巢狀化交易範圍，如下列範例中的 `RootMethod` 方法所示：  
  
```csharp  
void RootMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          SomeMethod();  
          scope.Complete();  
     }  
}  
  
void SomeMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          scope.Complete();  
     }  
}  
```  
  
 最上層的交易範圍，我們稱為根範圍。  
  
 <xref:System.Transactions.TransactionScope> 類別提供了幾項多載的建構函式以接受 <xref:System.Transactions.TransactionScopeOption> 型別的列舉，用來定義範圍的交易行為。  
  
 <xref:System.Transactions.TransactionScope> 物件包含三個選項：  
  
-   聯結環境交易，如果環境交易不存在的話，則建立新的環境交易。  
  
-   成為新的根範圍，意思就是開始新的交易並讓交易成為本身範圍中的新環境交易。  
  
-   完全不會參與交易。最後也不會產生環境交易。  
  
 如果使用 <xref:System.Transactions.TransactionScopeOption> 來具現化範圍，且存在環境交易，則範圍會聯結該交易。另一方面，如果不存在環境交易，則範圍會建立新的交易並成為根範圍。這是預設值。如果使用 <xref:System.Transactions.TransactionScopeOption>，則範圍內的程式碼不管本身是否為根，或僅僅聯結環境交易，都不需要做出不一樣的行為。在兩種情況中，程式碼的行為應該完全一樣。  
  
 如果使用 <xref:System.Transactions.TransactionScopeOption> 來具現化範圍，則一律成為根範圍。它會開始新的交易，且其交易會成為範圍內全新的環境交易。  
  
 如果使用 <xref:System.Transactions.TransactionScopeOption> 來具現化範圍，則永遠不會參與交易，不管是否存在環境交易皆然。使用此值具現化的範圍，一律將 **null** 視為環境交易。  
  
 茲將上列所有選項摘列至下表。  
  
|TransactionScopeOption|環境交易|範圍會參與|  
|----------------------------|----------|-----------|  
|必要項|否|新交易 \(將為根\)|  
|必須是新交易|否|新交易 \(將為根\)|  
|隱藏|否|無交易|  
|必要項|是|環境交易|  
|必須是新交易|是|新交易 \(將為根\)|  
|隱藏|是|無交易|  
  
 當 <xref:System.Transactions.TransactionScope> 物件聯結了現有的環境交易時，處理範圍物件可能不會結束交易，除非範圍中止交易。如果範圍交易是由根範圍所建立，則只有當根範圍已經處理完畢後才會呼叫 <xref:System.Transactions.CommittableTransaction.Commit%2A>。如果交易是手動建立的，則會在中止時或是建立者認可時結束。  
  
 下列範例所顯示的 <xref:System.Transactions.TransactionScope> 物件可建立三個巢狀範圍物件，而且每個物件都使用不同的 <xref:System.Transactions.TransactionScopeOption> 值來具現化。  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())   
//Default is Required   
{   
     using(TransactionScope scope2 = new   
      TransactionScope(TransactionScopeOption.Required))   
     {  
     ...  
     }   
  
     using(TransactionScope scope3 = new TransactionScope(TransactionScopeOption.RequiresNew))   
     {  
     ...  
     }   
  
     using(TransactionScope scope4 = new   
        TransactionScope(TransactionScopeOption.Suppress))   
    {  
     ...  
    }   
}  
```  
  
 在此範例程式碼區段中，不使用任何環境交易，而是以 <xref:System.Transactions.TransactionScopeOption> 來建立新範圍 \(`scope1`\)。`scope1` 範圍在建立新交易 \(交易 A\) 時會成為根範圍，並讓交易 A 成為環境交易。接著，`Scope1` 會建立另外三個物件，每個都包含不同的 <xref:System.Transactions.TransactionScopeOption> 值。例如，`scope2` 是由 <xref:System.Transactions.TransactionScopeOption> 所建立，而且因為環境交易已經存在，該範圍就會聯結由 `scope1` 所建立的第一個交易。請注意，`scope3` 是新交易的根範圍，而且 `scope4` 不包含任何環境交易。  
  
 儘管預設且最常用的 <xref:System.Transactions.TransactionScopeOption> 值是 <xref:System.Transactions.TransactionScopeOption>，其他所有值每個都具有唯一的用途。  
  
 當您想要保留程式碼區段所執行的作業，而且不想在作業失敗時中止環境交易，<xref:System.Transactions.TransactionScopeOption> 就會很有用處。例如，當您想要執行記錄或稽核作業，或是當您想要將事件發行到訂閱者時 \(不管您的環境交易是否已經認可或中止\)。此值可允許您在交易範圍內保有一段非交易式程式碼，如下列範例所示。  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())  
{  
     try  
     {  
          //Start of non-transactional section   
          using(TransactionScope scope2 = new  
             TransactionScope(TransactionScopeOption.Suppress))  
          {  
               //Do non-transactional work here  
          }  
          //Restores ambient transaction here  
   }  
     catch  
     {}  
   //Rest of scope1  
}  
  
```  
  
### 在巢狀範圍內投票  
 雖然巢狀範圍可以聯結根範圍的環境交易，呼叫巢狀範圍中的 <xref:System.Transactions.TransactionScope.Complete%2A> 不會對根範圍有任何影響。只有當從根範圍一直到最後一個巢狀範圍的所有範圍都投票認可交易，交易才算真正受到認可。若不在巢狀範圍中呼叫 <xref:System.Transactions.TransactionScope.Complete%2A>，將影響根範圍，因為環境交易會立即中止。  
  
## 設定 TransactionScope 逾時  
 某些多載的 <xref:System.Transactions.TransactionScope> 建構函式可接受 <xref:System.TimeSpan> 型別的值，以控制交易的逾時。設為零的逾時代表無限逾時。無限逾時最主要用在偵錯上。當您想要藉由逐步執行程式碼來隔離商務邏輯中的某個問題，但是不想要在嘗試找到問題之前讓進行偵錯的交易發生逾時，就可以使用無限逾時。在其他所有情況下使用無限逾時值時請務必特別小心，因為它會在碰到交易死結時覆寫防護措施。  
  
 在下列兩種情況中，通常您需要將 <xref:System.Transactions.TransactionScope> 逾時值設為預設以外的值。第一個情況是在開發階段，當您想要測試應用程式處理中止交易的方式時。您可以將逾時值設為較小的值 \(例如 1 毫秒\)，藉此讓交易失敗，並據此觀察錯誤處理程式碼。第二個情況是當您認為資源爭用情況涉及範圍並導致死結時，可以將此值設為小於預設逾時值。在此情況中，您希望儘快中止交易，而且不想等候預設逾時時間到期。  
  
 當範圍聯結了環境交易但卻指定了小於環境交易所設定的逾時值時，就會在 <xref:System.Transactions.TransactionScope> 物件上強制執行新的、時間較短的逾時值，而且範圍必須在指定的巢狀時間內結束，否則交易會自動中止。如果巢狀範圍的逾時值大於環境交易的逾時值，將無法產生任何作用。  
  
## 設定 TransactionScope 隔離等級  
 某些多載的 <xref:System.Transactions.TransactionScope> 建構函式可接受 <xref:System.Transactions.TransactionOptions> 型別的結構，以便指定逾時值以外的隔離等級。根據預設，交易會在隔離等級設為 <xref:System.Transactions.IsolationLevel> 時執行。在讀取頻繁的系統上，常常會選取使用 <xref:System.Transactions.IsolationLevel> 以外的隔離等級。要這麼做之前，需要先對交易處理理論、交易本身的語意、牽涉到的並行問題，以及對系統一致性的影響有很深入的了解才行。  
  
 此外，並非所有資源管理員都支援所有隔離等級，而且這些等級可能會選擇參與比所設定等級還要高的交易。  
  
 包括 <xref:System.Transactions.IsolationLevel> 的每個隔離等級都很容易因為其他交易項目存取相同資訊而產生不一致的情況。各種隔離等級的差異在於讀取\/寫入鎖定的使用方式。鎖定只有在交易項目存取資源管理員中的資料時才能暫停，或者可在認可或中止交易之前一直保持暫停。前者對於輸送量會有幫助，而後者則是容易保持一致性。兩種鎖定方式加上兩種作業 \(讀\/寫\) 方式，總共是四種基本的隔離等級。如需詳細資訊，請參閱 <xref:System.Transactions.IsolationLevel>。  
  
 在使用巢狀 <xref:System.Transactions.TransactionScope> 物件時，如果想要聯結環境交易，則所有巢狀範圍必須設定為使用完全相同的隔離等級。如果巢狀 <xref:System.Transactions.TransactionScope> 物件嘗試聯結環境交易，但卻指定了不同的隔離等級，則會擲回 <xref:System.ArgumentException>。  
  
## 和 COM\+ 互通  
 當您建立新的 <xref:System.Transactions.TransactionScope> 執行個體時，可以使用其中一個建構函式中的 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別來指定與 COM\+ 的互動方式。如需詳細資訊，請參閱[與 Enterprise Services 和 COM\+ 交易的互通性 ](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md)。  
  
## 請參閱  
 <xref:System.Transactions.Transaction.Clone%2A>   
 <xref:System.Transactions.TransactionScope>