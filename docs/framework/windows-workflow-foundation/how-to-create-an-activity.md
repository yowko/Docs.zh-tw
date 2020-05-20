---
title: HOW TO：建立活動
description: 本文說明如何在 Workflow Foundation 中建立兩個活動：一個使用程式碼來執行其邏輯，另一個則是使用其他活動所定義。
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419586"
---
# <a name="how-to-create-an-activity"></a>HOW TO：建立活動

活動是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的行為核心單位。 活動的執行邏輯可以實作在 Managed 程式碼中，或是使用其他活動來實作。 本主題示範如何建立兩個活動。 第一個活動是簡單的活動，使用程式碼來實作其執行邏輯。 第二個活動的實作則是使用其他活動來定義。 教學課程中的下列步驟將會使用這些活動。

> [!NOTE]
> 若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。

## <a name="create-the-activity-library-project"></a>建立活動程式庫專案

1. 開啟 Visual Studio，然後**New**  >  從 [檔案] 功能表中**選擇 [** 新增**專案**]。

2. 在 [**新增專案**] 對話方塊的 [**已安裝**] 類別之下，選取 [ **Visual c #**  >  **工作流程**] （或 [ **Visual Basic**  >  **工作流程**]）。

    > [!NOTE]
    > 如果您沒有看到 [**工作流程**] 範本類別目錄，您可能需要安裝 Visual Studio 的**Windows Workflow Foundation**元件。 選擇 [**新增專案**] 對話方塊左側的 [**開啟 Visual Studio 安裝程式**] 連結。 在 Visual Studio 安裝程式中，選取 [**個別元件**] 索引標籤。然後，在 [**開發活動**] 類別底下，選取 [ **Windows Workflow Foundation** ] 元件。 選擇 [**修改**] 以安裝元件。

3. 選取 [**活動程式庫**] 專案範本。 在 [名稱]**** 方塊中輸入 `NumberGuessWorkflowActivities`，然後按一下 [確定]****。

4. 在 **[方案總管]** 中的 **[Activity1.xaml]** 上按一下滑鼠右鍵，並選擇 **[刪除]**。 按一下 **[確定]** 以確認。

## <a name="create-the-readint-activity"></a>建立 ReadInt 活動

1. 從 [**專案**] 功能表中選擇 [**加入新專案**]。

2. 在 [**已安裝**的  >  **通用專案**] 節點中，選取 [**工作流程**]。 從 [**工作流程**] 清單中選取 [程式**代碼活動**]。

3. 在 [名稱]**** 方塊中輸入 `ReadInt`，然後按一下 [加入]****。

4. 以下列定義取代現有的 `ReadInt` 定義。

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt` 活動衍生自 <xref:System.Activities.NativeActivity%601>，而不是程式碼活動範本預設的 <xref:System.Activities.CodeActivity>。 如果活動提供單一結果 (透過 <xref:System.Activities.CodeActivity%601> 引數公開)，則可使用 <xref:System.Activities.Activity%601.Result%2A>，但 <xref:System.Activities.CodeActivity%601> 不支援使用書籤，因而會使用 <xref:System.Activities.NativeActivity%601>。

## <a name="create-the-prompt-activity"></a>建立提示活動

1. 按**Ctrl** + **Shift** + **B**以建立專案。 建置專案可將此專案中的 `ReadInt` 活動用來建置此步驟中的自訂活動。

2. 從 [**專案**] 功能表中選擇 [**加入新專案**]。

3. 在 [**已安裝**的  >  **通用專案**] 節點中，選取 [**工作流程**]。 從 **[工作流程]** 清單中選取 **[活動]**。

4. 在 [名稱]**** 方塊中輸入 `Prompt`，然後按一下 [加入]****。

5. 按兩下 [Prompt]，**方案總管**中的**xaml**將它顯示在設計工具中（如果尚未顯示）。

6. 在活動設計工具的左下方按一下 **[引數]**，以顯示 **[引數]** 窗格。

7. 按一下 **[建立引數]**。

8. `BookmarkName`在 [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [ **In** ]，從 [**引數型**別] 下拉式清單中選取 [**字串**]，然後按下**enter**以儲存引數。

9. 按一下 **[建立引數]**。

10. 在 `Result` 新加入之引數底下的 [**名稱**] 方塊中輸入 `BookmarkName` ，從 [**方向**] 下拉式清單中選取 [ **Out** ]，選取 [自**變數型**別] 下拉式清單中的 [ **Int32** ]，然後按**enter**。

11. 按一下 **[建立引數]**。

12. `Text`在 [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [ **In** ]，從 [**引數型**別] 下拉式清單中選取 [**字串**]，然後按下**enter**以儲存引數。

     這三個引數會繫結至下列步驟中加入至 <xref:System.Activities.Statements.WriteLine> 活動之 `ReadInt` 和 `Prompt` 活動的對應引數。

13. 在活動設計工具的左下方按一下 **[引數]**，以關閉 **[引數]** 窗格。

14. 從 [工具箱] 的 [**控制流程**] 區段，將 [**序列**] 活動拖放到 [**提示**] 活動設計**工具**的 [在**此放置活動**] 標籤上。

    > [!TIP]
    > 若 **[工具箱]** 視窗並未顯示，請從 **[檢視]** 功能表中選取 **[工具箱]**。

15. 將 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **Sequence** ] 活動的 [在**此放置活動**] 標籤上。

16. 在 [ **Text** **Text** **Prompt** **WriteLine** `Text` **屬性**] 視窗中輸入 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊，將 [WriteLine] 活動的 [文字] 引數系結至 [提示] 活動的 [text] 引數，然後按兩次**tab**鍵。 這樣會將選項移出屬性外，以關閉 IntelliSense 清單成員視窗並儲存屬性值。 您也可以在 `Text` 活動本身的 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中鍵入，來設定這個屬性。

    > [!TIP]
    > 如果沒有顯示 [**屬性] 視窗**，請從 [**視圖**] 功能表中選取 [**屬性視窗]** 。

17. 從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段中，將 [ **ReadInt** ] 活動拖放到 [ **Sequence** ] 活動中，使其遵循 [ **WriteLine** ] 活動。

18. 將**ReadInt**活動的**BookmarkName**引數系結至 [**提示**] 活動的**BookmarkName**引數，方法是在 `BookmarkName` [**屬性] 視窗**中輸入**BookmarkName**引數右邊的 [**輸入 VB 運算式**] 方塊，然後按兩次**tab**鍵以關閉 [IntelliSense 清單成員] 視窗並儲存屬性。

19. 在 [屬性] 視窗中，將 [ **ReadInt** ] 活動的**結果**引數系結至 [**提示**] 活動**的 [結果**] 引數，然後 `Result` 按兩次**Properties Window** **Enter a VB expression** **tab**鍵。 **Result**

20. 按**Ctrl** + **Shift** + **B**以建立方案。

## <a name="next-steps"></a>後續步驟

如需如何使用這些活動來建立工作流程的指示，請參閱教學課程 how [to：建立工作流程](how-to-create-a-workflow.md)中的下一個步驟。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [設計及實作自訂活動](designing-and-implementing-custom-activities.md)
- [消費者入門教學課程](getting-started-tutorial.md)
- [如何：建立工作流程](how-to-create-a-workflow.md)
- [在自訂活動設計工具中使用 ExpressionTextBox](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
