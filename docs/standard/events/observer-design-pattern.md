---
title: 觀察器設計模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06dbc4b7124aa873fd8471794fa25b0f47f8ce3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663583"
---
# <a name="observer-design-pattern"></a>觀察器設計模式

觀察者設計模式可讓訂閱者向提供者註冊，並且接收通知。 它適合任何需要推入型通知的情節。 這個模式會定義「提供者」  (也稱為「主題」  或「可預見值」  )，以及零個、一個或多個「觀察者」  。 觀察者會向提供者註冊，而且只要預先定義的條件、事件或狀態有所變更，提供者就會自動呼叫觀察者的其中一種方法，來通知所有觀察者。 在這個方法呼叫中，提供者也可以提供目前的狀態資訊給觀察者。 在 .NET Framework 中，觀察者設計模式是透過實作泛型 <xref:System.IObservable%601?displayProperty=nameWithType> 和 <xref:System.IObserver%601?displayProperty=nameWithType> 介面來套用。 泛型型別參數代表提供通知資訊的類型。

## <a name="applying-the-pattern"></a>套用模式

觀察者設計模式適合分散式推入型通知，因為它支援清楚分隔兩種不同的元件或應用程式層，例如資料來源 (商務邏輯) 層和使用者介面 (顯示) 層。 當提供者使用回呼將目前的資訊提供給其用戶端時，便會實作這個模式。

實作模式需要您提供下列項目：

- 提供者或主題，也就是傳送通知給觀察者的物件。 提供者是實作 <xref:System.IObservable%601> 介面的類別或結構。 提供者必須實作單一方法 <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>，觀察者會呼叫該方法，以接收來自提供者的通知。

- 觀察者，也就是接收來自提供者之通知的物件。 觀察者是實作 <xref:System.IObserver%601> 介面的類別或結構。 觀察者必須實作三種方法，這三種方法全都是由提供者呼叫：

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>，提供新的或目前的資訊給觀察者。

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>，通知觀察者發生錯誤。

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>，指出提供者已完成傳送通知。

- 允許提供者追蹤觀察者的機制。 一般而言，提供者會使用容器物件 (例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 物件) 保留已訂閱通知的 <xref:System.IObserver%601> 實作參考。 基於這個目的使用儲存容器，可讓提供者處理零個到無限多個觀察者。 觀察者接收通知的順序並未定義；提供者可自由使用任何方法來決定順序。

- <xref:System.IDisposable> 實作，可讓提供者在通知完成時移除觀察者。 觀察者會從 <xref:System.IObservable%601.Subscribe%2A> 方法接收 <xref:System.IDisposable> 實作的參考，如此觀察者同樣可以在提供者完成傳送通知之前呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法來取消訂閱。

- 包含提供者傳送給觀察者之資料的物件。 這個物件的類型對應至 <xref:System.IObservable%601> 和 <xref:System.IObserver%601> 介面的泛型類型參數。 雖然這個物件可以與 <xref:System.IObservable%601> 實作相同，但它常是不同的類型。

> [!NOTE]
> 除了實作觀察者設計模式之外，您可能對探索使用 <xref:System.IObservable%601> 和 <xref:System.IObserver%601> 介面建置的程式庫有興趣。 例如，[Reactive Extensions for .NET (Rx)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) 是由一組擴充方法和 LINQ 標準序列運算子所組成，可支援非同步程式設計。

## <a name="implementing-the-pattern"></a>實作模式

下列範例會使用觀察者設計模式實作機場行李提領資訊系統。 `BaggageInfo` 類別提供有關抵達班機及可提領各班機行李之轉盤的資訊。 下列範例會提供示範。

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

`BaggageHandler` 負責接收有關抵達班機和行李提領轉盤的資訊。 它在內部維護兩個集合：

- `observers` - 將接收更新資訊的用戶端集合。

- `flights` - 班機及其指派轉盤的集合。

這兩個集合都是由在 `BaggageHandler` 類別建構函式中執行個體化的泛型 <xref:System.Collections.Generic.List%601> 物件表示。 下列範例會顯示 `BaggageHandler` 類別的原始程式碼。

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

希望收到更新資訊的用戶端會呼叫 `BaggageHandler.Subscribe` 方法。 如果用戶端之前未訂閱通知，則會將用戶端的 <xref:System.IObserver%601> 實作參考加入 `observers` 集合。

