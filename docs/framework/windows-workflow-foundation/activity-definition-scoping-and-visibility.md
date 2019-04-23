---
title: 活動定義範圍和可視性
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: 27c43323a176c841f3d90cb9c52f25599bc0686d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976686"
---
# <a name="activity-definition-scoping-and-visibility"></a>活動定義範圍和可視性
就像物件的範圍和可視性一樣，活動定義範圍和可視性是其他物件或活動存取活動成員的能力。 活動定義是由下列實作所執行：  
  
1. 決定活動公開給其使用者的成員 (<xref:System.Activities.Argument>、<xref:System.Activities.Variable> 和 <xref:System.Activities.ActivityDelegate> 物件及子活動)。  
  
2. 實作活動的執行邏輯  
  
 此實作所牽涉到的成員可能未公開給活動的消費者，但是為實作的詳細資料。  與型別定義類似，活動模型允許作者限定有關所定義之活動定義的活動成員可視性。  此可視性會控管成員使用的層面，例如資料範圍。  
  
## <a name="scope"></a>範圍  
 除了資料範圍以外，活動模型可視性也可以限制存取活動的其他層面，例如驗證、偵錯或追蹤。 執行屬性會使用可視性與範圍，將執行特性限制為特定的定義範圍。 次要根項目會使用可視性與範圍，將 <xref:System.Activities.Statements.CompensableActivity> 所擷取的狀態限制為使用可補償之活動的定義範圍。  
  
## <a name="definition-and-usage"></a>定義與使用  
 撰寫新的活動，藉由繼承自基底活動類別，以及使用中的活動所撰寫的工作流程[內建活動程式庫](net-framework-4-5-built-in-activity-library.md)。 為了能夠使用活動，活動作者必須設定其定義之每一個元件的可視性。  
  
### <a name="activity-members"></a>活動成員  
 活動模型會定義該活動提供給消費者使用的引數、變數、委派和子活動。 這些成員的每一個都可以宣告為 `public` 或 `private`。 Public 成員是由活動的消費者所設定，而 `private` 成員則會使用活動作者所固定的實作。 資料範圍的可視性規則如下所示：  
  
1. Public 成員以及 Public 子活動的 Public 成員可以參考 Public 變數。  
  
2. Private 成員以及 public 子活動的 public 成員可以參考引數和 private 變數。  
  
 可由活動的消費者所設定的成員絕對不能為 private。  
  
### <a name="authoring-models"></a>撰寫模型  
 自訂活動是使用 <xref:System.Activities.NativeActivity>、<xref:System.Activities.Activity>、<xref:System.Activities.CodeActivity> 或 <xref:System.Activities.AsyncCodeActivity> 所定義。 衍生自這些類別的活動可以公開具有不同可視性的不同成員型別。  
  
#### <a name="nativeactivity"></a>NativeActivity  
 衍生自 <xref:System.Activities.NativeActivity> 的活動擁有以命令性程式碼所撰寫的行為，而且可以選擇使用現有的活動加以定義。 從 <xref:System.Activities.NativeActivity> 衍生活動會授與執行階段所公開之所有功能的存取權。 這類活動的任何成員都可以使用 public 或 private 可視性加以定義，但是只能宣告為 `public` 的引數除外。  
  
 衍生自 <xref:System.Activities.NativeActivity> 的類別成員會宣告給執行階段，其方式是使用傳遞給 <xref:System.Activities.NativeActivityMetadata> 方法的 <xref:System.Activities.NativeActivity.CacheMetadata%2A> Struct。  
  
#### <a name="activity"></a>活動  
 使用 <xref:System.Activities.Activity> 建立的活動所擁有的行為，只會透過撰寫其他活動加以設計。 <xref:System.Activities.Activity> 類別有一個子活動實作，這是由執行階段使用 <xref:System.Activities.Activity.Implementation%2A> 所取得。 衍生自 <xref:System.Activities.Activity> 的活動可以定義 public 引數、public 變數、匯入的 ActivityDelegates 和匯入的 Activities。  
  
 匯入的 ActivityDelegates 和 Activities 會宣告為活動的 public 子系，但是不能由活動直接排程。 驗證期間會使用這項資訊，以避免在絕對不會執行活動的位置執行面對父系的驗證。 此外，活動的實作也可以參考和排程匯入的子系，就像 public 子系一樣。 這表示，匯入名為 Activity1 之活動的某項活動可以在排程 Activity1 的實作中包含 <xref:System.Activities.Statements.Sequence>。  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity/ AsyncCodeActivity  
 此基底類別會在命令式程式碼中用來撰寫行為。 衍生自這個類別的活動只能存取其所公開的引數。 這表示，只有這些活動可以公開的成員才是 public 引數。 沒有其他成員或可視性會套用到這些活動。  
  
#### <a name="summary-of-visibilities"></a>可視性摘要  
 下表摘要列出本章節稍早的資訊。  
  
|成員類型|NativeActivity|活動|CodeActivity/ AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|引數|Public/ Private|Public|不適用|  
|變數|Public/ Private|Public|不適用|  
|Child Activities|Public/ Private|Public，實作中定義的一個固定 private 子系。|不適用|  
|ActivityDelegates|Public/ Private|Public|不適用|  
  
 一般來說，活動的消費者所無法設定的成員不能為 public。  
  
### <a name="execution-properties"></a>執行屬性  
 在某些情況下，將特定執行屬性的範圍設定為活動的 public 子系會很實用。 <xref:System.Activities.ExecutionProperties> 集合會將 <xref:System.Activities.ExecutionProperties.Add%2A> 方法提供給這項功能。 這個方法有一個布林參數，可指示特定屬性的範圍為所有子系還是 public 子系。 如果這個參數設定為 `true`，此屬性只能讓 public 成員以及其 public 子系的 public 成員看到。  
  
### <a name="secondary-roots"></a>次要根項目  
 次要根項目是執行階段的內部機制，可管理補償活動的狀態。 當 <xref:System.Activities.Statements.CompensableActivity> 執行完之後，不會立即清除它的狀態。 該狀態會由執行階段的次要根項目所維護，直到補償時段完成為止。 使用次要根項目所擷取的位置環境會對應到使用可補償活動的定義範圍。
