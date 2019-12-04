---
title: 程式設計模型項目樹狀
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: efda69ac568b0ad9c5fdcf4d42722c5b7dadd3f3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715670"
---
# <a name="programming-model-item-tree"></a>程式設計模型項目樹狀
這個範例會示範如何使用 Windows Presentation Foundation （WPF）樹狀檢視中的宣告式資料系結，流覽 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構。

## <a name="sample-details"></a>範例詳細資料
 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀目錄是 Windows 工作流程設計工具基礎結構所使用的抽象概念，用以公開所編輯之基礎實例的相關資料。 下圖是工作流程設計工具內各種基礎結構層的描述。

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

1. 在 Visual Studio 2010 中開啟 [ProgrammingModelItemTree] 方案。

2. 從 [**建立**] 功能表中選取 [**建立方案**] 來建立方案。

3. 按 F5 執行應用程式。 然後會顯示 WPF 表單。

4. 按一下 [**載入 WF** ] 按鈕以載入 <xref:System.Activities.Presentation.Model.ModelItem>，並將它系結至樹狀檢視。

5. 按一下 [**變更模型專案樹狀檢視**] 按鈕會執行上述程式碼，將專案加入至樹狀結構並設定屬性。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.IValueConverter>
