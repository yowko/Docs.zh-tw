---
title: 作法：建立狀態機器工作流程
description: 本文所建立的工作流程會使用內建活動，例如 StateMachine 活動和自訂活動。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 9df911779422ca2710686963a040a95258db8891
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248915"
---
# <a name="how-to-create-a-state-machine-workflow"></a>作法：建立狀態機器工作流程

工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題逐步解說如何建立工作流程，此工作流程會使用活動等內建活動 <xref:System.Activities.Statements.StateMachine> ，以及先前的 how [To：建立活動](how-to-create-an-activity.md) 主題的自訂活動。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
> 「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成 [如何：建立活動](how-to-create-an-activity.md)。  
  
> [!NOTE]
> 若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1. 以滑鼠右鍵按一下 **方案總管** 中的 **[numberguessworkflowactivities]** **，然後選取 [** 新增]、[**新增專案**]。  
  
2. 在 [ **已安裝** 的 **一般專案** ] 節點中，選取 [ **工作流程**]。 從 **[工作流程]** 清單中選取 **[活動]**。  
  
3. `StateMachineNumberGuessWorkflow`在 [**名稱**] 方塊中輸入，然後按一下 [**新增**]。  
  
4. 從 [**工具箱**] 的 [**狀態機器**] 區段，將 [ **StateMachine** ] 活動拖放到工作流程設計介面上的 [在 **此放置活動**] 標籤。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1. 按兩下 **方案總管** 中的 [ **StateMachineNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。  
  
2. 在工作流程設計工具的左下方按一下 [ **引數** ]，以顯示 [ **引數** ] 窗格。  
  
3. 按一下 **[建立引數]**。  
  
4. 在 `MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [加入]，從 [**引數類型**] 下拉式清單 **中** 選取 [ **Int32** ]，然後按 enter 儲存引數。  
  
5. 按一下 **[建立引數]**。  
  
6. 在 `Turns` 新加入之引數底下的 [**名稱**] 方塊中輸入 `MaxNumber` ，從 [**方向**] 下拉式清單 **中** 選取 [從自 **變數類型**] 下拉式清單選取 [ **Int32** ]，然後按 enter 鍵。  
  
7. 在活動設計工具的左下方按一下 **[引數]**，以關閉 **[引數]** 窗格。  
  
8. 在工作流程設計工具的左下方按一下 [ **變數** ]，以顯示 [ **變數** ] 窗格。  
  
9. 按一下 **[建立變數]**。  
  
    > [!TIP]
    > 如果未顯示 [ **建立變數** ] 方塊，請按一下 <xref:System.Activities.Statements.StateMachine> 工作流程設計工具介面上的活動加以選取。  
  
10. 在 `Guess` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
11. 按一下 **[建立變數]**。  
  
12. 在 `Target` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
13. 在活動設計工具的左下方按一下 **[變數]**，以關閉 **[變數]** 窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1. 按一下 [ **State1** ] 加以選取。 在 [ **屬性] 視窗** 中，將 [ **DisplayName** ] 變更為 `Initialize Target` 。  
  
    > [!TIP]
    > 如果未顯示 [**屬性] 視窗**，請從 [ **View** ] 功能表選取 [**屬性視窗]** 。  
  
2. 在工作流程設計工具中，按兩下剛剛重新命名的 [ **初始化目標** ] 狀態，將其展開。  
  
3. 從 [**工具箱**] 的 [**基本**] 區段中，將 [**指派**] 活動拖放到狀態的 [**專案**] 區段上。 在 `Target` [ **到** ] 方塊中輸入，並在 [ **輸入 c # 運算式** ] 或 [ **輸入 VB 運算式** ] 方塊中輸入下列運算式。  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > 若 **[工具箱]** 視窗並未顯示，請從 **[檢視]** 功能表中選取 **[工具箱]**。  
  
4. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，回到工作流程設計工具中的整體狀態機器查看。  
  
5. 將 [ **狀態** ] 活動從 [工具箱] 的 [ **狀態機器** ] 區段拖曳至工作流程設計 **工具** ，並將其停留在 [ **初始化目標** ] 狀態。 請注意，當新狀態超過時，會在 **初始化目標** 狀態周圍出現四個三角形。 將新狀態放在 [ **初始化目標** ] 狀態正下方的三角形上。 這會將新狀態放入工作流程，並建立從 **初始化目標** 狀態到新狀態的轉換。  
  
6. 按一下 [ **State1** ] 加以選取、將 [ **DisplayName** ] 變更為 `Enter Guess` ，然後按兩下工作流程設計工具中的狀態，將其展開。  
  
7. 將 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [**專案**] 區段上。  
  
8. 在 [ **WriteLine**] 的 [ **Text** ] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. 將 [**指派**] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態 **的 [結束] 區段。**  
  
10. 在 [到] 方塊中輸入 `Turns` ，然後 **To** `Turns + 1` 在 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入。  
  
11. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，回到工作流程設計工具中的整體狀態機器查看。  
  
12. 從 [**工具箱**] 的 [**狀態機器**] 區段中，將 [ **FinalState** ] 活動移至 [**進入猜測**] 狀態，然後將它放在 [**進入猜測**] 狀態右邊的三角形上，以在 **enter 猜測** 與 **FinalState** 之間建立轉換。  
  
13. 轉換的預設名稱是 **T2**。 按一下工作流程設計工具中的轉換加以選取，並設定其 **DisplayName** 以 **猜測正確**。 然後，按一下並選取 [ **FinalState**]，並將其拖曳至右側，讓完整的轉換名稱不會有空間可顯示，而不會覆迭兩個狀態的任一個。 這將可以更容易完成教學課程中的其他步驟。  
  
14. 在工作流程設計工具中，按兩下剛剛重新命名的 [ **猜測正確** ] 轉換，將其展開。  
  
15. 從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段中拖曳 **ReadInt** 活動，放在轉換的 [**觸發** 程式] 區段中。  
  
16. 在 [ **ReadInt** ] 活動的 [**屬性] 視窗** 中，在 `"EnterGuess"` [ **BookmarkName** ] 屬性值方塊中輸入包含引號，然後在 `Guess` [**結果**] 屬性值方塊中輸入。  
  
17. 在 [ **猜測正確** 轉換的 **條件** ] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，回到工作流程設計工具中的整體狀態機器查看。  
  
    > [!NOTE]
    > 收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。 針對這項轉換，如果使用者 `Guess` 符合隨機產生的 `Target` ，則控制權會傳遞至 **FinalState** ，且工作流程會完成。  
  
19. 根據猜測是否正確，工作流程應轉換為 **FinalState** ，或轉換回 **進入猜測** 狀態以進行另一次嘗試。 這兩個轉換都會共用等待使用者猜測透過 **ReadInt** 活動接收的相同觸發程式。 這稱為共用轉換。 若要建立共用轉換，請按一下表示 **猜測正確** 轉換開始的圓形，並將它拖曳至所需的狀態。 在此情況下，轉換是自我轉換，所以請將 [ **猜測正確** ] 轉換的起點拖放回 [ **進入猜測** ] 狀態的底部。 建立轉換之後，請在工作流程設計工具中選取它，並將其 **DisplayName** 屬性設定為 **猜測不正確**。  
  
    > [!NOTE]
    > 您也可以在轉換設計工具中，按一下 [轉換設計工具] 底部的 [ **加入共用觸發程式轉換** ]，然後從 [ **要連接的可用狀態]** 下拉式清單中選取所需的目標狀態，藉以建立共用轉換。  
  
    > [!NOTE]
    > 請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。 由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。  
  
20. 在工作流程設計工具中按兩下 [ **猜測不正確** ] 轉換，將其展開。 請注意，**觸發** 程式已設定為 **猜測正確** 轉換所使用的相同 **ReadInt** 活動。  
  
21. 在 [ **條件** ] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. 從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **If** ] 活動拖放到轉換的 [**動作**] 區段中。  
  
23. 在 [ **If** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    Guess < Target
    ```  
  
24. 將兩個 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **If** ] 活動的 [ **Then** ] 區段，另一個則是在 [ **Else** ] 區段中。  
  
25. 按一下 [ **Then** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. 按一下 [ **Else** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，回到工作流程設計工具中的整體狀態機器查看。  
  
     下列範例示範完成的工作流程。  
  
     ![顯示已完成狀態機器工作流程的圖例。](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1. 按 CTRL+SHIFT+B 建置解決方案。  
  
     如需如何執行工作流程的指示，請參閱下一個主題 [：如何：執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成如何：使用不同的工作流程樣式來[執行工作流程](how-to-run-a-workflow.md)步驟，並且想要使用此步驟中的狀態機器工作流程來執行它，請直接跳至 how [To：執行工作流程](how-to-run-a-workflow.md)的 [[建立和執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)] 區段。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [作法：建立活動](how-to-create-an-activity.md)
- [作法：執行工作流程](how-to-run-a-workflow.md)
