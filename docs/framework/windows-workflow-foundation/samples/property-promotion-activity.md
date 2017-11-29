---
title: "屬性促銷活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd8356927ad7cb4c24cc278fcb901cc543c6d7b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="property-promotion-activity"></a>屬性促銷活動
此範例提供了端對端方案，此方案會將 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 提升功能直接整合到工作流程撰寫經驗。 將會提供組態元素、工作流程活動、可簡化使用提升功能之工作流程延伸模組的集合。 此外，此範例也包含一個簡單的工作流程，可示範如何使用這個集合。  
  
> [!NOTE]
>  範例只供教育目的之用。 不能用於實際執行環境，而且從來沒有在實際執行環境中測試過。 Microsoft 不提供對這些範例的技術支援。  
  
## <a name="prerequisites"></a>必要條件  
  
-   初始化的 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 資料庫  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>範例專案  
  
-   **PropertyPromotionActivity**專案包含了有關提升特有的組態項目、 工作流程活動和工作流程延伸模組檔案。  
  
-   **CounterServiceApplication**專案包含使用的範例工作流程**SqlWorkflowInstanceStorePromotion**專案。  
  
-   必須針對 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 資料庫執行的 SQL 指令碼 (PropertyPromotionActivitySQLSample.sql)。  
  
-   連結兩個 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 專案的方案檔案 (`PropertyPromotionActivity.sln`)。  
  
## <a name="to-set-up-and-run-the-sample"></a>若要設定及執行範例  
  
1.  初始化工作流程持續性資料庫。  
  
    1.  巡覽至範例目錄 (\WF\Basic\Persistence\PropertyPromotionActivity)，並執行 CreateInstanceStore.cmd。  
  
    2.  如果未提供系統管理員權限，請建立 SQL Server 登入。 在 SQL Server Management Studio，請移至**安全性**，**登入**。 以滑鼠右鍵按一下**登入**並建立新的登入。 將 ACL 使用者加入至 SQL 角色，藉由開啟**資料庫**， **InstanceStore**，**安全性**。 以滑鼠右鍵按一下**使用者**選取**新使用者**。 設定**登入名稱**上面建立的使用者。 將使用者加入至資料庫角色成員資格 System.Activities.DurableInstancing.InstanceStoreUsers (和其他成員資格)。 請注意，使用者可能已存在 (例如 dbo 使用者)。  
  
2.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 PropertyPromotionActivity.sln 方案檔案。  
  
3.  如果您在 SQL Server Express 本機安裝以外的資料庫中建立執行個體存放區，您必須更新資料庫連接字串。 更改 App.config 檔案下的**CounterServiceApplication**所設定的值`connectionString`屬性`sqlWorkflowInstanceStorePromotion`節點，讓它指向已初始化的持續性資料庫中步驟 1。  
  
4.  建置並執行方案。 這樣會啟動計數器 WF 服務，並自動啟動工作流程執行個體。  
  
5.  在持續性資料庫中快速選取 [dbo].[CounterService] 檢視表中的所有資料列 (這個檢視表是藉由執行步驟 1 的 CreateInstanceStore.cmd 所加入)。 您將會看到類似下面的結果集：  
  
    |InstanceId|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     在您持續重新整理檢視表時，您會注意到 CounterValue 和 CounterValueLastUpdated 每隔兩秒鐘就會變更。 這是計數器更新自己的間隔。 CounterValue 和 CounterValueLastUpdated 代表這個工作流程的提升屬性。  
  
## <a name="to-remove-the-sample"></a>若要移除範例  
  
-   執行範例目錄 (\WF\Basic\Persistence\PropertyPromotionActivity) 中的 RemoveInstanceStore.cmd。  
  
## <a name="understanding-this-sample"></a>了解這個範例  
 此範例包含兩個專案和一個 SQL 檔案：  
  
-   **CounterServiceApplication**是裝載簡單計數器 WF 服務的主控台應用程式。 一旦透過 `Start` 端點收到單向訊息之後，工作流程就會從 0 開始算到 29，每隔兩秒鐘累加計數器變數。 在每次累加計數器之後，工作流程會保存而提升屬性則會在 [dbo].[CounterService] 檢視表中更新。 當執行主控台應用程式時，它會裝載 WF 服務並將訊息傳送給 `Start` 端點，以建立計數器 WF 執行個體。  
  
-   **PropertyPromotionActivity**是一個類別庫包含組態項目、 工作流程活動和工作流程延伸模組， **CounterServiceApplication**使用。  
  
