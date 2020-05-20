---
title: HOW TO：建立狀態機器工作流程
description: 本文所建立的工作流程會使用內建活動，例如 StateMachine 活動和自訂活動。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8a9342c07c15d65df0310c0cb35b4b2c6f2ba686
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419651"
---
# <a name="how-to-create-a-state-machine-workflow"></a>HOW TO：建立狀態機器工作流程
工作流程可以從內建活動建構，也可以從自訂活動建構。 本主題將逐步說明如何建立使用內建活動（例如活動）的工作流程， <xref:System.Activities.Statements.StateMachine> 以及先前[如何：建立活動](how-to-create-an-activity.md)主題中的自訂活動。 此工作流程會以數字猜測遊戲為模型。  
  
> [!NOTE]
> 「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成本主題，您必須先完成[如何：建立活動](how-to-create-an-activity.md)。  
  
> [!NOTE]
> 若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow"></a>建立工作流程  
  
1. 以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowactivities]** ，然後選取 [**加入**]、[**新增專案**]。  
  
2. 在 [**已安裝**的**通用專案**] 節點中，選取 [**工作流程**]。 從 **[工作流程]** 清單中選取 **[活動]**。  
  
3. `StateMachineNumberGuessWorkflow`在 [**名稱**] 方塊中輸入，然後按一下 [**新增**]。  
  
4. 從 [**工具箱**] 的 [**狀態機器**] 區段中，將 [ **StateMachine** ] 活動拖放到工作流程設計介面上的 [在**此放置活動**] 標籤上。  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>若要建立工作流程變數和引數  
  
