---
title: HOW TO：建立活動
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 8aa6900b26bbe9f77fe0802a7929febe5af61269
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48872953"
---
# <a name="how-to-create-an-activity"></a>HOW TO：建立活動

活動是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的行為核心單位。 活動的執行邏輯可以實作在 Managed 程式碼中，或是使用其他活動來實作。 本主題示範如何建立兩個活動。 第一個活動是簡單的活動，使用程式碼來實作其執行邏輯。 第二個活動的實作則是使用其他活動來定義。 教學課程中的下列步驟將會使用這些活動。

> [!NOTE]
> 若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。

## <a name="create-the-activity-library-project"></a>建立活動程式庫專案

1.  開啟 Visual Studio，然後選擇**的新** > **專案**從**檔案**功能表。

2.  在 **新的專案**對話方塊底下**已安裝**類別目錄中，選取**Visual C#** > **工作流程**(或**Visual Basic** > **流程**)。

    > [!NOTE]
    > 如果您沒有看到**工作流程**範本類別，您可能需要安裝**Windows Workflow Foundation** Visual Studio 的元件。 選擇**開啟的 Visual Studio 安裝程式**左手邊的連結**新的專案**對話方塊。 在 Visual Studio 安裝程式中，選取**個別元件** 索引標籤。然後，在**開發活動**類別目錄中，選取**Windows Workflow Foundation**元件。 選擇**修改**安裝元件。

3. 選取 **活動程式庫**專案範本。 型別`NumberGuessWorkflowActivities`中**名稱**方塊，然後按一下**確定**。

4.  以滑鼠右鍵按一下**Activity1.xaml**中**方案總管**，然後選擇 **刪除**。 按一下 [ **確定** ] 以確認。

## <a name="create-the-readint-activity"></a>建立 ReadInt 活動

1.  選擇**加入新項目**從**專案**功能表。

2.  在 **已安裝** > **通用的項目**節點中，選取**工作流程**。 選取 **程式碼活動**從**工作流程**清單。

3.  型別`ReadInt`成**名稱**方塊，然後按一下**新增**。

4.  以下列定義取代現有的 `ReadInt` 定義。

     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt` 活動衍生自 <xref:System.Activities.NativeActivity%601>，而不是程式碼活動範本預設的 <xref:System.Activities.CodeActivity>。 如果活動提供單一結果 (透過 <xref:System.Activities.CodeActivity%601> 引數公開)，則可使用 <xref:System.Activities.Activity%601.Result%2A>，但 <xref:System.Activities.CodeActivity%601> 不支援使用書籤，因而會使用 <xref:System.Activities.NativeActivity%601>。

## <a name="create-the-prompt-activity"></a>建立提示活動

1.  按下**Ctrl**+**Shift**+**B**來建置專案。 建置專案可將此專案中的 `ReadInt` 活動用來建置此步驟中的自訂活動。

2.  選擇**加入新項目**從**專案**功能表。

3.  在 **已安裝** > **通用的項目**節點中，選取**工作流程**。 選取 **活動**從**工作流程**清單。

4.  型別`Prompt`成**名稱**方塊，然後按一下**新增**。

5.  按兩下**Prompt.xaml**中**方案總管 中**如果未顯示在設計工具中顯示它。

6.  按一下 **引數**中要顯示在活動設計工具的左下方**引數**窗格。

7.  按一下  **Vytvořit Argument**。

8.  型別`BookmarkName`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下**Enter**儲存引數。

9. 按一下  **Vytvořit Argument**。

10. 型別`Result`成**名稱**是在新加入的方塊`BookmarkName`引數，選取**Out**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下**Enter**。

11. 按一下  **Vytvořit Argument**。

12. 型別`Text`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下**Enter**儲存引數。

     這三個引數會繫結至下列步驟中加入至 <xref:System.Activities.Statements.WriteLine> 活動之 `ReadInt` 和 `Prompt` 活動的對應引數。

13. 按一下 **引數**關閉的活動設計工具左下角**引數**窗格。

14. 拖曳**順序**活動，從**控制流程**一節**工具箱**拖曳至**活動拖曳到這裏**的標籤**提示**活動設計工具。

    > [!TIP]
    > 如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。

15. 拖曳**WriteLine**活動，從**基本型別**一節**工具箱**拖曳至**活動拖曳到這裏**的標籤**順序**活動。

16. 繫結**文字**引數**WriteLine**活動**文字**引數**提示**活動輸入`Text`到**輸入 C# 運算式**或是**輸入 VB 運算式**方塊中**屬性**視窗，然後再按**索引標籤**索引鍵兩次。 這樣會將選項移出屬性外，以關閉 IntelliSense 清單成員視窗並儲存屬性值。 這個屬性也可以設定輸入`Text`成**輸入 C# 運算式**或是**輸入 VB 運算式**活動本身的方塊。

    > [!TIP]
    > 如果**屬性 視窗**顯示，請選取**屬性視窗**從**檢視**功能表。

17. 拖曳**ReadInt**活動，從**NumberGuessWorkflowActivities**一節**工具箱**並將它放**順序**活動中，讓它遵循**WriteLine**活動。

18. 繫結**BookmarkName**引數**ReadInt**活動**BookmarkName**引數**提示**輸入活動`BookmarkName`成**輸入 VB 運算式**右邊的方塊**BookmarkName**中的引數**屬性 視窗**，然後按  ** 索引標籤**鍵關閉 IntelliSense 清單成員視窗並儲存屬性的兩倍。

19. 繫結**結果**引數**ReadInt**活動**結果**引數**提示**活動輸入`Result`到**輸入 VB 運算式**右邊的方塊**結果**中的引數**屬性 視窗**，然後按下** 索引標籤**鍵兩次。

20. 按下**Ctrl**+**Shift**+**B**建置方案。

## <a name="next-steps"></a>後續步驟

如需如何使用這些活動中，建立工作流程的指示，請參閱下一步在教學課程中，[如何： 建立工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [設計及實作自訂活動](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)
- [快速入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [如何：建立工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [在自訂活動設計工具中使用 ExpressionTextBox](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)