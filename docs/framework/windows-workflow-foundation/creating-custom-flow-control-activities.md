---
title: "建立自訂流程控制活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 12b5c8db096c0261041c29385b0ebe2e1569078c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-custom-flow-control-activities"></a>建立自訂流程控制活動
.Net Framework 包含各種流程控制活動，這些活動的運作方式與抽象程式設計結構 (例如 <xref:System.Activities.Statements.Flowchart>) 或標準程式設計陳述式 (例如 <xref:System.Activities.Statements.If>) 很相似。 本主題討論的其中一個範例專案中，架構[非泛型 ForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)。  
  
## <a name="creating-the-custom-class"></a>建立自訂類別  
 因為非泛型 ForEach 類別必須排程子活動，而且衍生自 <xref:System.Activities.NativeActivity> 的活動沒有這項功能，所以它必須衍生自 <xref:System.Workflow.Activities.CodeActivity>。  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 此自訂類別需要使用許多成員來儲存活動所使用的資料，以及提供執行活動之子活動的功能。 這些成員包括：  
  
-   `valueEnumerator`：屬於用來反覆查看項目集合之 <xref:System.Activities.Variable%601> 型別的非公用 <xref:System.Collections.IEnumerator>。 這個成員屬於 <xref:System.Activities.Variable%601> 型別，因為它是在活動內部使用，而非引數或公用屬性。如果此物件的來源位於活動外部，就會使用引數或公用屬性。  
  
-   `OnChildComplete`：每個子系完成執行時所執行的公用 <xref:System.Activities.CompletionCallback> 屬性。 這個成員會定義為 CLR 屬性，因為其值不會針對活動的不同執行個體變更。  
  
-   `Values`：用於子活動之反覆項目的輸入集合。 這個成員屬於 <xref:System.Activities.InArgument%601> 型別，因為資料的來源位於活動外部，但是集合的內容不應該在活動執行期間變更。 如果活動需要在活動執行時變更此集合內容的功能 (例如加入或移除活動)，這個成員就會定義為 <xref:System.Activities.ActivityAction>，然後每次存取該成員時就會進行評估，以便將變更提供給活動。  
  
-   `Body`：這個成員會定義要針對 `Values` 集合中每個項目執行的活動。 這個成員會定義為 <xref:System.Activities.ActivityAction>，以便每次存取該成員時進行評估。  
  
-   `Execute`：這個方法會使用 `InternalExecute`、`OnForEachComplete` 和 `GetStateAndExecute` 非共用成員來排程執行作業，並且指派 Body 成員中定義之子活動的完成處理常式。  
  
-   `CacheMetadata`：這個成員會為執行階段提供執行活動所需的資訊。 根據預設，活動的 `CacheMetadata` 方法會將活動的所有公用成員告知執行階段，但是因為此活動會針對部分功能使用私用成員，所以它必須將這些成員的存在告知執行階段，才能讓執行階段注意它們。 在此情況下，系統會覆寫 `CacheMetadata` 函式，以便存取私用 `valueEnumerator` 成員。 這個成員也會針對活動的值建立引數，以便在執行期間將它們傳入活動。
