---
title: 計時器
description: 了解哪些 .NET 計時器可用於多執行緒環境。
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 644ccf5951e9d2556fc697d2fd763f026fd0ebdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617222"
---
# <a name="timers"></a>計時器

.NET 提供兩種計時器，可用於多執行緒環境：

- <xref:System.Threading.Timer?displayProperty=nameWithType> 會定期在 <xref:System.Threading.ThreadPool> 執行緒上執行單一回呼方法。
- <xref:System.Timers.Timer?displayProperty=nameWithType> 預設會定期在 <xref:System.Threading.ThreadPool> 執行緒上引發事件。

> [!NOTE]
> 某些 .NET 實作可能會包含其他計時器：
>
> - <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>：定期引發事件的 Windows Forms 元件。 該元件沒有使用者介面，是專為用於單一執行緒環境所設計。  
> - <xref:System.Web.UI.Timer?displayProperty=nameWithType>：定期執行非同步或同步網頁回傳的 ASP.NET 元件。
> - <xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>：整合到 <xref:System.Windows.Threading.Dispatcher> 佇列中的計時器，會依指定的時間間隔及指定的優先順序處理。

## <a name="the-systemthreadingtimer-class"></a>System.Threading.Timer 類別

<xref:System.Threading.Timer?displayProperty=nameWithType> 類別可讓您依指定的時間間隔連續呼叫委派。 您也可以使用此類別，排程單一委派呼叫依指定時間間隔執行。 委派是在 <xref:System.Threading.ThreadPool> 執行緒上執行。

當您建立 <xref:System.Threading.Timer?displayProperty=nameWithType> 物件時，您會指定定義回呼方法的 <xref:System.Threading.TimerCallback> 委派、傳遞至回呼的選擇性狀態物件、第一個回呼引動過程之前延遲的時間量，以及回呼引動過程之間的時間間隔。 若要取消擱置中的計時器，請呼叫 <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> 方法。

下列範例會建立計時器，在一秒 (1000 毫秒) 後第一次呼叫提供的委派，然後每隔兩秒呼叫一次。 範例中的狀態物件可用來計算呼叫委派的次數。 計時器會在委派至少呼叫 10 次時停止。

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

如需詳細資訊與範例，請參閱<xref:System.Threading.Timer?displayProperty=nameWithType>。

## <a name="the-systemtimerstimer-class"></a>System.Timers.Timer 類別

可用於多執行緒環境的另一個計時器是 <xref:System.Timers.Timer?displayProperty=nameWithType>，預設會在 <xref:System.Threading.ThreadPool> 上引發事件。

建立 <xref:System.Timers.Timer?displayProperty=nameWithType> 物件時，您可以指定要引發 <xref:System.Timers.Timer.Elapsed> 事件的時間間隔。 使用 <xref:System.Timers.Timer.Enabled%2A> 屬性指出計時器是否應該引發 <xref:System.Timers.Timer.Elapsed> 事件。 如果您需要 <xref:System.Timers.Timer.Elapsed> 事件只在經過指定的間隔之後才引發，請將 <xref:System.Timers.Timer.AutoReset%2A> 設定為 `false`。 <xref:System.Timers.Timer.AutoReset%2A> 屬性的預設值為 `true`，表示 <xref:System.Timers.Timer.Elapsed> 事件會依 <xref:System.Timers.Timer.Interval%2A> 屬性定義的間隔定期引發。

如需詳細資訊與範例，請參閱<xref:System.Timers.Timer?displayProperty=nameWithType>。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [執行緒物件和功能](threading-objects-and-features.md)
