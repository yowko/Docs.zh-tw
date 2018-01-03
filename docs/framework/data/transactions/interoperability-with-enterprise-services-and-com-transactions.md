---
title: "與 Enterprise Services 和 COM+ 交易的互通性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0fd0d26-fe86-443b-b208-4d57d39fa4aa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 246658ceb2fdbaa302753441ca5e34a1eef92b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-enterprise-services-and-com-transactions"></a>與 Enterprise Services 和 COM+ 交易的互通性
<xref:System.Transactions> 命名空間支援以此命名空間建立的交易物件，以及透過 COM+ 建立的交易兩者之間的互通性。  
  
 當您想要建立新的 <xref:System.Transactions.EnterpriseServicesInteropOption> 執行個體來指定與 COM+ 的互通性等級時，就可以使用 <xref:System.Transactions.TransactionScope> 列舉型別 (Enumeration)。  
  
 根據預設，當應用程式程式碼會檢查靜態<xref:System.Transactions.Transaction.Current%2A>屬性，<xref:System.Transactions>嘗試尋找其他方式的目前的交易或<xref:System.Transactions.TransactionScope>物件，指出，<xref:System.Transactions.Transaction.Current%2A>是**null**. 如果程式碼找不到當中任何一個，則 <xref:System.Transactions> 會查詢 COM+ 內容，看看是否有交易。 請注意，就算 <xref:System.Transactions> 在 COM+ 內容中找到了交易項目，仍舊偏好 <xref:System.Transactions> 的原生交易。  
  
## <a name="interoperability-levels"></a>互通性等級  
 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別會定義下列互通性等級 - <xref:System.Transactions.EnterpriseServicesInteropOption.None>、<xref:System.Transactions.EnterpriseServicesInteropOption.Full> 與 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>。  
  
 <xref:System.Transactions.TransactionScope> 類別會提供可將 <xref:System.Transactions.EnterpriseServicesInteropOption> 接受為參數的建構函式。  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.None>，如名稱所示，意味著 <xref:System.EnterpriseServices> 內容與交易範圍之間不存在任何互通性。 在使用 <xref:System.Transactions.TransactionScope> 建立了 <xref:System.Transactions.EnterpriseServicesInteropOption.None> 之後，任何對 <xref:System.Transactions.Transaction.Current%2A> 所做的變更都不會反映在 COM+ 內容中。 同理，對 COM+ 內容中的交易所做的變更，也不會反映在 <xref:System.Transactions.Transaction.Current%2A> 中。 對於 <xref:System.Transactions> 來說，這種作業模式是最快速的，因為不需要額外的同步處理。 <xref:System.Transactions.EnterpriseServicesInteropOption.None> 預設會採用 <xref:System.Transactions.TransactionScope> 值，而且所有的建構函式也不接受 <xref:System.Transactions.EnterpriseServicesInteropOption> 做為參數。  
  
 如果您希望將 <xref:System.EnterpriseServices> 交易與您的環境交易結合，便需要使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 或 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>。 這兩個值同時仰賴稱為服務的功能 (不包含元件)，因此在使用這些值的時候，您應該在 Windows XP Service Pack 2 或 Windows Server 2003 上執行。  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 指定了 <xref:System.Transactions> 與 <xref:System.EnterpriseServices> 的環境交易一律相同。 它最後會建立一個新的 <xref:System.EnterpriseServices> 交易式內容，並套用目前交易，讓 <xref:System.Transactions.TransactionScope> 成為該內容的目前交易。 這樣一來，<xref:System.Transactions.Transaction.Current%2A> 中的交易就會與 <xref:System.EnterpriseServices.ContextUtil.Transaction%2A> 中的交易完全同步處理。 此值會對效能帶來負面影響，因為可能需要建立新的 COM+ 內容。  
  
 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> 指定了下列需求：  
  
-   在檢查過 <xref:System.Transactions.Transaction.Current%2A> 之後，如果 <xref:System.Transactions> 偵測到自己正於預設內容以外的內容中執行時，就會支援 COM+ 內容中的所有交易。 請注意，預設內容無法包含交易。 因此，在預設內容中，就算包含了 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>，儲存在 <xref:System.Transactions> 使用的執行緒區域儲存區中的交易就會傳回至 <xref:System.Transactions.Transaction.Current%2A>。  
  
