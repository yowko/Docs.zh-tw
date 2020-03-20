---
title: 活動樹狀結構檢查
ms.date: 03/30/2017
ms.assetid: 100d00e4-8c1d-4233-8fbb-dd443a01155d
ms.openlocfilehash: 692f36d993c3f9c27839122b388a24d0698a2b59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183045"
---
# <a name="activity-tree-inspection"></a>活動樹狀結構檢查
活動樹狀檢查可供工作流程應用程式作者用於檢查應用程式所裝載的工作流程。 使用 <xref:System.Activities.WorkflowInspectionServices>，即可針對特定子活動搜尋工作流程、列舉個別活動及其屬性，以及在特定時間快取活動的執行階段中繼資料。 本主題提供 <xref:System.Activities.WorkflowInspectionServices> 的概觀，並且說明如何利用它來檢查活動樹狀結構。  
  
## <a name="using-workflowinspectionservices"></a>使用 WorkflowInspectionServices  
 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 方法用於列舉指定活動樹狀中的所有活動。 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 會傳回可列舉項目，該項目會觸及樹狀結構中的所有活動，包括子系、委派處理常式、預設變數及引數運算式。 在下列範例中，工作流程定義是使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.WriteLine> 和運算式所建立。 建立工作流程定義之後，就會叫用該工作流程，然後呼叫 `InspectActivity` 方法。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#45](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#45)]  
  
 為了列舉活動，會在根活動上呼叫 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>，然後再次以遞迴方式在每個傳回的活動上呼叫。 在下列範例中，會將活動樹狀中每個活動和運算式的 <xref:System.Activities.Activity.DisplayName%2A> 寫入至主控台。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#46](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#46)]  
  
 這個範例程式碼會提供下列輸出。  
  
 **清單項目 1**  
**清單項 2**
**清單項項 3**
**清單項 4**
**清單項項 5**
**項添加到集合中。**
**序列****文本<清單\<字串>>**  
 **While**  
 **>添加收集\<字串**  
 **<ICollection\<字串>>的變數值**  
 **lambdaValue\<字串>**  
 **位置參考值<清單\<字串>>**  
 **蘭姆達\<價值布林>**  
 **位置參考值<清單\<字串>>**  
 **對於每個\<字串>**  
 **可變值<iE500 字串\<>>**  
 **WriteLine**  
 **委託參數值\<字串>**  
 **序列**  
 **WriteLine**  
 **使用\<文本字串>** 檢索特定活動而不是枚舉所有活動。 <xref:System.Activities.WorkflowInspectionServices.Resolve%2A> 如果先前尚未呼叫過 <xref:System.Activities.WorkflowInspectionServices.Resolve%2A>，<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 和 `WorkflowInspectionServices.CacheMetadata` 都會執行中繼資料快取。 如果已經呼叫過 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>，則 <xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 會以現有的中繼資料為基礎。 因此，自上次呼叫 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A> 以來，如果樹狀結構進行過變更，<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A> 可能會產生非預期的結果。 如果在調用<xref:System.Activities.WorkflowInspectionServices.GetActivities%2A>後對工作流進行了更改，則可以通過調用<xref:System.Activities.Validation.ActivityValidationServices><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>方法重新緩存中繼資料。 下一節將討論快取中繼資料。  
  
### <a name="caching-metadata"></a>快取中繼資料  
 快取活動的中繼資料會建置並驗證活動之引數、變數、子活動和活動委派的描述。 根據預設，中繼資料會在預備執行活動時由執行階段快取。 如果工作流程主機作者想要在此之前快取活動或活動樹狀的中繼資料，例如要預先取得成本，可以使用 <xref:System.Activities.WorkflowInspectionServices.CacheMetadata%2A>，在任何時間快取中繼資料。
