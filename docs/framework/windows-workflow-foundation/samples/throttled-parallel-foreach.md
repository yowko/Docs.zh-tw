---
title: 流速控制平行 ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715913"
---
# <a name="throttled-parallel-foreach"></a>流速控制平行 ForEach

`ThrottleParallelForEach` 活動與 <xref:System.Activities.Statements.ParallelForEach%601> 活動十分類似，唯一的例外是前者允許設定並行因數來限制同時執行的分支數目。 `ThrottleParallelForEach` 活動衍生自 <xref:System.Activities.NativeActivity>，因為它必須排程其他活動 (子活動)，而且這只能透過 <xref:System.Activities.NativeActivityContext> 類別存取。

## <a name="projects"></a>Projects

|**ProjectName**|**說明**|**主要檔案**|
|-|-|-|
|ThrottledParallelForEach|包含 `ThrottledParallelForEach` 活動和其設計工具|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` 活動定義。|
|CodeTestClient|範例用戶端應用程式，可透過使用命令式程式碼的 `ThrottledParallelForEach` 來設定及執行工作流程。|Program.cs<br /><br /> 定義及執行範例工作流程的執行個體。|

## <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2010，開啟 [Throttledparallelforeach.sln] 檔案。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

3. 若要執行此方案，請按 F5。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
