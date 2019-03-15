---
title: 建立自訂流程控制活動
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 2be47281335066def5c1d267cd709db5a8ff1187
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57847007"
---
# <a name="creating-custom-flow-control-activities"></a>建立自訂流程控制活動
.NET Framework 包含各種與抽象程式設計結構的功能類似的流程控制活動 (例如<xref:System.Activities.Statements.Flowchart>) 或標準程式設計陳述式 (例如<xref:System.Activities.Statements.If>)。 本主題討論的其中一個範例專案中，架構[非泛型 ForEach](./samples/non-generic-foreach.md)。  
  
## <a name="creating-the-custom-class"></a>建立自訂類別  
 因為非泛型 ForEach 類別必須排程子活動，而且衍生自 <xref:System.Activities.NativeActivity> 的活動沒有這項功能，所以它必須衍生自 <xref:System.Workflow.Activities.CodeActivity>。  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 此自訂類別需要使用許多成員來儲存活動所使用的資料，以及提供執行活動之子活動的功能。 這些成員包括：  
  
-   `valueEnumerator`：非公用<xref:System.Activities.Variable%601>型別的<xref:System.Collections.IEnumerator>用來逐一查看集合的項目。 這個成員屬於 <xref:System.Activities.Variable%601> 型別，因為它是在活動內部使用，而非引數或公用屬性。如果此物件的來源位於活動外部，就會使用引數或公用屬性。  
  
-   `OnChildComplete`：公用<xref:System.Activities.CompletionCallback>每個子系完成執行時執行的屬性。 這個成員會定義為 CLR 屬性，因為其值不會針對活動的不同執行個體變更。  
  
-   `Values`：輸入用於子活動的反覆項目集合。 這個成員屬於 <xref:System.Activities.InArgument%601> 型別，因為資料的來源位於活動外部，但是集合的內容不應該在活動執行期間變更。 如果活動需要在活動執行時變更此集合內容的功能 (例如加入或移除活動)，這個成員就會定義為 <xref:System.Activities.ActivityAction>，然後每次存取該成員時就會進行評估，以便將變更提供給活動。  
  
-   `Body`：這個成員會定義要在執行中的每個項目的活動`Values`集合。 這個成員會定義為 <xref:System.Activities.ActivityAction>，以便每次存取該成員時進行評估。  
  
-   `Execute`：這個方法會使用`InternalExecute`， `OnForEachComplete`，和`GetStateAndExecute`排程執行，並將指派 Body 成員中所定義的子活動的完成處理常式的非公用成員。  
  
-   `CacheMetadata`：這個成員會提供執行階段，需要執行活動的資訊。 根據預設，活動的 `CacheMetadata` 方法會將活動的所有公用成員告知執行階段，但是因為此活動會針對部分功能使用私用成員，所以它必須將這些成員的存在告知執行階段，才能讓執行階段注意它們。 在此情況下，系統會覆寫 `CacheMetadata` 函式，以便存取私用 `valueEnumerator` 成員。 這個成員也會針對活動的值建立引數，以便在執行期間將它們傳入活動。
