---
title: 使用 WorkflowInvoker 類別
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: 70fc94b1f190236cb2cb40c407e0172f0213fb7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-workflowinvoker-class"></a>使用 WorkflowInvoker 類別
這個範例示範如何使用 <xref:System.Activities.WorkflowInvoker> 類別如同方法一般叫用活動。  
  
## <a name="sample-details"></a>範例詳細資料  
 使用 <xref:System.Activities.WorkflowInvoker> 類別是執行活動的最簡單方式。 其設計在於如同方法一般直接執行活動。 它是一個輕量型、高效能且易用的 API，可在活動的執行不需要其他裝載變化提供的控制項基礎結構的情況下使用。  
  
 此範例會使用自訂活動衍生自<xref:System.Activities.CodeActivity%601>< Int32\>名為`Add`會加入兩個<xref:System.Activities.InArgument%601>，`X`和`Y`，並傳回`Result` <xref:System.Activities.OutArgument%601>。 (<xref:System.Activities.CodeActivity%601>\<T > 是衍生自<xref:System.Activities.Activity%601>< T\>，其具有<xref:System.Activities.OutArgument%601> \<T > 名為`Result`。)A `Dictionary`\<字串、 物件 > 用來將引數傳遞到透過叫用活動<xref:System.Activities.WorkflowInvoker>。 字典的索引鍵會對應到所叫用活動上引數的名稱。 與特殊索引鍵相關聯的值會繫結至索引鍵識別的引數。  
  
 此範例會呼叫 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 並且傳遞包含 `X` 和 `Y` 之值的字典。 <xref:System.Activities.WorkflowInvoker> 類別會將這些值繫結至 `Add` 活動的引數、執行活動，並且傳回結果。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [Invoker.sln] 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按 F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`