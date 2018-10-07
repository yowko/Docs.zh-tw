---
title: 使用 Pick 活動
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 59f99d2e0a69d796c1ec64093cf73e07b88887c9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48848279"
---
# <a name="using-the-pick-activity"></a>使用 Pick 活動
這個範例示範如何使用 <xref:System.Activities.Statements.Pick> 活動。

 <xref:System.Activities.Statements.Pick> 活動會提供以事件為主的控制模型。 其行為與 C# `switch` 陳述式類似，只執行 `switch` 陳述式的其中一個分支。 不同於 `switch` 陳述式是根據值來執行分支，<xref:System.Activities.Statements.Pick> 活動是根據活動完成方式來執行分支。

 這個範例會提示使用者在主控台於給定時限內輸入名稱。 範例中的 <xref:System.Activities.Statements.Pick> 活動有兩個分支，它們是根據使用者是否在 5 秒內輸入名稱來執行。 如果使用者在 5 秒內輸入名稱，則會執行包含自訂 `ReadLine` 活動的第一個分支，否則會執行包含 <xref:System.Activities.Statements.Delay> 活動的另一個分支。 在主控台輸入使用者名稱後，就會在主控台上列印此名稱。 如果沒有在 5 秒內輸入，則作業逾時。

## <a name="demonstrates"></a>示範
 <xref:System.Activities.Statements.Pick> 活動。

## <a name="discussion"></a>討論
 此範例包含設計工具工作流程和程式碼工作流程。

 設計工具的工作流程設計工具版本的範例示範如何建立工作流程設計工具中。 包含下列檔案：

-   Program.cs：包含執行範例工作流程的 `Main` 函數。

-   ReadString.cs：從主控台讀取輸入的自訂活動。

-   Sequence1.xaml：在使用 Pick 的設計工具中建立工作流程。

 自動程式化的工作流程範例的程式碼版本示範如何建立工作流程設計工具中。 包含下列檔案：

-   Program.cs：包含執行範例工作流程的 `Main` 函數。

-   ReadString.cs：從主控台讀取輸入的自訂活動。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1.  使用 Visual Studio 2010 開啟 Pick.sln 方案檔案。

2.  若要建置此方案，請按 CTRL+SHIFT+B。

3.  若要執行此方案，請按 F5。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`