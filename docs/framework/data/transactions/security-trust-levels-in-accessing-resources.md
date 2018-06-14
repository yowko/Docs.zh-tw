---
title: 存取資源的安全性信任層級
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 8e7d632c361ea73cb65668e43506d9e1128d31ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357591"
---
# <a name="security-trust-levels-in-accessing-resources"></a>存取資源的安全性信任層級
本主題說明如何針對 <xref:System.Transactions> 所公開的資源型別限制其存取。  
  
 <xref:System.Transactions> 主要有三種信任層級。 信任層級會依據 <xref:System.Transactions> 所公開的資源型別，以及在存取這些資源時應該會用到的信任層級，來加以定義。 <xref:System.Transactions> 提供存取的資源是系統記憶體、共用的所有處理序資源，以及整個系統資源。 這些層級是：  
  
-   **AllowPartiallyTrustedCallers** (APTCA) 使用單一應用程式網域內的交易之應用程式。  
  
-   **DistributedTransactionPermission** (DTP) 使用分散式的交易的應用程式。  
  
-   永久性資源、組態管理應用程式，以及舊版 Interop 應用程式的完全信任。  
  
> [!NOTE]
>  您不應該使用模擬內容來呼叫任何登記介面。  
  
## <a name="trust-levels"></a>信任層級  
  
### <a name="aptca-partial-trust"></a>APTCA (部分信任)  
 <xref:System.Transactions>可由部分信任程式碼呼叫組件，因為標示為**AllowPartiallyTrustedCallers**屬性 (APTCA)。 這個屬性基本上會移除隱含<xref:System.Security.Permissions.SecurityAction.LinkDemand>如**FullTrust**權限集合也就是自動放置在每個型別中每個公開存取方法上。 然而，部分型別和成員仍舊需要更強勢的使用權限。  
  
 APTCA 屬性可讓應用程式在單一應用程式定義域中以部分信任方式來使用交易。 這樣一來就可以使用非擴大規模的交易與變動性登記來處理錯誤。 交易雜湊資料表與使用該交易雜湊資料表的應用程式即是一例。 您可以在單一交易中將資料加入雜湊資料表或從雜湊資料表移除資料。 如果交易稍後復原回來，則所有在該交易底下對雜湊資料表所做的變更都會復原。  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 當 <xref:System.Transactions> 交易的規模擴大至需由 MSDTC 管理時，<xref:System.Transactions> 就會要求 <xref:System.Transactions.DistributedTransactionPermission> (DTP) 建立分散式交易。 也就是說，導致交易規模擴大的程式碼 (例如透過序列化或額外的永久性登記作業) 需要被授予 DTP。 原先建立 <xref:System.Transactions> 交易的程式碼，不一定需要擁有此使用權限。  
  
### <a name="fulltrust-link-demands"></a>FullTrust 連結要求  
 這項權限等級主要是用來限制寫入永久性資源的應用程式權限。 一旦發生失敗，應用程式需要能夠透過交易管理員來復原，以決定交易的最後結果，方便它更新永久資料。 此類型的應用程式我們稱為永久性資源管理員。 SQL 即是典型的這類應用程式類型。  
  
 為了啟用復原，此類型的應用程式必須具備永久取用系統資源的能力。 這是因為可復原的交易管理員必須一直記住已經認可的交易，直到它確認所有參與交易的永久性資源管理員都已收到結果告知。 因此，這類型的應用程式需要完全信任，而且不應該在未獲得此信任等級之前貿然執行。  
  
 如需有關的永久性登錄和復原的詳細資訊，請參閱[編列的資源，以在交易中的參與者身分](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)和[執行復原](../../../../docs/framework/data/transactions/performing-recovery.md)主題。  
  
 要擁有完全信任，必須同時具備使用 COM+ 來執行舊版 Interop 工作的應用程式。  
  
 下列是一份型別和成員不是可由呼叫部分信任的程式碼，因為它們以裝飾**FullTrust**宣告式安全性屬性：  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
-   <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
-   <xref:System.Transactions.TransactionInterop>  
  
-   <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
-   <xref:System.Transactions.HostCurrentTransactionCallback>  
  
-   <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
-   <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
-   <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 只立即呼叫端需要擁有**FullTrust**權限設為使用上述的型別或方法。
