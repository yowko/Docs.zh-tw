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
ms.openlocfilehash: 88ca1b5bfbb8bfbdfef01dea8af07c5d56784c5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289911"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>使用 IAsyncResult 呼叫非同步方法
.NET Framework 和協力廠商類別程式庫中的型別提供的方法，可讓應用程式在主應用程式執行緒以外的執行緒中執行非同步作業時繼續執行。 下列各節說明並提供示範不同方式的程式碼範例，您可以呼叫使用 <xref:System.IAsyncResult> 設計模式的非同步方法。  
  
- 藉[由結束非同步作業來封鎖應用程式執行](blocking-application-execution-by-ending-an-async-operation.md)。  
  
- [使用 AsyncWaitHandle 封鎖應用程式執行](blocking-application-execution-using-an-asyncwaithandle.md)。  
  
- [輪詢非同步作業的狀態](polling-for-the-status-of-an-asynchronous-operation.md)。  
  
- [使用 AsyncCallback 委派結束非同步作業](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。  
  
## <a name="see-also"></a>另請參閱

- [事件架構非同步模式 (EAP)](event-based-asynchronous-pattern-eap.md)
- [事件架構非同步模式概觀](event-based-asynchronous-pattern-overview.md)
