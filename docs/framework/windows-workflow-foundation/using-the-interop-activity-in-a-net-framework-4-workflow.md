---
title: 在 .NET Framework 4 工作流程中使用 Interop 活動
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528106"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>在 .NET Framework 4 工作流程中使用 Interop 活動
使用 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 或 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 建立的活動，可以經由使用 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 活動，在 <xref:System.Activities.Statements.Interop> 工作流程中使用。 本主題提供使用 <xref:System.Activities.Statements.Interop> 活動的概觀。  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop>活動不會顯示在工作流程設計工具工具箱除非工作流程的專案具有其**目標 Framework**設定設為 **.Net Framework 4**或更新版本。  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>在 .NET Framework 4.5 Workflows 中使用 Interop 活動  
 在本主題中，會建立一個 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動程式庫，其中包含 `DiscountCalculator` 活動。 `DiscountCalculator` 會根據購買金額計算折扣，並且由包含 <xref:System.Workflow.Activities.SequenceActivity> 的 <xref:System.Workflow.Activities.PolicyActivity> 組成。  
  
> [!NOTE]
>  在本主題中建立的 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動會使用 <xref:System.Workflow.Activities.PolicyActivity> 實作活動的邏輯。 不需使用自訂的 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動或 <xref:System.Activities.Statements.Interop> 活動，即可在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程中使用規則。 如需範例的使用中的規則[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]而不使用的工作流程<xref:System.Activities.Statements.Interop>活動，請參閱[.NET Framework 4.5 中的原則活動](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md)範例。  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>若要建立 .NET Framework 3.5 活動程式庫專案  
  
1.  開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，然後選取**新增**，然後**專案...** 從**檔案**功能表。  
  
2.  依序展開**其他專案類型**中的節點**已安裝的範本**窗格，然後選取**Visual Studio 方案**。  
  
3.  選取 **空白方案**從**Visual Studio 方案**清單。 型別`PolicyInteropDemo`中**名稱**方塊，然後按一下**確定**。  
  
4.  以滑鼠右鍵按一下**PolicyInteropDemo**中**方案總管**，然後選取**新增**，然後**新專案...**.  
  
    > [!TIP]
    >  如果**方案總管**視窗未顯示，選取**方案總管**從**檢視**功能表。  
  
5.  在 **已安裝的範本**清單中，選取**Visual C#** ，然後**流程**。 選取  **.NET Framework 3.5**從.NET Framework 版本下拉式清單中，然後選取**Workflow Activity Library**從**範本**清單。  
  
6.  型別`PolicyActivityLibrary`中**名稱**方塊，然後按一下**確定**。  
  
7.  以滑鼠右鍵按一下**Activity1.cs**中**方案總管**，然後選取**刪除**。 按一下 [ **確定** ] 以確認。  
  
#### <a name="to-create-the-discountcalculator-activity"></a>若要建立 DiscountCalculator 活動  
  
1.  以滑鼠右鍵按一下**PolicyActivityLibrary**中**方案總管**，然後選取**新增**，然後**活動...**.  
  
2.  選取 **活動 （程式碼分開置放）** 從**Visual C# 項目**清單。 型別`DiscountCalculator`中**名稱**方塊，然後按一下**確定**。  
  
3.  以滑鼠右鍵按一下**DiscountCalculator.xoml**中**方案總管**，然後選取**檢視程式碼**。  
  
4.  將下列三個屬性加入至 `DiscountCalculator` 類別。  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  以滑鼠右鍵按一下**DiscountCalculator.xoml**中**方案總管**，然後選取**檢視表設計工具**。  
  
6.  拖曳**原則**活動，從**Windows Workflow v3.0**一節**工具箱**並將它放**DiscountCalculator**活動.  
  
    > [!TIP]
    >  如果**工具箱**視窗未顯示，選取**工具箱**從**檢視**功能表。  
  
#### <a name="to-configure-the-rules"></a>若要設定規則  
  
1.  按一下 新增**原則**來選取它，如果尚未選取的活動。  
  
