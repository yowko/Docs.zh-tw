---
title: 使用 IAsyncResult 呼叫非同步方法
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830450"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>使用 IAsyncResult 呼叫非同步方法

.NET 程式庫和協力廠商類別庫中的類型可以提供方法，讓應用程式在主應用程式執行緒以外的執行緒中執行非同步作業時，繼續執行。 下列各節說明並提供示範不同方式的程式碼範例，您可以呼叫使用 <xref:System.IAsyncResult> 設計模式的非同步方法。  
  
- 藉[由結束非同步作業來封鎖應用程式執行](blocking-application-execution-by-ending-an-async-operation.md)。  
  
- [使用 AsyncWaitHandle 封鎖應用程式執行](blocking-application-execution-using-an-asyncwaithandle.md)。  
  
- [輪詢非同步作業的狀態](polling-for-the-status-of-an-asynchronous-operation.md)。  
  
- [使用 AsyncCallback 委派結束非同步作業](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="see-also"></a>請參閱

- [事件架構非同步模式 (EAP)](event-based-asynchronous-pattern-eap.md)
- [事件架構非同步模式概觀](event-based-asynchronous-pattern-overview.md)