1. 按兩下**方案總管**中的 [ **StateMachineNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。  
  
2. 在工作流程設計工具的左下方按一下 [**引數**]，以顯示 [**引數**] 窗格。  
  
3. 按一下 **[建立引數]**。  
  
4. 在 `MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [In]，選取 [自**變數型**別] 下拉式清單**中**的 [ **Int32** ]，然後按下 enter 以儲存引數。  
  
5. 按一下 **[建立引數]**。  
  
6. 在 `Turns` 新加入的引數下方輸入 [**名稱**] 方塊 `MaxNumber` ，從 [**方向**] 下拉式清單中選取 [ **Out** ]，選取 [自**變數型**別] 下拉式清單中的 [ **Int32** ]，然後按 enter。  
  
7. 在活動設計工具的左下方按一下 **[引數]**，以關閉 **[引數]** 窗格。  
  
8. 按一下工作流程設計工具左下方的 [**變數**]，以顯示 [**變數**] 窗格。  
  
9. 按一下 **[建立變數]**。  
  
    > [!TIP]
    > 如果沒有顯示 [**建立變數**] 方塊，請按一下 <xref:System.Activities.Statements.StateMachine> 工作流程設計工具介面上的活動加以選取。  
  
10. 在 `Guess` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
11. 按一下 **[建立變數]**。  
  
12. 在 `Target` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。  
  
13. 在活動設計工具的左下方按一下 **[變數]**，以關閉 **[變數]** 窗格。  
  
### <a name="to-add-the-workflow-activities"></a>若要加入工作流程活動  
  
1. 按一下 [ **State1** ] 加以選取。 在 [**屬性] 視窗**中，將 [ **DisplayName** ] 變更為 `Initialize Target` 。  
  
    > [!TIP]
    > 如果沒有顯示 [**屬性] 視窗**，請從 [**視圖**] 功能表中選取 [**屬性視窗]** 。  
  
2. 在工作流程設計工具中，按兩下新重新命名的 [**初始化目標**] 狀態，將它展開。  
  
3. 將 [ **Assign** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [**專案**] 區段上。 在 [到] 方塊中輸入 `Target` ，並在 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入下列運算式。 **To**  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > 若 **[工具箱]** 視窗並未顯示，請從 **[檢視]** 功能表中選取 **[工具箱]**。  
  
4. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。  
  
5. 將 [ **state** ] 活動從 [工具箱] 的 [**狀態機器**] 區段拖曳至工作流程設計**工具**，並將它放在 [**初始化目標**] 狀態上。 請注意，當新狀態超過時，會在**初始化目標**狀態周圍出現四個三角形。 將新狀態放置在 [**初始化目標**] 狀態正下方的三角形上。 這會將新的狀態放到工作流程上，並建立從**初始化目標**狀態到新狀態的轉換。  
  
6. 按一下 [ **State1** ] 加以選取，將 [ **DisplayName** ] 變更為 `Enter Guess` ，然後在工作流程設計工具中按兩下該狀態加以展開。  
  
7. 將 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [**專案**] 區段上。  
  
8. 在 [ **WriteLine**] 的 [ **Text** ] 屬性方塊中輸入下列運算式。  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. 將 [ **Assign** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [結束 **] 區段。**  
  
10. 在 `Turns` [**到**] 方塊中輸入，然後 `Turns + 1` 在 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中。  
  
11. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。  
  
12. 從 [**工具箱**] 的 [**狀態機器**] 區段中，將 [ **FinalState** ] 活動拖曳到 [**輸入猜測**] 狀態，然後將它放置到出現在 [**輸入猜測**] 狀態右邊的三角形上，以在 [**輸入猜測**] 與 [ **FinalState**] 之間建立轉換。  
  
13. 轉換的預設名稱為**T2**。 按一下工作流程設計工具中的轉換來選取它，並將其**DisplayName**設定為 [**猜測正確**]。 然後，按一下並選取**FinalState**，並將其拖曳至右側，讓完整轉換名稱顯示空間，而不會覆迭兩個狀態的其中一個。 這將可以更容易完成教學課程中的其他步驟。  
  
14. 在工作流程設計工具中，按兩下新重新命名的 [**猜測正確**] 轉換，將其展開。  
  
15. 從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段中，將 [ **ReadInt** ] 活動拖放到轉換的 [**觸發**程式] 區段中。  
  
16. 在 [ **ReadInt** ] 活動的 [**屬性] 視窗**中，在 `"EnterGuess"` [ **BookmarkName**屬性值] 方塊中輸入包含引號，然後在 `Guess` [**結果**] 屬性值方塊中輸入  
  
17. 在 [**猜測正確**轉換的**條件**] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。  
  
    > [!NOTE]
    > 收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。 在此轉換中，如果使用者 `Guess` 與隨機產生的相符 `Target` ，則控制權會傳遞至**FinalState** ，而且工作流程會完成。  
  
19. 視猜測是否正確而定，工作流程應該轉換成**FinalState** ，或回到另一個 Try 的**Enter 猜測**狀態。 這兩個轉換共用的觸發程式，會等待使用者透過**ReadInt**活動收到猜測。 這稱為共用轉換。 若要建立共用轉換，請按一下表示 [**猜測正確**] 轉換開始的圓形，然後將它拖曳至想要的狀態。 在此情況下，轉換是一種自我轉換，因此請將**猜測正確**轉換的起點拖放回 [**進入猜測**] 狀態的底部。 建立轉換之後，請在工作流程設計工具中選取它，並將其**DisplayName**屬性設定為 [**猜測不正確**]。  
  
    > [!NOTE]
    > 您也可以從轉換設計工具內建立共用轉換，方法是按一下轉換設計工具底部的 [**新增共用觸發程式轉換**]，然後從 [**可用的狀態]** 下拉式選單選取想要的目標狀態。  
  
    > [!NOTE]
    > 請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。 由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。  
  
20. 在工作流程設計工具中按兩下 [**猜測不正確**] 轉換，將其展開。 請注意，此**觸發**程式已設定為「**猜測正確**」轉換所使用的相同**ReadInt**活動。  
  
21. 在 [**條件**] 屬性值方塊中輸入下列運算式。  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. 從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **If** ] 活動拖放到轉換的 [**動作**] 區段中。  
  
23. 在 [ **If** ] 活動的 [ **Condition** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    Guess < Target
    ```  
  
24. 將兩個 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **if** ] 活動的 [ **Then** ] 區段，其中一個是在 [ **Else** ] 區段中。  
  
25. 按一下 [ **Then** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. 按一下 [ **Else** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. 在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。  
  
     下列範例示範完成的工作流程。  
  
     ![顯示已完成狀態機器工作流程的圖例。](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>若要建置工作流程  
  
1. 按 CTRL+SHIFT+B 建置解決方案。  
  
     如需有關如何執行工作流程的指示，請參閱下一個主題[：如何：執行工作流程](how-to-run-a-workflow.md)。 如果您已經完成如何：以不同的工作流程樣式[執行工作流程](how-to-run-a-workflow.md)步驟，而且想要使用此步驟中的狀態機器工作流程執行它，請直接跳至[如何：執行工作流程](how-to-run-a-workflow.md)中的[建立並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation 程式設計](programming.md)
- [設計工作流程](designing-workflows.md)
- [消費者入門教學課程](getting-started-tutorial.md)
- [如何：建立活動](how-to-create-an-activity.md)
- [如何：執行工作流程](how-to-run-a-workflow.md)
