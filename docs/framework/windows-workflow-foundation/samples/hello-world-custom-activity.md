---
title: Hello World 自訂活動
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533492"
---
# <a name="hello-world-custom-activity"></a>Hello World 自訂活動
這個範例會示範幾個重要功能的 Windows Workflow Foundation (WF)，包括如何建立簡單的自訂活動。 這個範例中示範的部分功能是以 C# 建立自訂活動，以及使用 `in` 和 `out` 引數 (<xref:System.Activities.InArgument> 和 <xref:System.Activities.OutArgument>)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a>以程式碼建立工作流程  
 在這個範例中，會使用 C# 程式碼建立兩個自訂活動。 這兩個自訂活動直接或間接繼承自 <xref:System.Activities.Activity%601>，以傳回單一值。 使用泛型傳回值 (而不繼承自非泛型 <xref:System.Activities.Activity> 類別) 的好處是，某些活動 (例如 <xref:System.Activities.Statements.Assign>) 在當做複合活動的一部分使用時能夠存取傳回值。  
  
 AppendString  
 這個活動繼承自 <xref:System.Activities.Activity%601>，會使用串連兩個字串的 <xref:System.Activities.Statements.Assign> 活動。  
  
 Prepend String  
 這個活動直接繼承自 <xref:System.Activities.CodeActivity%601>，會建立與 `AppendString` 活動類似的功能，即使用程式碼中實作的邏輯，而不是包含既有的活動。  
  
 下列檔案包含在此專案中。  
  
 AppendString.cs  
 附加字串的自訂活動。 它會接受字串，並將它與結合常值文字字串"says hello world 」 以形成完整訊息做為輸出。  
  
 PrependString.cs  
 這個活動會將預先定義的字串前置到輸入字串。  
  
 Sequence1.xaml  
 使用 `AppendString` 和 `PrependString` 自訂活動的工作流程。  
  
 Program.cs  
 執行工作流程的程式。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 HelloWorld.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按 F5。