-   **PropertyPromotionActivitySQLSample.sql**建立，並將檢視 [dbo]。 [CounterService] 資料庫。  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>使用 SqlWorkflowInstanceStorePromotion 組態元素  
 `SqlWorkflowInstanceStorePromotion` 組態元素繼承自 `SqlWorkflowInstanceStore` 組態元素，而且會加入稱為 `promotionSets` 的其他組態元素。 `promotionSets` 元素可讓使用者透過組態指定提升屬性。 這是範例所使用的組態檔：  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 檢查 [dbo].[CounterService] 檢視表的定義。  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 當保存工作流程執行個體時，將會針對組態中定義的每一個 `InstancePromotedProperties`，將一個資料列插入 `PromotionSet` 檢視表中。 這個資料列包含 `PromotionSet` 的所有提升屬性 (一個資料行一個提升屬性)。 這個 `PromotionSet` 是由 Tuple 當做索引鍵：`InstanceId, PromotionName`。 在此範例中，組態中已定義一個 `PromotionSet`，而它的名稱屬性為 `CounterService`。 請注意，`PromotionName` 資料行值為何等於 `PromotionSet` 元素的名稱屬性。  
  
 `promotedValue` 元素的順序與提升屬性在 `InstancePromotedProperties` 檢視中的位置相關。 `Count` 是第一個 `promotedValue` 元素。 因此，它會對應到 `Value1` 檢視表中的 `InstancePromotedProperties` 資料行。 `LastIncrementedAt` 是第二個 `promotedValue` 元素。 因此，它會對應到 `Value2` 檢視表中的 `InstancePromotedProperties` 資料行。  
  
#### <a name="using-the-promotevalue-activity"></a>使用 PromoteValue 活動  
 在 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] 設計工具中檢查 CounterService.xamlx 檔案。 請注意 WF 定義中有兩個特殊活動：`PromoteValue<DateTime>` 和 `PromoteValue<Int32>`。  
  
 `PromoteValue<Int32>` 活動將它的 `Name` 成員定義為 `Count`。 這會符合組態中的第一個 `promotedValue` 元素，並將其 `Value` 定義為 `Counter` 工作流程變數。 當保存此工作流程時，`Counter` 工作流程變數會當做提升屬性保存到 `Value1` 檢視表的 `InstancePromotedProperties` 資料行中。  
  
 `PromoteValue<DateTime>` 活動將它的 `Name` 成員定義為 `LastIncrementedAt`。 這會符合組態中的第二個 `promotedValue` 元素，並將其 `Value` 定義為 `TimeLastIncremented` 工作流程變數。 這表示當保存此工作流程時，`TimeLastIncremented` 工作流程變數的值將會當做提升屬性保存到 `Value2` 檢視表的 `InstancePromotedProperties` 資料行中。  
  
 請注意，`PromotedValue` 活動也有一個名為 `ClearExistingPromotedData` 的布林成員。 當這個成員設定為 `true` 時，這會在工作流程中清除到該點為止的所有提升屬性值。 例如，如果序列活動定義如下：  
  
1.  PromoteValue {Name ="Count"，值 = 3}  
  
2.  PromoteValue {Name ="LastIncrementedAt"，值 = 1-1-2000年}  
  
3.  保存  
  
4.  PromoteValue {Name ="Count"，值 = 4，ClearExistingPromotedData = true}  
  
5.  保存  
  
 在第二個保存中，`Count` 的提升值將會是 4。 不過的提升的值`LastIncrementedAt`將`NULL`。 如果 `ClearExistingPromotedData` 在步驟 4 未設定為 `true`，則在第二個保存之後，Count 的提升值會是 4。 因此，`LastIncrementedAt` 的提升值仍然是 1-1-2000。  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 此類別庫包含下列公用類別，以簡化 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 提升功能的使用。  
  
#### <a name="promotevalue-class"></a>PromoteValue 類別  
 這個類別會提升一個屬性。 提升屬性 (Property) 的名稱應該符合組態中 `promotedValue` 元素的名稱屬性 (Attribute)。 這個活動可在工作流程設計工具中使用。 請參閱 CounterServiceApplication 以了解範例的使用。  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 ClearExistingPromotedData (Bool)  
 清除在這個活動之前提升的所有值。  
  
 Name (string)  
 代表這個屬性的名稱。 這應該符合的名稱屬性\<promotedValue > 組態中的項目。  
  
 值 (InArgument\<T >)  
 您想要儲存在資料行中的變數 / 值。  
  
#### <a name="promotevalues-class"></a>PromoteValues 類別  
 提升多個屬性。 提升屬性 (Property) 的名稱應該符合組態中 `promotedValue` 元素內的所有名稱屬性 (Attribute)。 其用法類似於 `PromoteValue` 活動，除了多個屬性將會同時提升的事實以外。 這個活動不能在工作流程設計工具中使用。  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a>SqlWorkflowInstanceStorePromotionBehavior  
 衍生自 `SqlWorkflowInstanceStoreBehavior`。 這個衍生類別會加入自訂持續性參與者 (也是這個程式庫的一部分) 當做工作流程延伸模組。 之前兩個工作流程活動的實作取決於這個自訂持續性參與者。  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 此類別庫也包含 `ConfigurationElement` 的 `SqlWorkflowInstanceStorePromotionElement` 實作，以及之前的提升活動所使用的自訂持續性參與者。  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 這個 SQL 檔案除了 `[dbo].[CounterService]` 檢視表以外也會建立 `[InstancePromotedProperties]` 檢視表，以便查詢已設定 CounterService Promotion 的所有執行個體。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
