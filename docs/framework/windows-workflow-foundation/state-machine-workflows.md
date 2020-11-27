---
title: 狀態機器工作流程
description: 本文概述如何使用 StateMachine 活動建立狀態機器工作流程。
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 5ecfc53795d50a4b633cc26c8911fec0a36f54ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262342"
---
# <a name="state-machine-workflows"></a>狀態機器工作流程

狀態機器是用來開發程式的知名範例。 <xref:System.Activities.Statements.StateMachine> 活動以及 <xref:System.Activities.Statements.State>、<xref:System.Activities.Statements.Transition> 和其他活動皆可用來建置狀態機器工作流程程式。 本主題提供建立狀態機器工作流程的概觀。  
  
## <a name="state-machine-workflow-overview"></a>狀態機器工作流程概觀  

 狀態機工作流提供模型樣式，可讓您以事件導向的方式建立工作流程的模型。 <xref:System.Activities.Statements.StateMachine> 活動包含組成狀態機器邏輯的狀態和轉換，並且適用於任何能夠使用活動的地方。 狀態機器執行階段包含數種類別：  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 若要建立狀態機器工作流程，狀態會新增至 <xref:System.Activities.Statements.StateMachine> 活動，而轉換會用來控制狀態之間的流程。 下列螢幕擷取畫面中，從 [消費者入門教學](getting-started-tutorial.md) 課程逐步解說 [如何：建立狀態機器工作流程](how-to-create-a-state-machine-workflow.md)中，會顯示具有三個狀態和三個轉換的狀態機器工作流程。 **Initialize Target** 是初始狀態，代表工作流程中的第一個狀態。 這是由從 **開始節點開始** 的那一行所指定。 工作流程中的最終狀態會命名為 **FinalState**，並代表工作流程完成的時間點。  
  
 ![顯示已完成狀態機器工作流程的圖例。](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 狀態機器工作流程必須且只能有一個初始狀態，以及至少有一個最終狀態。 每個不是最終狀態的狀態都至少要有一個轉換。 以下各節將說明建立和設定狀態及轉換。  
  
## <a name="creating-and-configuring-states"></a>建立和設定狀態  

 <xref:System.Activities.Statements.State> 代表狀態機器可以具有的狀態。 若要將加入 <xref:System.Activities.Statements.State> 至工作流程，請從 [工具箱] 的 [**狀態機器**] 區段中，將 [**狀態**] 活動設計 **工具** 拖放到 <xref:System.Activities.Statements.StateMachine> Windows 工作流程設計工具介面上的活動。  
  
 ![[工具箱] 的 [狀態機器] 區段的螢幕擷取畫面。](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 若要將狀態設定為 **初始狀態**，請以滑鼠右鍵按一下狀態，然後選取 [ **設為初始狀態**]。 此外，如果目前沒有初始狀態，則可以從工作流程頂端的 [ **開始** ] 節點將一行拖曳至所需的狀態，藉以指定初始狀態。 當 <xref:System.Activities.Statements.StateMachine> 活動放入工作流程設計工具時，它會預先設定為具有名為 **State1** 的初始狀態。 狀態機器工作流程必須且只能有一個初始狀態。  
  
 在狀態機器中代表終止狀態的狀態稱為最終狀態。 最終狀態就是其 <xref:System.Activities.Statements.State.IsFinal%2A> 屬性設為 `true` 的狀態，沒有任何 <xref:System.Activities.Statements.State.Exit%2A> 活動，而且沒有源自於此的轉換。 若要將最後狀態加入至工作流程，請從 [工具箱] 的 [**狀態機器**] 區段中，將 [ **FinalState** ] 活動設計 **工具** 拖放到 <xref:System.Activities.Statements.StateMachine> Windows 工作流程設計工具介面上的活動。 狀態機器工作流程至少要有一個最終狀態。  
  
### <a name="configuring-entry-and-exit-actions"></a>設定進入及結束動作  

 狀態可以有 <xref:System.Activities.Statements.State.Entry%2A> 和 <xref:System.Activities.Statements.State.Exit%2A> 動作。 (設定為最終狀態的狀態只能有一個進入動作)。 當工作流程執行個體進入狀態時，就會執行進入動作中的任何活動。 當輸入動作完成時，系統會排定狀態轉換的觸發程式。 確認轉換成另一個狀態時，會執行結束狀態中的活動，即使該狀態重新轉換回相同狀態也一樣。 結束動作完成後，會執行轉換動作中的活動，然後將新狀態轉換成，並排定其進入動作。  
  
> [!NOTE]
> 在偵錯狀態機器工作流程時，可以將中斷點放置在根狀態機器活動以及狀態機器工作流程的狀態上。 中斷點不能直接放在轉換上，但可以放在狀態及轉換中包含的任何活動上。  
  
## <a name="creating-and-configuring-transitions"></a>建立和設定轉換  

 所有狀態都必須至少有一個轉換，但最終狀態除外，其可能沒有任何轉換。 可在將狀態加入到狀態機器工作流程之後再加入轉換，也可以在放置狀態時建立轉換。  
  
 若要 <xref:System.Activities.Statements.State> 在一個步驟中加入和建立轉換，請從 [工具箱] 的 [**狀態機器**] 區段中拖曳 [**狀態**] 活動，並將其停留在工作流程設計 **工具** 中的另一個狀態。 當被拖曳的 <xref:System.Activities.Statements.State> 位在另一個 <xref:System.Activities.Statements.State> 上方時，另一個 <xref:System.Activities.Statements.State> 周圍會出現四個三角形。 如果將 <xref:System.Activities.Statements.State> 拖放到四個三角形的其中一個，就會將它加入到該狀態機器，並建立從來源 <xref:System.Activities.Statements.State> 到所放置之目的地 <xref:System.Activities.Statements.State> 的轉換。 如需詳細資訊，請參閱 [轉換活動設計](/visualstudio/workflow-designer/transition-activity-designer)工具。  
  
 若要在加入狀態後建立轉換，有兩個選項。 第一個選項是從工作流程設計工具介面拖曳狀態，將它移到現有狀態上方，然後在其中一個放置點上將它放下。 這與上一節所述的方法類似。 您也可以將滑鼠游標移到所需的來源狀態上方，然後將一條線拖曳至所需的目的地狀態。  
  
> [!NOTE]
> 狀態機器中的單一狀態最多可以有 76 個以工作流程設計工具來建立的轉換。 針對在設計工具以外建立的工作流程，狀態的轉換數目上限僅受制於系統資源。  
  
 轉換中可能會有 <xref:System.Activities.Statements.Transition.Trigger%2A>、<xref:System.Activities.Statements.Transition.Condition%2A> 和 <xref:System.Activities.Statements.Transition.Action%2A>。 轉換的 <xref:System.Activities.Statements.Transition.Trigger%2A> 來源狀態的動作完成時，會排程轉換 <xref:System.Activities.Statements.State.Entry%2A> 。 通常 <xref:System.Activities.Statements.Transition.Trigger%2A> 是等候某事件類型發生的活動，但它可以是任何活動，也可以不是活動。 <xref:System.Activities.Statements.Transition.Trigger%2A>活動完成後，如有　<xref:System.Activities.Statements.Transition.Condition%2A> 存在，就會對其進行評估。 如果沒有任何 <xref:System.Activities.Statements.Transition.Trigger%2A> 活動，則 <xref:System.Activities.Statements.Transition.Condition%2A> 會立即評估。 如果條件評估為 `false` ，則會取消轉換，而且狀態的 <xref:System.Activities.Statements.Transition.Trigger%2A> 所有轉換活動都會重新排程。 如果有其他與目前轉換共用相同來源狀態的轉換， <xref:System.Activities.Statements.Transition.Trigger%2A> 則也會取消和重新排程這些動作。 如果 <xref:System.Activities.Statements.Transition.Condition%2A> 評估為 `true`，或是沒有任何條件，則會執行來源狀態的 <xref:System.Activities.Statements.State.Exit%2A> 動作，然後執行轉換的 <xref:System.Activities.Statements.Transition.Action%2A>。 完成時 <xref:System.Activities.Statements.Transition.Action%2A> ，控制權會傳遞至 **目標** 狀態  
  
 共用相同觸發程序的轉換稱為共用觸發程序轉換。 共用觸發程序轉換群組中的每個轉換都有相同的觸發程序，但各自擁有唯一的 <xref:System.Activities.Statements.Transition.Condition%2A> 和動作。 若要將其他動作加入到轉換，並建立共用轉換，請按一下指出所要之轉換起始點的圓形，然後將它拖曳到所要的狀態。 新的轉換會與初始轉換共用相同的觸發程序，但擁有唯一的條件和動作。 您也可以在轉換設計工具中，按一下 [轉換設計工具] 底部的 [ **加入共用觸發程式轉換** ]，然後從 [ **要連接的可用狀態]** 下拉式清單中選取所需的目標狀態，藉以建立共用轉換。  
  
> [!NOTE]
> 請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `False` (或所有共用觸發轉換的條件皆評估為 `False`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。  
  
 如需建立狀態機器工作流程的詳細資訊，請參閱 [如何：建立狀態機器工作流程](how-to-create-a-state-machine-workflow.md)、 [StateMachine 活動設計](/visualstudio/workflow-designer/statemachine-activity-designer)工具、 [狀態活動設計](/visualstudio/workflow-designer/state-activity-designer)工具、 [FinalState 活動設計](/visualstudio/workflow-designer/finalstate-activity-designer)工具和 [轉換活動設計](/visualstudio/workflow-designer/transition-activity-designer)工具。  
  
## <a name="state-machine-terminology"></a>狀態機器術語  

 本節定義在本主題中使用的狀態機器詞彙。  
  
 州  
 組成狀態機器的基本單位。 狀態機器可在任何特定時間進入一種狀態。  
  
 進入動作  
 進入狀態時所執行的動作  
  
 結束動作  
 結束狀態時所執行的動作  
  
 轉換  
 這兩個狀態之間的引導式關聯性，表示狀態機器的完整回應發生于特定類型的事件。  
  
 共用轉換  
 與一個或多個轉換共用來源狀態及觸發程序的轉換，但每個轉換各有其唯一的條件和動作。  
  
 觸發程序  
 會導致轉換發生的觸發活動。  
  
 條件  
 必須在觸發程式之後評估為的條件約束，才能 `true` 完成轉換。  
  
 轉換動作  
 執行特定轉換時所執行的活動。  
  
 條件轉換  
 有明確條件的轉換。  
  
 自行轉換  
 從狀態傳輸至本身的轉換。  
  
 初始狀態  
 表示狀態機器起點的狀態。  
  
 最終狀態  
 表示狀態機器完成的狀態。  
  
## <a name="see-also"></a>另請參閱

- [作法：建立狀態機器工作流程](how-to-create-a-state-machine-workflow.md)
- [StateMachine 活動設計工具](/visualstudio/workflow-designer/statemachine-activity-designer)
- [狀態活動設計工具](/visualstudio/workflow-designer/state-activity-designer)
- [FinalState 活動設計工具](/visualstudio/workflow-designer/finalstate-activity-designer)
- [轉換活動設計工具](/visualstudio/workflow-designer/transition-activity-designer)
