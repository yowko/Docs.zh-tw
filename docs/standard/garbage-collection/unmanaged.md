---
title: "清除 Unmanaged 資源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c94a449edbbe38c4028e27fd946b66a054badf51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cleaning-up-unmanaged-resources"></a>清除 Unmanaged 資源
對於大部分的應用程式所建立的物件，您可以依賴。網路的記憶體回收行程處理記憶體管理。 但是，當您建立包含 Unmanaged 資源的物件時，必須在應用程式使用完這些資源後明確地釋放它們。 最常見的 Unmanaged 資源類型就是包裝作業系統資源的物件，例如檔案、視窗、網路連接或資料庫連接都屬於這類資源。 雖然記憶體回收行程能夠追蹤封裝 Unmanaged 資源的物件存留期，但是它並不知道如何釋放和清除 Unmanaged 資源。  
  
 如果您的類型使用 Unmanaged 資源，則應該執行下列作業：  
  
-   實作[處置模式](../../../docs/standard/design-guidelines/dispose-pattern.md)。 這樣會要求您提供 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作以便將 Unmanaged 資源進行決定性的釋放。 類型的消費者會在不再需要物件與其使用的資源時呼叫 <xref:System.IDisposable.Dispose%2A>。 <xref:System.IDisposable.Dispose%2A> 方法會立即釋放 Unmanaged 資源。  
  
-   提供的用途是在您的類型消費者忘記呼叫 <xref:System.IDisposable.Dispose%2A> 時釋放 Unmanaged 資源。 執行這項作業的方法有兩種：  
  
    -   使用安全控制代碼包裝您的 Unmanaged 資源。 這是建議使用的技巧。 安全控制代碼衍生自 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 類別，並且包括穩固的 <xref:System.Object.Finalize%2A> 方法。 當您使用安全控制代碼時，只要實作 <xref:System.IDisposable> 介面並且在 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 實作中呼叫安全控制代碼的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法即可。 如果未呼叫 <xref:System.IDisposable.Dispose%2A> 方法，記憶體回收行程會自動呼叫安全控制代碼的完成項。  
  
         -或-  
  
    -   覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法。 最終處理可在類型消費者未呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 以決定性的方式處理 Unmanaged 資源時，進行非決定性的 Unmanaged 資源釋放。 不過，由於物件最終處理可能是複雜且容易發生錯誤的作業，因此建議您使用安全控制代碼，而不要提供您自己的完成項。  
  
 這樣類型的消費者就可以直接呼叫您的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作來釋放 Unmanaged 資源所使用的記憶體。 當您正確實作 <xref:System.IDisposable.Dispose%2A> 方法時，安全控制代碼的 <xref:System.Object.Finalize%2A> 方法或是自有的 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法覆寫便會成為一種防護措施，可在未呼叫 <xref:System.IDisposable.Dispose%2A> 方法時清除資源。  
  
## <a name="in-this-section"></a>本章節內容  
 [實作 Dispose 方法](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 描述如何實作[處置模式](../../../docs/standard/design-guidelines/dispose-pattern.md)用於釋放 unmanaged 的資源。  
  
 [使用實作 IDisposable 的物件](../../../docs/standard/garbage-collection/using-objects.md)  
 描述類型消費者如何確保會呼叫其 <xref:System.IDisposable.Dispose%2A> 實作。 建議您使用 C# `using` 陳述式或 Visual Basic `Using` 陳述式執行這項作業。  
  
## <a name="reference"></a>參考資料  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 定義用於釋放 Unmanaged 資源的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 提供的用途是在 <xref:System.IDisposable.Dispose%2A> 方法未釋放 Unmanaged 資源時，進行物件最終處理。  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 隱藏最終處理。 這個方法通常會從 `Dispose` 方法呼叫，以便防止執行完成項。
