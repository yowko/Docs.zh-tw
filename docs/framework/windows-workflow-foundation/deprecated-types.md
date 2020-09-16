---
title: Windows Workflow Foundation 中被取代的類型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b0ec30d2778333537e781e6681927f7048b630ea
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543780"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation 中被取代的類型
在 .NET 4 中，工作流程小組在 <xref:System.Activities> 命名空間中發行了全新的工作流程引擎。 在 .NET 4.5 Beta 版中，我們會將 "WF 3" <xref:System.Workflow.Activities> 、和命名空間中的大部分類型標示 <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> 為已淘汰。  
  
## <a name="obsolete-namespaces-and-tools"></a>過時的命名空間和工具  
 下列組件含有一個或多個將會被取代的公用型別：  
  
- System.Workflow.Activities.dll  
  
- System.Workflow.ComponentModel.dll  
  
- System.Workflow.Runtime.dll  
  
- System.WorkflowServices.dll  
  
- Microsoft.Workflow.DebugController.dll  
  
- Microsoft.Workflow.Compiler.exe  
  
- Wfc.exe  
  
 因此，使用已被取代之 WF 3 應用程式開發介面的客戶，將會遇到類似下列訊息的建置警告：  
  
 **警告 BC40000： X 已淘汰： WF 3 類型已淘汰。請改用 WF 4。** 在未來的發行版本中，我們會將這些型別從 .NET Framework 移除，但我們尚未決定時間範圍 (不是在 4.5)。 目前這個步驟可讓我們向客戶傳達我們的方向，讓他們有大量的時間可以移至新的 WF4 模型。 當然，我們也會繼續在 [Microsoft 支援服務生命週期原則](/lifecycle/)下支援這些 WF 3 類型。 現有的 WF3 應用程式將會在 .NET 4.5 中執行，而不會發生問題，Visual Studio 2012 將會支援新的和現有的 WF3 解決方案。  
  
 <xref:System.Workflow.Activities.Rules> 命名空間中與規則相關的型別在 WF 4.5 中並沒有替代項目，所以尚未被取代。  
  
 如果客戶想要將其應用程式遷移至 WF 4，則會在 [工作流程4遷移指引](migration-guidance.md)中找到說明。