2.  按一下  **RuleSetReference**中的屬性**屬性**視窗來加以選取，然後按一下屬性右邊的省略符號按鈕。  
  
    > [!TIP]
    >  如果**屬性**看不到視窗中，選擇**屬性視窗**從**檢視**功能表。  
  
3.  選取**按一下 [新增]...**.  
  
4.  按一下 **新增規則**。  
  
5.  輸入下列運算式**條件** 方塊中。  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  輸入下列運算式**Then 動作** 方塊中。  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  按一下 **新增規則**。  
  
8.  輸入下列運算式**條件** 方塊中。  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. 輸入下列運算式**Then 動作** 方塊中。  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. 按一下 **新增規則**。  
  
11. 輸入下列運算式**條件** 方塊中。  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. 輸入下列運算式**Then 動作** 方塊中。  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. 輸入下列運算式**Else 動作** 方塊中。  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. 按一下 [ **[確定]** 以關閉**規則集編輯器**] 對話方塊。  
  
15. 請確認新建立<xref:System.Workflow.Activities.Rules.RuleSet>中選取**名稱**清單，然後按**確定**。  
  
16. 按下 CTRL+SHIFT+B 以建置方案。  
  
 下列程式碼範例顯示在本程序中加入至 `DiscountCalculator` 活動的規則。  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 執行 <xref:System.Workflow.Activities.PolicyActivity> 時，這三個規則會評估並修改 `Subtotal` 活動的 `DiscountPercent`、`Total` 及 `DiscountCalculator` 屬性值，以計算所需的折扣。  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>搭配使用 DiscountCalculator 活動與 Interop 活動  
 若要在 `DiscountCalculator` 工作流程內使用 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 活動，需使用 <xref:System.Activities.Statements.Interop> 活動。 本節中會建立兩個工作流程 (其中一個使用程式碼，另一個使用工作流程設計工具)，示範如何搭配使用 <xref:System.Activities.Statements.Interop> 活動與 `DiscountCalculator` 活動。 兩個工作流程會使用同樣的主應用程式。  
  
#### <a name="to-create-the-host-application"></a>若要建立主應用程式  
  
1.  以滑鼠右鍵按一下**PolicyInteropDemo**中**方案總管**，然後選取**新增**，然後**新專案...**.  
  
2.  請確認 **.NET Framework 4.5**已在.NET Framework 版本下拉式清單中，選取，然後選取**工作流程主控台應用程式**從**Visual C# 項目**清單。  
  
3.  型別`PolicyInteropHost`成**名稱**方塊，然後按一下**確定**。  
  
4.  以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**屬性**。  
  
5.  在 **目標 framework**下拉式清單中，變更選取範圍 **.NET Framework 4 Client Profile**來 **.NET Framework 4.5**。 按一下 **是**確認。  
  
6.  以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**加入參考...**.  
  
7.  選取  **PolicyActivityLibrary**從**專案**索引標籤，然後按一下**確定**。  
  
8.  以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**加入參考...**.  
  
9. 選取  **System.Workflow.Activities**， **System.Workflow.ComponentModel**，然後**System.workflow.componentmodel**從 **.NET**索引標籤，然後按一下**確定**。  
  
10. 以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**設定為啟始專案**。  
  
11. 按下 CTRL+SHIFT+B 以建置方案。  
  
### <a name="using-the-interop-activity-in-code"></a>在程式碼中使用 Interop 活動  
 在此範例中，會使用包含 <xref:System.Activities.Statements.Interop> 活動和 `DiscountCalculator` 活動的程式碼建立工作流程定義。 使用 <xref:System.Activities.WorkflowInvoker> 叫用這個工作流程，使用 <xref:System.Activities.Statements.WriteLine> 活動則會將規則評估的結果寫入至主控台。  
  
##### <a name="to-use-the-interop-activity-in-code"></a>若要在程式碼中使用 Interop 活動  
  
1.  以滑鼠右鍵按一下**Program.cs**中**方案總管**，然後選取**檢視程式碼**。  
  
