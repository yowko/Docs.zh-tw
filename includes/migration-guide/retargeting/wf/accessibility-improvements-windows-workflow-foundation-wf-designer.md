---
ms.openlocfilehash: d420be76645fc71ac922542fa49f799a473e9a83
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614392"
---
### <a name="accessibility-improvements-in-windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) 工作流程設計工具中的協助工具改善

#### <a name="details"></a>詳細資料

Windows Workflow Foundation (WF) 工作流程設計工具正在使用協助工具技術改善其運作方式。 這些改善包括下列變更：

- 在某些控制項中，定位順序變更為由左至右及由上至下：
- 設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動之關聯性資料的初始化關聯性視窗
- <xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的內容定義視窗
- 可透過鍵盤使用多個功能：
- 編輯活動的屬性時，如果第一次將焦點放在屬性群組，可以透過鍵盤將其摺疊。
- 現在可透過鍵盤存取警告圖示。
- 現在可透過鍵盤存取 [屬性] 視窗中的 [其他屬性] 按鈕。
- 鍵盤使用者現在可以存取工作流程設計工具之 [引數] 和 [變數] 窗格中的標頭項目。
- 在以下這類情況發生時，已改善具有焦點之項目的可見性：
- 在工作流程設計工具與活動設計工具所使用的資料格中新增資料列。
- 使用 Tab 鍵循環顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活動的欄位。
- 設定變數或引數的預設值
- 螢幕助讀程式現在可以正確辨識：
- 工作流程設計工具中設定的中斷點。
- <xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision> 和 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。
- <xref:System.ServiceModel.Activities.Receive> 活動的內容。
- <xref:System.Activities.Statements.InvokeMethod> 活動的目標類型。
- <xref:System.Activities.Statements.TryCatch> 活動中的例外狀況下拉式方塊和 Finally 區段。
- 傳訊活動 (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>) 中的 [訊息類型] 下拉式方塊、[新增關聯性初始設定式] 視窗、[內容定義] 視窗和 [CorrelatesOn 定義] 視窗。
- 狀態機器轉換和轉換目的地。
- <xref:System.Activities.Statements.FlowDecision> 活動的註釋和連接器。
- 活動的操作 (右鍵) 功能表。
- 屬性方格中的屬性值編輯器、[清除搜尋] 按鈕、[依分類] 及 [字母順序] 排序按鈕和 [運算式編輯器] 對話方塊。
- 工作流程設計工具中的顯示比例百分比。
- <xref:System.Activities.Statements.Parallel> 和 <xref:System.Activities.Statements.Pick> 活動中的分隔符號。
- <xref:System.Activities.Statements.InvokeDelegate> 活動。
- 字典活動 (`Microsoft.Activities.AddToDictionary&lt;TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>` 等) 的 [選取類型] 視窗。
- [瀏覽並選取 .NET 類型] 視窗。
- 工作流程設計工具中的階層連結。
- 選擇高對比佈景主題的使用者會看到工作流程設計工具和其控制項在可見性方面的許多改善，例如項目之間的更佳對比比例以及用於焦點項目的更明顯選取方塊。

#### <a name="suggestion"></a>建議

如果您使用已重新裝載工作流程設計工具的應用程式，藉由執行上述其中一個動作，您的應用程式可以受益於這些變更：

- 重新編譯應用程式，使其以 .NET Framework 4.7.1 為目標。 預設會啟用這些協助工具變更。
- 應用程式若以 .NET Framework 4.7 或舊版為目標，但卻在 .NET Framework 4.7.1 上執行，您可以在 app.config 檔案的 `<runtime>` 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出這些舊版協助工具行為，如下列範例所示。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇加入舊版的協助工具功能。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.1       |
| 類型    | 正在重定目標 |
