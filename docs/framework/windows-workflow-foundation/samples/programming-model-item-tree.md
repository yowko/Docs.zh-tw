---
title: 程式設計模型項目樹狀
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 059bb3edcfe41f52e2244ff6f5bf3fc78a4262bb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235801"
---
# <a name="programming-model-item-tree"></a>程式設計模型項目樹狀

這個範例示範如何 <xref:System.Activities.Presentation.Model.ModelItem> 使用 Windows Presentation Foundation (WPF) 樹狀檢視中的宣告式資料系結，來流覽樹狀結構。

## <a name="sample-details"></a>範例詳細資料

 <xref:System.Activities.Presentation.Model.ModelItem>樹狀結構是 Windows 工作流程設計工具基礎結構用來公開所編輯之基礎實例相關資料的抽象概念。 下圖是工作流程設計工具內各層基礎結構的描述。

 ![顯示工作流程設計工具架構的圖表。](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> 包含基礎值的指標，以及 <xref:System.Activities.Presentation.Model.ModelProperty> 物件的集合。 <xref:System.Activities.Presentation.Model.ModelProperty> 物件則是由名稱、屬性型別和值的指標這類資料所構成，而值的指標則會是另一個 <xref:System.Activities.Presentation.Model.ModelItem>。 值轉換子可用來操作從 <xref:System.Activities.Presentation.Model.ModelItem> 傳回的一些 <xref:System.Activities.Presentation.Model.ModelProperty>，讓它們在樹狀檢視中正確顯示。 接著這個範例會示範如何使用命令式語法，以命令方式對 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀進行程式設計，如下面範例中所示。

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 在 Visual Studio 2010 中開啟 ProgrammingModelItemTree .sln 方案。

2. 從 [**組建**] 功能表選取 [**組建方案**] 來建立方案。

3. 按 F5 執行應用程式。 WPF 表單隨即顯示。

4. 按一下 [ **載入 WF** ] 按鈕載入， <xref:System.Activities.Presentation.Model.ModelItem> 並將它系結至樹狀檢視。

5. 按一下 [ **變更模型專案樹狀** ] 按鈕會執行上述程式碼，將專案加入至樹狀結構並設定屬性。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.IValueConverter>
