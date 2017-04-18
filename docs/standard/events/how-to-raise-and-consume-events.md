---
title: "如何：引發和使用事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件 [.NET Framework], 引發"
  - "事件 [.NET Framework], 範例"
  - "引發事件"
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：引發和使用事件
本主題中的範例示範如何使用事件。  包含由 <xref:System.EventHandler> 委派、 <xref:System.EventHandler%601> 委派和自訂委派的範例，以有資料和沒資料兩種情況說明事件。  
  
 範例使用 [事件](../../../docs/standard/events/index.md) 文章說明的概念。  
  
## 範例  
 第一個範例顯示如何引發和使用沒有資料的事件。  它包含有一個名為有 `ThresholdReached`事件的`Counter`類別名稱。  在計數器值等於或超過臨界值時，就會引發此事件。  因為未提供任何事件， <xref:System.EventHandler>委派與事件有關。  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## 範例  
 下一個範例顯示如何引發和使用有提供資料的事件。  <xref:System.EventHandler%601> 委派與事件有關，因此提供自訂事件資料物件的執行個體。  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## 範例  
 下一個範例顯示如何宣告事件的委派。  委派名稱為 `ThresholdReachedEventHandler`。  這只是個範例。  通常，因為您可以使用 <xref:System.EventHandler> 或 <xref:System.EventHandler%601> 委派，所以您不需要宣告委派給一個事件。  在罕見案例像是讓類別能夠在舊版程式碼\(不可使用泛型\)使用，您應該宣告一個委派。  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## 請參閱  
 [事件](../../../docs/standard/events/index.md)