您可以呼叫多載的 `BaggageHandler.BaggageStatus` 方法，以指出班機的行李正在卸載，或是已卸載完成。 在第一個案例中，會對方法傳遞一個班機號碼、班機的起飛機場，以及卸載行李的轉盤。 在第二個案例中，只會對方法傳遞一個班機號碼。 針對正在卸載的行李，這個方法會檢查傳遞給方法的 `BaggageInfo` 資訊是否存在於 `flights` 集合中。 如果不存在，則這個方法會加入資訊並且呼叫每個觀察者的 `OnNext` 方法。 針對行李已卸載完成的班機，這個方法會檢查該班機的資訊是否已儲存至 `flights` 集合中。 如果已儲存，則這個方法會呼叫每個觀察者的 `OnNext` 方法，並且從 `flights` 集合中移除 `BaggageInfo` 物件。

當天最後一個班機降落且其行李已處理完成時，就會呼叫 `BaggageHandler.LastBaggageClaimed` 方法。 這個方法會呼叫每個觀察者的 `OnCompleted` 方法，指出所有通知已完成，然後清除 `observers` 集合。

提供者的 <xref:System.IObservable%601.Subscribe%2A> 方法會傳回 <xref:System.IDisposable> 實作，讓觀察者在呼叫 <xref:System.IObserver%601.OnCompleted%2A> 方法之前停止接收通知。 下列範例會顯示這個 `Unsubscriber(Of BaggageInfo)` 類別的原始程式碼。 當類別在 `BaggageHandler.Subscribe` 方法中執行個體化時，會對該類別傳遞 `observers` 集合的參考，以及對已加入集合之觀察者的參考。 這些參考會指派給區域變數。 呼叫物件的 `Dispose` 方法時，它會檢查觀察者是否仍存在於 `observers` 集合中；如果存在的話，則會移除觀察者。

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

下列範例提供名為 `ArrivalsMonitor` 的 <xref:System.IObserver%601> 實作，其為顯示行李提領資訊的基底類別。 資訊會依照起飛城市名稱的英文字母順序顯示。 `ArrivalsMonitor` 的方法會標記為 `overridable` (在 Visual Basic 中) 或 `virtual` (在 C# 中)，如此衍生類別就能一次覆寫所有方法。

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor` 類別包含 `Subscribe` 和 `Unsubscribe` 方法。 `Subscribe` 方法可讓類別將呼叫 <xref:System.IObservable%601.Subscribe%2A> 所傳回的 <xref:System.IDisposable> 實作儲存至私用變數。 `Unsubscribe` 方法可讓類別藉由呼叫提供者的 <xref:System.IDisposable.Dispose%2A> 實作來取消訂閱通知。 `ArrivalsMonitor` 還提供 <xref:System.IObserver%601.OnNext%2A>、<xref:System.IObserver%601.OnError%2A> 和 <xref:System.IObserver%601.OnCompleted%2A> 方法的實作。 只有 <xref:System.IObserver%601.OnNext%2A> 實作會包含大量程式碼。 這個方法可處理私用且已排序的泛型 <xref:System.Collections.Generic.List%601> 物件，該物件會維護有關抵達班機的起飛機場以及可提領其行李之轉盤的資訊。 如果 `BaggageHandler` 類別報告有新班機抵達，則 <xref:System.IObserver%601.OnNext%2A> 方法實作會將該班機的相關資訊加入清單中。 如果 `BaggageHandler` 類別報告班機的行李已卸載完畢，則 <xref:System.IObserver%601.OnNext%2A> 方法會從清單中移除該班機。 只要發生變更，清單就會排序並顯示於主控台上。

下列範例包含執行個體化 `BaggageHandler` 類別及 `ArrivalsMonitor` 類別之兩個執行個體的應用程式進入點，並且使用 `BaggageHandler.BaggageStatus` 方法加入和移除抵達班機的相關資訊。 在每個案例中，觀察者都會接收更新並且正確顯示行李提領資訊。

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>相關主題

|標題|說明|
|-----------|-----------------|
|[觀察者設計模式最佳做法](../../../docs/standard/events/observer-design-pattern-best-practices.md)|描述開發實作觀察者設計模式的應用程式時，所採用的最佳做法。|
|[如何：實作提供者](../../../docs/standard/events/how-to-implement-a-provider.md)|提供溫度監控應用程式的提供者逐步實作。|
|[如何：實作觀察者](../../../docs/standard/events/how-to-implement-an-observer.md)|提供溫度監控應用程式的觀察者逐步實作。|
