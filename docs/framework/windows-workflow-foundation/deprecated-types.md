---
title: Windows Workflow Foundation 中被取代的類型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b25be26d4c0ad6c423b011cd7cad24a8728333f5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658895"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation 中被取代的類型
在 .NET 4 中，工作流程小組在 <xref:System.Activities> 命名空間中發行了全新的工作流程引擎。 .NET 4.5 Beta 版本中，我們要標記"WF 3"中類型的大部分<xref:System.Workflow.Activities>， <xref:System.Workflow.ComponentModel>，和<xref:System.Workflow.Runtime>為已過時的命名空間。  
  
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
  
 **警告 BC40000: X 是已經過時： WF 3 型別已被取代。請改用 WF 4。** 在未來的發行版本中，我們會將這些型別從 .NET Framework 移除，但我們尚未決定時間範圍 (不是在 4.5)。 目前這個步驟可讓我們向客戶傳達我們的方向，讓他們有大量的時間可以移至新的 WF4 模型。 我們當然會繼續支援這些 WF 3 型別[Microsoft 支援週期原則](https://aka.ms/MicrosoftSupportLifecycle)。 現有的 WF3 應用程式將會在 .NET 4.5 上執行，而不會有問題，而且 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 會支援最新和現有的 WF3 方案。  
  
 <xref:System.Workflow.Activities.Rules> 命名空間中與規則相關的型別在 WF 4.5 中並沒有替代項目，所以尚未被取代。  
  
 想要移轉到 WF 4 應用程式的客戶會發現協助[工作流程 4 移轉指引](migration-guidance.md)。
