---
title: "狀態機器工作流程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 狀態機器工作流程
狀態機器是常見的開發程式架構。<xref:System.Activities.Statements.StateMachine>活動及  <xref:System.Activities.Statements.State>、<xref:System.Activities.Statements.Transition> 與其他活動皆可用於建置狀態機器工作流程程式。本主題提供建立狀態機器工作流程的概觀。  
  
## 狀態機器工作流程概觀  
 狀態機工作流提供模型樣式，可供您以事件導向方式建立您的工作流程模型。<xref:System.Activities.Statements.StateMachine>活動包含組成狀態機器邏輯的狀態和轉換，只要能使用活動，就能使用該活動。狀態機器執行階段包含數種類別：  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 若要建立狀態機器工作流程，必須將狀態加入至 <xref:System.Activities.Statements.StateMachine> 活動，並且使用轉換控制狀態之間的流向。下列螢幕擷取畫面取自於 [快速入門教學課程](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)的[HOW TO：建立狀態機器工作流程](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md)步驟，內容顯示含三個狀態和三個轉換的狀態機器工作流程。**Initialize Target** 是初始狀態，表示工作流程中的第一個狀態。這是由從 \[**狀態**\] 節點連到該狀態的線條委派的。工作流程中的最終狀態名為 **FinalState**，代表工作流程結束的點。  
  
 ![已完成的狀態機器工作流程](../../../docs/framework/windows-workflow-foundation//media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 狀態機器工作流程必須且只能有一個初始狀態，而且至少要有一個最終狀態。每個不是最後狀態的狀態至少要有一個轉換。以下各節說明建立和設定狀態及轉換。  
  
## 建立和設定狀態  
 <xref:System.Activities.Statements.State> 表示狀態機器可以具有的狀態。若要將 <xref:System.Activities.Statements.State> 加入至工作流程，請從 \[**工具箱**\] 的 \[**狀態機器**\] 區段中，將 \[**State**\] 活動設計工具拖放至 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 介面的 <xref:System.Activities.Statements.StateMachine> 活動上。  
  
 ![WF4 狀態機器活動](../../../docs/framework/windows-workflow-foundation//media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 若要將狀態設定為 \[**初始狀態**\]，請以滑鼠右鍵按一下該狀態，然後選取 \[**設為初始狀態**\]。此外，如果沒有目前的初始狀態，可從工作流程最上方的 \[**狀態**\] 節點拖曳線條到所需的狀態，以指定初始狀態。將<xref:System.Activities.Statements.StateMachine>活動放置到工作流程設計工具上時，會預先設定一個名為 **State1** 的初始狀態。狀態機器工作流程必須且只能有一個初始狀態。  
  
 在狀態機器中代表終止狀態的狀態稱為最終狀態。最終狀態就是具有其 <xref:System.Activities.Statements.State.IsFinal%2A> 屬性設為 `true` 的狀態，沒有任何 <xref:System.Activities.Statements.State.Exit%2A> 活動，而且沒有源自於此的轉換。若要將最後狀態加入到工作流程中，請將 **FinalState** 活動從 \[**工具箱**\] 的 \[**狀態機器**\] 區段拖放到 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 介面的 <xref:System.Activities.Statements.StateMachine> 活動上。狀態機器工作流程至少要有一個最終狀態。  
  
### 設定輸入與結束動作  
 狀態可以有 <xref:System.Activities.Statements.State.Entry%2A>和  <xref:System.Activities.Statements.State.Exit%2A>動作。 \(設定為最終狀態的狀態只能有一個輸入動作\)。當工作流程執行個體進入狀態時，會執行輸入動作中的所有活動。輸入動作完成時，會排定該狀態之轉換的觸發程序。確認轉換成另一個狀態時，會執行結束狀態中的活動，即使該狀態會重新轉換回同一個狀態。退出動作完成後，會執行轉換動作中的活動，然後執行轉換目標的新狀態，同時排定其輸入動作。  
  
> [!NOTE]
>  偵錯狀態機器工作流程時，可以將中斷點放置在根狀態機活動和狀態機器工作流程的狀態上。中斷點不能直接放在轉換上，但可以放置在狀態及轉換所包含的任何活動上。  
  
## 建立和設定轉換  
 所有狀態至少要有一個轉換，但最終狀態不能有任何轉換。可在將狀態加入到狀態機器工作流程之後加入轉換，也可以在放置狀態時建立轉換。  
  
 若要在同一個步驟中加入 <xref:System.Activities.Statements.State> 並建立轉換，請從 \[**工具箱**\] 的 \[**狀態機器**\]區段拖曳 **State** 活動，並將該活動移到工作流程設計工作中另一個狀態的上方。當被拖曳的 <xref:System.Activities.Statements.State> 位在另一個 <xref:System.Activities.Statements.State> 上方時，一個 <xref:System.Activities.Statements.State> 周圍會出現四個三角形。如果將 <xref:System.Activities.Statements.State> 放到四個三角形的其中一個，它會加入到狀態機器，並建立從 <xref:System.Activities.Statements.State> 到放置目的地 <xref:System.Activities.Statements.State> 的轉換。如需詳細資訊，請參閱[轉換活動設計工具](../Topic/Transition%20Activity%20Designer.md)。  
  
 若要在加入狀態後建立轉換，有兩個選項。第一個選項是從工作流程設計工具介面拖曳狀態，然後將它移到現有狀態的上方，然後放置在其中一個放置點上。這種方法與上一節說明的方法類似。您也可以將滑鼠游標移到所需的來源狀態上方，然後拖曳一條線道所需的目的地狀態。  
  
> [!NOTE]
>  狀態機器中的單一狀態可以具有最多 76 個以工作流程設計工具建立的轉換。在設計工具外建立的工作流程狀態轉換，其數目上限僅受系統資源限制。  
  
 轉換可以有 <xref:System.Activities.Statements.Transition.Trigger%2A>、  <xref:System.Activities.Statements.Transition.Condition%2A> 和  <xref:System.Activities.Statements.Transition.Action%2A>。轉換的 <xref:System.Activities.Statements.Transition.Trigger%2A> 會在轉換之來源狀態的  <xref:System.Activities.Statements.State.Entry%2A>動作完成時排定。通常，<xref:System.Activities.Statements.Transition.Trigger%2A> 是等候特定型別的事件發生的活動，但它可以是任何活動，也可以不是活動。<xref:System.Activities.Statements.Transition.Trigger%2A>活動完成後，如有  <xref:System.Activities.Statements.Transition.Condition%2A> 存在，就會進行評估。如果沒有任何 <xref:System.Activities.Statements.Transition.Trigger%2A>活動，就會立即評估  <xref:System.Activities.Statements.Transition.Condition%2A>。如果條件評估為 `false`，則會取消轉換，並且重新排定該狀態之所有轉換的  <xref:System.Activities.Statements.Transition.Trigger%2A> 活動。如果有其他轉換共用相同的來源狀態做為目前的轉換，則會取消這些 <xref:System.Activities.Statements.Transition.Trigger%2A> 動作並重新排定。如果<xref:System.Activities.Statements.Transition.Condition%2A>評估為 `true`，或者沒有任何條件，則會執行來源狀態的 <xref:System.Activities.Statements.State.Exit%2A>動作，然後執行轉換的 <xref:System.Activities.Statements.Transition.Action%2A>。當<xref:System.Activities.Statements.Transition.Action%2A>完成後，會將控制傳遞給 \[**目標**\] 狀態  
  
 共用觸發程序的轉換稱為共用觸發轉換。共用觸發程序的轉換群組中的每個轉換都包含相同的觸發程序，但各自擁有唯一的 <xref:System.Activities.Statements.Transition.Condition%2A>和行動。若要將其他動作加入到轉換並建立共用轉換，按一下表示目的狀態的開頭的圓形，然後拖曳到想要的狀態。新的轉換會和初始轉換共用同一個觸發程序，但具有唯一的條件和動作。共用轉換可以從轉換設計工具內建立，方式是按一下轉換設計工具底部的 \[**加入共用觸發轉換**\]，然後從 \[**可連接的狀態**\] 下拉式清單選取想要的目標狀態。  
  
> [!NOTE]
>  請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為  `False` \(或所有共用觸發轉換的條件皆評估為  `False`\)，則不會發生轉換，且會重新排定該狀態之所有轉換的所有觸發。  
  
 如需建立狀態機器工作流程的詳細資訊，請參閱 [HOW TO：建立狀態機器工作流程](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md), [StateMachine 活動設計工具](../Topic/StateMachine%20Activity%20Designer.md), [狀態活動設計工具](../Topic/State%20Activity%20Designer.md), [FinalState 活動設計工具](../Topic/FinalState%20Activity%20Designer.md) 和 [轉換活動設計工具](../Topic/Transition%20Activity%20Designer.md)。  
  
## 狀態機器用語  
 本節定義在本主題中使用的狀態機器詞彙。  
  
 State  
 組成狀態機器的基本單位。狀態機器可以在任何特定時間進入一種狀態。  
  
 輸入行動  
 進入狀態時執行的動作  
  
 結束行動  
 結束狀態時執行的動作  
  
 轉換  
 兩個狀態之間的定向關係，代表狀態機器對發生特定類型之事件的完整回應。  
  
 共用轉換  
 與一個或多個轉換共用來源狀態及觸發程序的轉換，但每個轉換有其唯一條件和動作。  
  
 觸發程序  
 導致發生轉換的觸發活動。  
  
 條件  
 觸發後，條件約束必須評估為 `true`，才能使轉換完成。  
  
 轉換動作  
 執行特定轉換時執行的活動。  
  
 條件轉換  
 有明確條件的轉換。  
  
 自行轉換  
 從其他狀態轉換成其本身的轉換。  
  
 初始狀態  
 代表狀態機器起點的狀態。  
  
 最終狀態  
 代表狀態機器完成的狀態。  
  
## 請參閱  
 [HOW TO：建立狀態機器工作流程](../../../docs/framework/windows-workflow-foundation//how-to-create-a-state-machine-workflow.md)   
 [StateMachine 活動設計工具](../Topic/StateMachine%20Activity%20Designer.md)   
 [狀態活動設計工具](../Topic/State%20Activity%20Designer.md)   
 [FinalState 活動設計工具](../Topic/FinalState%20Activity%20Designer.md)   
 [轉換活動設計工具](../Topic/Transition%20Activity%20Designer.md)