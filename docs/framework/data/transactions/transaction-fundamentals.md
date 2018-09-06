---
title: 交易基礎觀念
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 20bce37bb5d5aa1460570b1d39b54c2cb8a3362f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036648"
---
# <a name="transaction-fundamentals"></a>交易基礎觀念
交易作業會將多項工作繫結在一起。 例如，想像應用程式正在執行兩項工作。 首先，它會在資料庫中建立新的表格。 接著，它會呼叫特定物件來收集與格式化資料，然後將資料插入新的表格中。 這兩項工作都是相關的，甚至是互相依存的，除非您可以在表格中填入資料，否則您會想要避免建立新的表格。 在單一交易範圍內執行這兩項工作，會將這兩項工作強制聯結在一起。 如果第二項工作失敗，第一項工作就會復原至建立新表格之前的時間點。  
  
 為了確保行為可以預測，所有交易都必須具備基本 ACID 屬性 (不可部分完成性、一致性、隔離性，以及耐用性)。 這些屬性會以「全部或無」(All-Or-None) 的論點來強調重要的交易角色。 如需有關 ACID 的詳細資訊，請參閱[ACID 屬性](https://go.microsoft.com/fwlink/?LinkId=98791)。 簡言之，ACID 可確保一組相關工作會全部成功或失敗。 在交易處理術語中，交易可以認可或中止。 若要讓交易認可，所有的參與者都必須保證任何對資料的變更都是永久的。 不管系統是否當機，還是發生其他不可預見的事件，變更必須持續。 只要任何一個參與者無法做出此保證，整個交易就會失敗。 所有對交易範圍內的資料所做的變更，都會復原到特定的時間點。  
  
 交易可以限定在單一資料資源，例如資料庫或訊息佇列。 在此情況中，本機交易會受到 <xref:System.Transactions> 所提供的交易管理員所管理，進而提升效能。 受到資料資源控制的這些交易會很有效率，而且容易管理。  
  
 交易也可以跨越多個資料資源。 分散式交易可讓您將發生在不同系統上的數個個別作業整合至單一成功或失敗動作。 在此情況中，駐留在每個系統中的「Microsoft 分散式交易協調器」(MSDTC) 將協調所有交易。  
  
 當您使用 <xref:System.Transactions> 所提供的類別來開發交易式應用程式時，不用擔心需要哪種交易，或是會牽涉到那個交易管理員。 <xref:System.Transactions> 基礎結構會自動為您打點好所有事項。  
  
 當您建立異動時，可以指定套用至異動的隔離等級。 所定義的隔離層級<xref:System.Transactions.IsolationLevel>列舉，決定其他交易將會有資料受您交易的存取層級為何。  
  
 您可以建立使用 ADO.NET，交易<xref:System.EnterpriseServices>，或所提供的交易式程式設計模型<xref:System.Transactions>命名空間。 [System.Transactions 所提供的功能](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)主題將討論您可以使用來撰寫交易式應用程式使用的功能<xref:System.Transactions>命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [System.Transactions 所提供的功能](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)
