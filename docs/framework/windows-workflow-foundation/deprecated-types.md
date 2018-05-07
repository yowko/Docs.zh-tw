---
title: Windows Workflow Foundation 中被取代的類型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 899d21f23c0500a1df01916d1da210b2f9bea95b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation 中被取代的類型
在 .NET 4 中，工作流程小組在 <xref:System.Activities> 命名空間中發行了全新的工作流程引擎。 .NET 4.5 Beta 版本中，我們要標記的大部分"WF 3"中類型<xref:System.Workflow.Activities>， <xref:System.Workflow.ComponentModel>，和<xref:System.Workflow.Runtime>命名空間為已過時。  
  
## <a name="obsolete-namespaces-and-tools"></a>過時的命名空間和工具  
 下列組件含有一個或多個將會被取代的公用型別：  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 因此，使用已被取代之 WF 3 應用程式開發介面的客戶，將會遇到類似下列訊息的建置警告：  
  
 **警告 BC40000: X 已過時： WF 3 型別已被取代。請改用 WF 4。** 在未來的發行版本中，我們會將這些型別從 .NET Framework 移除，但我們尚未決定時間範圍 (不是在 4.5)。 目前這個步驟可讓我們向客戶傳達我們的方向，讓他們有大量的時間可以移至新的 WF4 模型。 我們將當然，繼續支援這些 WF 3 型別[Microsoft 支援週期原則](http://aka.ms/MicrosoftSupportLifecycle)。 現有的 WF3 應用程式將會在 .NET 4.5 上執行，而不會有問題，而且 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 會支援最新和現有的 WF3 方案。  
  
 <xref:System.Workflow.Activities.Rules> 命名空間中與規則相關的型別在 WF 4.5 中並沒有替代項目，所以尚未被取代。  
  
 客戶想要移轉到 WF 4 其應用程式會尋找說明[工作流程 4 移轉指引](migration-guidance.md)。
