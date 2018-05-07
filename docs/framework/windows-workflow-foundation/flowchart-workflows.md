---
title: Flowchart 工作流程
ms.date: 03/30/2017
ms.assetid: b0a3475c-d22f-49eb-8912-973c960aebf5
ms.openlocfilehash: dd013e47da881c16d1fa469dfc3e3c4f2a86b6e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="flowchart-workflows"></a>Flowchart 工作流程
流程圖是設計程式的常見範例。 Flowchart 活動通常用於實作非循序性的工作流程，但如果沒有使用 `FlowDecision` 節點，也可用於循序性的工作流程。  
  
## <a name="flowchart-workflow-structure"></a>Flowchart 工作流程結構  
 流程圖活動是包含所要執行之活動集合的活動。  流程圖還包含流程控制元素，例如 <xref:System.Activities.Statements.FlowDecision> 和 <xref:System.Activities.Statements.FlowSwitch%601>，可根據變數的值，在所包含的活動之間主導執行。  
  
## <a name="types-of-flow-nodes"></a>流程節點的型別  
 使用的項目型別，要視項目執行時所需的流程控制型別而定。 流程圖項目的型別有：  
  
-   `FlowStep` - 建立流程圖中一個步驟執行的模型。  
  
-   `FlowDecision` - 根據 Boolean 條件執行的分支，與 <xref:System.Activities.Statements.If> 相似。  
  
-   `FlowSwitch` - 根據專有參數執行的分支，與 <xref:System.Activities.Statements.Switch%601> 相似。  
  
 每個連結都有 `Action` 屬性，會定義可用來執行子活動的 <xref:System.Activities.ActivityAction>，以及一個或多個 `Next` 屬性，以定義當目前的元素完成執行時，要執行哪個或哪些元素。  
  
### <a name="creating-a-basic-activity-sequence-with-a-flowstep-node"></a>使用 FlowStep 節點建立基礎活動序列  
 若要建立讓兩個活動從中輪流執行的基礎序列，就要使用 `FlowStep` 項目。 在下列範例中，會使用兩個 `FlowStep` 項目來依序執行兩個活動。  
  
```xml  
<Flowchart>  
  <FlowStep>      
  <Assign DisplayName="Get Name">  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:String">[result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:String">["User"]</InArgument>  
    </Assign.Value>  
  </Assign>  
    <FlowStep.Next>  
      <FlowStep>  
        <WriteLine Text="["Hello, " & result]"/>  
</FlowStep>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-a-conditional-flowchart-with-a-flowdecision-node"></a>使用 FlowDecision 節點建立條件式流程圖  
 若要在流程圖工作流程中建立條件式流程節點 (也就是，建立做為傳統流程圖決策符號的連結)，就要使用 <xref:System.Activities.Statements.FlowDecision> 節點。 節點的 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 屬性設定為定義條件的運算式，而且 <xref:System.Activities.Statements.FlowDecision.True%2A> 和 <xref:System.Activities.Statements.FlowDecision.False%2A> 屬性設定為當運算式評估為 <xref:System.Activities.Statements.FlowNode> 或 `true` 時所要執行的 `false` 執行個體。 下列範例示範如何定義使用 <xref:System.Activities.Statements.FlowDecision> 節點的工作流程。  
  
```xml  
<Flowchart>  
  <FlowStep>  
    <Read Result="[s]"/>  
    <FlowStep.Next>  
      <FlowDecision>  
        <IsEmpty Input="[s]" />  
        <FlowDecision.True>  
    <FlowStep>  
            <Write Text="Empty"/>  
    </FlowStep>  
        </FlowDecision.True>  
        <FlowDecision.False>  
    <FlowStep>  
            <Write Text="Non-Empty"/>  
          </FlowStep>  
        </FlowDecision.False>  
      </FlowDecision>  
    </FlowStep.Next>  
  </FlowStep>  
</Flowchart>  
```  
  
### <a name="creating-an-exclusive-switch-with-a-flowswitch-node"></a>使用 FlowSwitch 節點建立獨佔開關  
 若要建立其中根據相符值選取之獨佔路徑流程圖的模型，就要使用 <xref:System.Activities.Statements.FlowSwitch%601> 節點。 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 屬性設為 <xref:System.Activities.Activity%601>，且型別參數為 <xref:System.Object>，可定義用來比對選擇的值。 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 屬性會定義用來比對條件運算式的索引鍵字典和 <xref:System.Activities.Statements.FlowNode> 物件，以及另一組 <xref:System.Activities.Statements.FlowNode> 物件，以定義當給定個案符合條件運算式時，執行的流程為何。 <xref:System.Activities.Statements.FlowSwitch%601> 也會定義 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> 屬性，此屬性會定義如果沒有符合條件運算式的情況時，應該要如何進行執行的流程。 下列範例示範如何定義使用 <xref:System.Activities.Statements.FlowSwitch%601> 項目的工作流程。  
  
```xml  
<Flowchart>  
    <FlowSwitch>  
      <FlowStep x:Key="Red">  
        <WriteRed/>  
      </FlowStep>  
      <FlowStep x:Key="Blue">  
        <WriteBlue/>  
      </FlowStep>  
      <FlowStep x:Key="Green">  
        <WriteGreen/>  
      </FlowStep>  
    </FlowSwitch>  
</Flowchart>  
```
