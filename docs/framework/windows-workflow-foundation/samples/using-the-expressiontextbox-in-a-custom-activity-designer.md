---
title: 使用自訂活動設計工具中的 ExpressionTextBox
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182760"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>使用自訂活動設計工具中的 ExpressionTextBox
這個範例示範如何在自訂活動設計工具內使用 <xref:System.Activities.Presentation.View.ExpressionTextBox>。 自訂活動 `MultiAssign` 會將兩個字串值指派給兩個字串變數。 某些 <xref:System.Activities.Presentation.View.ExpressionTextBox> 控制項會繫結至 <xref:System.Activities.InArgument>，而某些則繫結至 <xref:System.Activities.OutArgument>。

## <a name="sample-details"></a>範例詳細資料
 `ArgumentToExpressionConverter` 是將運算式繫結至引數時所使用的型別轉換子。 `ConverterParameter` 必須適當地設定為 `In` 或 `Out`。 不支援 `InOut`。

 該`UseLocationExpression`屬性用於`OutArgument`指定運算式應為 L 值（"左值"或"位置值"）運算式。 在大多數情況下，L-value 運算式是有效的 Visual Basic 識別碼，用來指出傳回的 `OutArgument` 為變數或引數名稱。

 在這個範例中，`MaxLines` 屬性設定為一，而且未設定 `MinLines`。 這表示 <xref:System.Activities.Presentation.View.ExpressionTextBox> 的固定大小為一行，不論使用者輸入多少的文字數量。 若要允許 <xref:System.Activities.Presentation.View.ExpressionTextBox> 成長來符合使用者輸入，請將 `MaxLines` 設定為大於 `MinLines`。

 ExpressionTextBox 只能繫結至引數，無法繫結至 CLR 屬性。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2010，打開運算式文本BoxSample.sln 檔。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

#### <a name="to-run-this-sample"></a>執行此範例

1. 將新的工作流程主控台應用程式加入至方案。

2. 從新的工作流主控台應用程式專案添加對**運算式文本BoxSample**專案的引用。

3. 建置方案。

4. 從工具箱中拖動 **"多分配"** 活動並將其放入工作流中。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [使用工作流程設計工具開發應用程式](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