2.  將下列 `using` 陳述式加入至檔案最上方。  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  移除 `Main` 方法的內容，並以下列程式碼取代。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  在名為 `Program` 的 `CalculateDiscountUsingCodeWorkflow` 類別中建立新方法，其中包含下列程式碼。  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  `Subtotal` 活動的 `DiscountPercent`、`Total` 和 `DiscountCalculator` 屬性會以 <xref:System.Activities.Statements.Interop> 活動的引數形式出現，並且繫結至 <xref:System.Activities.Statements.Interop> 活動之 <xref:System.Activities.Statements.Interop.ActivityProperties%2A> 集合的本機工作流程變數。 `Subtotal` 會加入成為 <xref:System.Activities.ArgumentDirection.In> 引數，因為 `Subtotal` 資料會流入 <xref:System.Activities.Statements.Interop> 活動中，此外會加入 `DiscountPercent` 和 `Total` 做為 <xref:System.Activities.ArgumentDirection.Out> 引數，因為它們的資料會流出 <xref:System.Activities.Statements.Interop> 活動。 請注意，兩個 <xref:System.Activities.ArgumentDirection.Out> 引數是以 `DiscountPercentOut` 和 `TotalOut` 這兩個名稱加入，表示它們代表 <xref:System.Activities.ArgumentDirection.Out> 引數。 `DiscountCalculator` 型別會指定為 <xref:System.Activities.Statements.Interop> 活動的 <xref:System.Activities.Statements.Interop.ActivityType%2A>。  
  
5.  按 CTRL+F5 建置並執行應用程式。 將 `Subtotal` 的值替換成不同的值，測試出 `DiscountCalculator` 活動所提供的不同折扣層級。  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>在工作流程設計工具中使用 Interop 活動  
 在這個範例中，會使用工作流程設計工具建立工作流程。 這個工作流程與上一個範例中的工作流程具有相同的功能，但不會使用 <xref:System.Activities.Statements.WriteLine> 活動顯示折扣，而是由主應用程式在工作流程完成時擷取並顯示折扣資訊。 同時，這個工作流程不使用區域工作流程變數來包含資料，而是在工作流程設計工具中建立引數，並在叫用工作流程時從主機傳入值。  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>若要使用工作流程設計工具建立的工作流程裝載 PolicyActivity  
  
1.  以滑鼠右鍵按一下**Workflow1.xaml**中**方案總管**，然後選取**刪除**。 按一下 [ **確定** ] 以確認。  
  
2.  以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**新增**，**新項目...**.  
  
3.  依序展開**Visual C# 項目**節點，然後選取**工作流程**。 選取 **活動**從**Visual C# 項目**清單。  
  
4.  型別`DiscountWorkflow`成**名稱**方塊，然後按一下**新增**。  
  
5.  按一下 **引數**按鈕以顯示工作流程設計工具左下角**引數**窗格。  
  
6.  按一下  **Vytvořit Argument**。  
  
7.  型別`Subtotal`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Double**從**引數型別**下拉式清單中，然後按下 ENTER 儲存引數。  
  
    > [!NOTE]
    >  如果**雙**不是處於**引數型別**下拉式清單中，選取**Vyhledat Typy...**，輸入`System.Double`中**型別名稱**方塊，然後按一下**確定**。  
  
8.  按一下  **Vytvořit Argument**。  
  
9. 型別`DiscountPercent`成**名稱**方塊中，選取**出**從**方向**下拉式清單中，選取**Double**從**引數型別**下拉式清單中，然後按下 ENTER 儲存引數。  
  
10. 按一下  **Vytvořit Argument**。  
  
11. 型別`Total`成**名稱**方塊中，選取**出**從**方向**下拉式清單中，選取**Double**從**引數型別**下拉式清單中，然後按下 ENTER 儲存引數。  
  
12. 按一下 **引數**按鈕以關閉工作流程設計工具左下角**引數**窗格。  
  
13. 拖曳**順序**活動，從**控制流程**一節**工具箱**拖放到工作流程設計工具介面。  
  
