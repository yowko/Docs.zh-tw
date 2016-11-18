---
title: "清除 Unmanaged 資源"
description: "清除 Unmanaged 資源"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8c97c3e2-8619-47ce-ae29-d6a3140bfa83
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: c0600eb27c27261f6496fb45310514f7f716b3b3

---

# <a name="cleaning-up-unmanaged-resources"></a>清除 Unmanaged 資源

對於應用程式所建立的大部分物件而言，您都可以依賴 .NET 記憶體回收行程處理記憶體管理。 但是，當您建立包含 Unmanaged 資源的物件時，必須在應用程式使用完這些資源後明確地釋放它們。 最常見的 Unmanaged 資源類型就是包裝作業系統資源的物件，例如檔案、視窗、網路連接或資料庫連接都屬於這類資源。 雖然記憶體回收行程能夠追蹤封裝 Unmanaged 資源的物件存留期，但是它並不知道如何釋放和清除 Unmanaged 資源。 

如果您的類型使用 Unmanaged 資源，則應該執行下列作業： 

* 實作處置模式。 這樣會要求您提供 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 實作以便將 Unmanaged 資源進行決定性的釋放。 類型的消費者會在不再需要物件與其使用的資源時呼叫 [Dispose](xref:System.IDisposable.Dispose)。 [Dispose](xref:System.IDisposable.Dispose) 方法會立即釋放 Unmanaged 資源。 

* 提供的用途是在您的類型消費者忘記呼叫 [Dispose](xref:System.IDisposable.Dispose) 時釋放 Unmanaged 資源。 執行這項作業的方法有兩種： 

    * 使用安全控制代碼包裝您的 Unmanaged 資源。 這是建議使用的技巧。 安全控制代碼衍生自 [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 類別，並且包含穩固的 [Finalize](xref:System.Object.Finalize) 方法。 當您使用安全控制代碼時，只要實作 [IDisposable](xref:System.IDisposable) 介面並且在 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 實作中呼叫安全控制代碼的 [Dispose](xref:System.IDisposable.Dispose) 方法即可。 如果未呼叫 [Dispose](xref:System.IDisposable.Dispose) 方法，記憶體回收行程會自動呼叫安全控制代碼的完成項。 

      -或-

    * 覆寫 [Object.Finalize](xref:System.Object.Finalize) 方法。 最終處理可在類型消費者未呼叫 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 以決定性的方式處理 Unmanaged 資源時，進行非決定性的 Unmanaged 資源釋放。 不過，由於物件最終處理可能是複雜且容易發生錯誤的作業，因此建議您使用安全控制代碼，而不要提供您自己的完成項。 

這樣類型的消費者就可以直接呼叫您的 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 實作來釋放 Unmanaged 資源所使用的記憶體。 當您正確實作 [Dispose](xref:System.IDisposable.Dispose) 方法時，安全控制代碼的 [Finalize](xref:System.Object.Finalize) 方法或是自有的 [Object.Finalize](xref:System.Object.Finalize) 方法覆寫便會成為一種防護措施，可在未呼叫 [Dispose](xref:System.IDisposable.Dispose) 方法時清除資源。 

## <a name="in-this-section"></a>本章節內容

[實作 Dispose 方法](implementing-dispose.md) - 描述如何實作處置模式以便釋放 Unmanaged 資源。

[使用實作 IDisposable 的物件](using-objects.md) - 描述類型消費者如何確保會呼叫其 Dispose 實作。 建議您使用 C# using 陳述式或 Visual Basic Using 陳述式執行這項作業。

## <a name="reference"></a>參考資料

[System.IDisposable](xref:System.IDisposable) - 定義用於釋放 Unmanaged 資源的 `Dispose` 方法。

[Object.Finalize](xref:System.Object.Finalize) - 提供的用途是在 `Dispose` 方法未釋放 Unmanaged 資源時，進行物件最終處理。 

[GC.SuppressFinalize](xref:System.GC#System_GC_SuppressFinalize_System_Object_) - 隱藏最終處理。 這個方法通常會從 `Dispose` 方法呼叫，以便防止執行完成項。 



<!--HONumber=Nov16_HO3-->