-   如果建立了新的 <xref:System.Transactions.TransactionScope> 物件，而建立作業發生在預設內容以外的內容之中，則 <xref:System.Transactions.TransactionScope> 物件的目前交易應該會反映在 COM+ 中。 在此情況下，<xref:System.Transactions.EnterpriseServicesInteropOption.Automatic> 會有如 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 的反應 (好像它建立了新的 COM+ 內容一樣)。  
  
 此外，當 <xref:System.Transactions.Transaction.Current%2A> 與 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 同時設定為 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>，則兩種模式同時將意味著無法直接設定 <xref:System.Transactions.Transaction.Current%2A>。  任何嘗試直接設定 <xref:System.Transactions.Transaction.Current%2A> (而不是建立 <xref:System.Transactions.TransactionScope>) 的動作將導致產生 <xref:System.InvalidOperationException>。 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別值將由未明確指定使用值的新交易範圍所繼承。 例如，如果您使用 <xref:System.Transactions.TransactionScope> 來建立新的 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 物件，然後建立了第二個 <xref:System.Transactions.TransactionScope> 物件 (但卻未指定 <xref:System.Transactions.EnterpriseServicesInteropOption> 值)，則第二個 <xref:System.Transactions.TransactionScope> 物件同樣具有 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>。  
  
 簡言之，建立新的交易範圍時將適用下列規則：  
  
1.  <xref:System.Transactions.Transaction.Current%2A> 會經過檢查，以確定是否有交易。 檢查結果為：  
  
    -   檢查是否有範圍。  
  
    -   如果有範圍，則會檢查初次建立範圍時所傳入的 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別值。  
  
    -   如果 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別設為 <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>，則 COM+ 交易 (<xref:System.EnterpriseServices> 交易) 的優先順序將高於 Managed 執行緒區域儲存區中的 <xref:System.Transactions> 交易。  
  
         如果值設為 <xref:System.Transactions.EnterpriseServicesInteropOption.None>，則 Managed 執行緒區域儲存區中的 <xref:System.Transactions> 交易將具有較高的優先順序。  
  
         如果值為 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>，則只有一個交易，那就是 COM+ 交易。  
  
2.  這時會檢查 <xref:System.Transactions.TransactionScopeOption> 建構函式所傳入的 <xref:System.Transactions.TransactionScope> 列舉型別值。 這項檢查可決定是否必須建立新的交易。  
  
3.  如果需要建立新的交易，則下列各項 <xref:System.Transactions.EnterpriseServicesInteropOption> 值將產生：  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.Full>：會建立與 COM+ 內容相關聯的交易。  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.None>：會建立 <xref:System.Transactions> 交易。  
  
    -   <xref:System.Transactions.EnterpriseServicesInteropOption.Automatic>：如果存在 COM+ 內容，則會建立交易並附加到內容之中。  
  
 下表說明了 Enterprise Services (ES) 內容，以及需要使用 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別之交易的交易式範圍。  
  
|ES 內容|無|自動|全功能|  
|----------------|----------|---------------|----------|  
|預設內容|預設內容|預設內容|建立新 <br />交易式內容|  
|非預設內容|維護用戶端內容|建立新的交易式內容|建立新的交易式內容|  
  
 下表說明了環境交易在特定 <xref:System.EnterpriseServices> 內容中的意義，以及需要使用 <xref:System.Transactions.EnterpriseServicesInteropOption> 列舉型別之交易的交易式範圍。  
  
|ES 內容|無|自動|全功能|  
|----------------|----------|---------------|----------|  
|預設內容|ST|ST|ES|  
|非預設內容|ST|ES|ES|  
  
 在上一個表格：  
  
-   ST 表示範圍的環境交易受到 <xref:System.Transactions> 管理 (有別於可能存在的任何 <xref:System.EnterpriseServices> 內容的交易)。  
  
-   ES 表示範圍的環境交易與 <xref:System.EnterpriseServices> 內容的交易完全一樣。
