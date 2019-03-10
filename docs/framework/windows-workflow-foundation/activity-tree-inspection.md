---
title: 活動樹狀結構檢查
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 014795b79b3536b387096e4de64266e26649da21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705489"
---
# <a name="activity-tree-inspection"></a>活動樹狀結構檢查
活動樹狀檢查可供工作流程應用程式作者用於檢查應用程式所裝載的工作流程。 使用 <xref:System.Activities.WorkflowInspectionServices>，即可針對特定子活動搜尋工作流程、列舉個別活動及其屬性，以及在特定時間快取活動的執行階段中繼資料。 本主題提供 <xref:System.Activities.WorkflowInspectionServices> 的概觀，並且說明如何利用它來檢查活動樹狀結構。  
  
## <a name="using-workflowinspectionservices"></a>使用 WorkflowInspectionServices  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 方法用於列舉指定活動樹狀結構中的所有活動。 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 會傳回可列舉項目，該項目會觸及樹狀結構中的所有活動，包括子系、委派處理常式、預設變數及引數運算式。 在下列範例中，工作流程定義是使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.WriteLine> 和運算式所建立。 建立工作流程定義之後，就會叫用該工作流程，然後呼叫 `InspectActivity` 方法。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 為了列舉活動，會在根活動上呼叫 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>，然後再次以遞迴方式在每個傳回的活動上呼叫。 在下列範例中，會將活動樹狀結構中每個活動和運算式的 <xref:System.Activities.Activity.DisplayName%2A> 寫入至主控台。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 這個範例程式碼會提供下列輸出。  
  
 **清單項目 1**  
**清單項目 2**   
**清單項目 3**   
**清單項目 4**   
**清單項目 5**   
**加入至集合的項目。**   
**順序**   
 **常值 < 清單\<字串 >>**  
 **While**  
 **AddToCollection\<String>**  
 **VariableValue<ICollection\<String>>**  
 **LambdaValue\<String>**  
 **LocationReferenceValue<List\<String>>**  
 **LambdaValue\<Boolean>**  
 **LocationReferenceValue<List\<String>>**  
 **ForEach\<String>**  
 **VariableValue<IEnumerable\<String>>**  
 **WriteLine**  
 **DelegateArgumentValue\<String>**  
 **Sequence**  
 **WriteLine**  
 **常值\<字串 >** 來擷取特定的活動，而非列舉所有活動，<xref:System.Activities.WorkflowInspectionServices.Resolve%2A>用。 如果先前尚未呼叫過 <xref:System.Activities.WorkflowInspectionServices.Resolve%2A>，<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 和 `WorkflowInspectionServices.CacheMetadata` 都會執行中繼資料快取。 如果已經呼叫過 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>，則 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 會以現有的中繼資料為基礎。 因此，自上次呼叫 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> 以來，如果樹狀結構進行過變更，<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 可能會產生非預期的結果。 如果工作流程已變更之後呼叫<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>，藉由呼叫重新快取中繼資料<xref:System.Activities.Validation.ActivityValidationServices><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>方法。 下一節將討論快取中繼資料。  
  
### <a name="caching-metadata"></a>快取中繼資料  
 快取活動的中繼資料會建置並驗證活動之引數、變數、子活動和活動委派的描述。 根據預設，中繼資料會在預備執行活動時由執行階段快取。 如果工作流程主機作者想要在此之前快取活動或活動樹狀結構的中繼資料，例如要預先取得成本，可以使用 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>，在任何時間快取中繼資料。
