---
title: 程式設計模型項目樹狀
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142689"
---
# <a name="programming-model-item-tree"></a>程式設計模型項目樹狀
此示例演示如何使用 Windows 演示文稿<xref:System.Activities.Presentation.Model.ModelItem>基礎 （WPF） 樹狀檢視的聲明性資料繫結導航樹。

## <a name="sample-details"></a>範例詳細資料
 樹<xref:System.Activities.Presentation.Model.ModelItem>是 Windows 工作流設計器基礎結構用於公開有關正在編輯的基礎實例的資料的抽象。 下圖描述了工作流設計器中的各種基礎結構層。

 ![顯示工作流設計器體系結構的圖表。](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> 包含基礎值的指標，以及 <xref:System.Activities.Presentation.Model.ModelProperty> 物件的集合。 <xref:System.Activities.Presentation.Model.ModelProperty> 物件則是由名稱、屬性型別和值的指標這類資料所構成，而值的指標則會是另一個 <xref:System.Activities.Presentation.Model.ModelItem>。 值轉換子可用來操作從 <xref:System.Activities.Presentation.Model.ModelItem> 傳回的一些 <xref:System.Activities.Presentation.Model.ModelProperty>，讓它們在樹狀檢視中正確顯示。 接著這個範例會示範如何使用命令式語法，以命令方式對 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀進行程式設計，如下面範例中所示。

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 在 Visual Studio 2010 中打開程式設計模型專案Tree.sln 解決方案。

2. 通過從 **"生成"** 功能表中選擇**生成解決方案**來生成解決方案。

3. 按 F5 執行應用程式。 然後顯示 WPF 表單。

4. 按一下 **"載入 WF"** 按鈕以<xref:System.Activities.Presentation.Model.ModelItem>載入 並綁定到樹狀檢視。

5. 按一下 **"更改模型項樹"** 按鈕將執行前面的代碼，以將項添加到樹中並設置屬性。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.IValueConverter>
