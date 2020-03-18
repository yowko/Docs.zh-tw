---
title: 使用 IAsyncResult 呼叫非同步方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121319"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>使用 IAsyncResult 呼叫非同步方法
.NET Framework 和協力廠商類別程式庫中的型別提供的方法，可讓應用程式在主應用程式執行緒以外的執行緒中執行非同步作業時繼續執行。 下列各節說明並提供示範不同方式的程式碼範例，您可以呼叫使用 <xref:System.IAsyncResult> 設計模式的非同步方法。  
  
- [通過結束非同步作業來阻止應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)。  
  
- [使用非同步WaitHandle阻止應用程式執行](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)。  
  
- [輪詢非同步作業的狀態](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)。  
  
- [使用非同步回檔委託結束非同步作業](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="see-also"></a>另請參閱

- [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
