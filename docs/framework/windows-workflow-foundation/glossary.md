---
title: ".NET Framework 4.5 的 Windows Workflow Foundation 字彙"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: "259"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a0cc6d9a0c922e57bf00b649894f26b42a64f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>.NET Framework 4.5 的 Windows Workflow Foundation 字彙
以下是 Windows Workflow Foundation 文件中使用的詞彙。  
  
## <a name="terms"></a>詞彙  
  
|詞彙|定義|  
|----------|----------------|  
|活動|Windows Workflow Foundation 中程式行為的單元。 可將單一活動組成更複雜的活動。|  
|Activity Action - 活動動作|用來公開回呼以執行工作流程和活動的資料結構。|  
|Argument - 引數|定義進出活動的資料流程。 每個引數都有指定的方向：in、out 或 in/out。這些參數表示活動的輸入、輸出和輸入/輸出參數。|  
|Bookmark - 書籤|活動可暫停並等候繼續的時間點。|  
|補償|設計用來恢復或降低先前完成工作之影響的動作群組。|  
|相互關聯|路由傳送訊息至工作流程或服務執行個體的機制。|  
|運算式|接受一個或多個引數、在引數上執行作業並傳回單一值的建構。 只要可使用活動的任何地方，就可以使用運算式。|  
|Flowchart - 流程圖|將程式元件表示為符號並用方向箭頭加以連結的已知模型開發架構。  在 .NET Framework 4 中，工作流程可透過 Flowchart 活動模型化為流程圖。|  
|Long-running Process - 長期執行的處理序|不會立即傳回、可跨越多次系統重新啟動的程式執行單元。|  
|保存性|將工作流程或服務的狀態儲存至永久性媒體，使其得以從記憶體卸載或在系統失敗後復原。|  
|State Machine - 狀態機器|將程式元件表示為個別狀態並用事件驅動狀態轉換加以連結的已知模型開發架構。  工作流程可透過 StateMachine 活動模型化為狀態機器。|  
|Substance - 令重|表示在通用識別項下的相關書籤群組，允許執行階段決定特定書籤的繼續執行是否有效或可變成有效。|  
|Type Converter - 型別轉換子|CLR 型別可以與一個或多個 System.ComponentModel.TypeConverter 衍生型別相關聯，這些型別可將 CLR 型別的執行個體和其他型別的執行個體來回轉換。 型別轉換子透過 System.ComponentModel.TypeConverterAttribute 屬性來與 CLR 型別相關聯。  TypeConverterAttribute 可直接在 CLR 型別或在屬性上指定。 屬性上指定之型別轉換子的優先順序永遠高於屬性之 CLR 型別上指定之型別轉換子。|  
|變數|表示必須儲存以供稍後存取之部分資料的儲存體。|  
|工作流程|主機處理序所叫用之單一活動或活動樹狀結構。|  
|XAML|eXtensible Application Markup Language|
