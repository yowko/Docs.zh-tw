---
title: 如何：引發和使用事件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44193213"
---
# <a name="how-to-raise-and-consume-events"></a>如何：引發和使用事件
本主題中的範例將示範如何使用事件。 包括 <xref:System.EventHandler> 委派、<xref:System.EventHandler%601> 委派和自訂委派的範例，用以說明包含和不包含資料的事件。  
  
 範例將使用[事件](../../../docs/standard/events/index.md)一文中所述的概念。  
  
## <a name="example"></a>範例  
 第一個範例將示範如何引發和使用沒有資料的事件。 它包含名為 `Counter` 的類別，該類別中包含名為 `ThresholdReached` 的事件。 當計數器的值等於或超過臨界值時，就會引發此事件。 由於未提供任何事件資料，因此 <xref:System.EventHandler> 委派會與事件產生關聯。  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>範例  
 下一個範例將示範如何引發和使用有提供資料的事件。 <xref:System.EventHandler%601> 委派會與事件相關聯，而且會提供自訂事件資料物件的執行個體。  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>範例  
 下一個範例將示範如何宣告事件的委派。 委派的名稱為 `ThresholdReachedEventHandler`。 這只是一個範例。 通常，您可以使用 <xref:System.EventHandler> 或 <xref:System.EventHandler%601> 委派，所以不需要為事件宣告委派。 在某些少見的案例中您會需要宣告委派，像是讓無法使用泛型的舊版程式碼使用您的類別。  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [事件](../../../docs/standard/events/index.md)