14. 拖曳**Interop**活動，從**移轉**一節**工具箱**並將它放**順序**活動。  
  
15. 按一下  **Interop**活動上的**按一下即可瀏覽...** 標籤中，輸入**DiscountCalculator**中**型別名稱**方塊，然後按一下**確定**。  
  
    > [!NOTE]
    >  將 <xref:System.Activities.Statements.Interop> 活動加入至工作流程中，並將 `DiscountCalculator` 型別指定為其 <xref:System.Activities.Statements.Interop.ActivityType%2A> 時，<xref:System.Activities.Statements.Interop> 活動會公開三個 <xref:System.Activities.ArgumentDirection.In> 引數和三個 <xref:System.Activities.ArgumentDirection.Out> 引數 (代表 `DiscountCalculator` 活動的三個公用屬性)。 <xref:System.Activities.ArgumentDirection.In>引數具有相同名稱的三個公用屬性和三個<xref:System.Activities.ArgumentDirection.Out>引數具有相同名稱時**出**附加至屬性名稱。 在下列步驟中，在前述步驟中建立的工作流程引數會繫結至 <xref:System.Activities.Statements.Interop> 活動的引數。  
  
16. 型別`DiscountPercent`成**輸入 VB 運算式**右邊的方塊**Discountpercent**屬性並按下 TAB 鍵。  
  
17. 型別`Subtotal`成**輸入 VB 運算式**右邊的方塊**Subtotal**屬性並按下 TAB 鍵。  
  
18. 型別`Total`成**輸入 VB 運算式**右邊的方塊**TotalOut**屬性並按下 TAB 鍵。  
  
19. 以滑鼠右鍵按一下**Program.cs**中**方案總管**，然後選取**檢視程式碼**。  
  
20. 將下列 `using` 陳述式加入至檔案最上方。  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. 註解 `CalculateDiscountInCode` 方法中對 `Main` 方法的呼叫，然後加入下列程式碼。  
  
    > [!NOTE]
    >  如果您未遵循前述程序，而出現預設的 `Main` 程式碼，請以下列程式碼取代 `Main` 的內容。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. 在名為 `Program` 的 `CalculateDiscountUsingDesignerWorkflow` 類別中建立新方法，其中包含下列程式碼。  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. 按 CTRL+F5 建置並執行應用程式。 若要指定不同的 `Subtotal` 金額，請變更下列程式碼中 `SubtotalValue` 的值。  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>規則功能概觀  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 規則引擎可支援以優先順序為主的方式處理規則，並且支援向前鏈結。 規則可針對單一項目或集合中之項目進行評估。 如需規則概觀與特定規則功能的詳細資訊，請參閱下表。  
  
|規則功能|文件|  
|-------------------|-------------------|  
|規則概觀|[Windows Workflow Foundation Rules Engine 簡介](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|RuleSet|[在工作流程中使用 Ruleset](https://go.microsoft.com/fwlink/?LinkId=178516)和 <xref:System.Workflow.Activities.Rules.RuleSet>|  
|規則評估|[Ruleset 中的規則評估](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|規則鏈結|[向前鏈結控制項](https://go.microsoft.com/fwlink/?LinkId=178518)和[規則的向前鏈結](https://go.microsoft.com/fwlink/?LinkId=178519)|  
|處理規則中的集合|[處理規則中的集合](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|使用 PolicyActivity|[使用 PolicyActivity 活動](https://go.microsoft.com/fwlink/?LinkId=178521)和 <xref:System.Workflow.Activities.PolicyActivity>|  
  
 在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中建立的工作流程不會使用 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 提供的所有規則功能，例如宣告式活動條件及條件式活動 (例如 <xref:System.Workflow.Activities.ConditionedActivityGroup> 和 <xref:System.Workflow.Activities.ReplicatorActivity>)。 如有必要，這個功能可供以 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 和 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 建立的工作流程使用。 如需詳細資訊，請參閱 <<c0> [ 移轉指引](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)。
