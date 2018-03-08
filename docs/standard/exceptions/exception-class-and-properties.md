---
title: "Exception 類別和屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 120d56832aad5024ee607d6e3114f164c967a12f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="exception-class-and-properties"></a>Exception 類別和屬性

<xref:System.Exception> 類別是例外狀況所繼承的基底類別。 例如 <xref:System.InvalidCastException> 類別的階層如下：

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> 類別具有下列屬性，讓您更容易了解例外狀況。

| 屬性名稱 | 描述 |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> 會將任意資料保存在索引鍵/值組。 |
| <xref:System.Exception.HelpLink> | 可保留說明檔的 URL (或 URN)，以提供有關例外狀況原因的廣泛資訊。 |
| <xref:System.Exception.InnerException> | 您可以在例外狀況處理期間，使用此屬性來建立及保留一系列的例外狀況。 您可以使用此屬性來建立新的例外狀況，其中包含先前攔截例外狀況。 <xref:System.Exception.InnerException> 屬性中的第二個例外狀況可以擷取原始的例外狀況，讓程式碼可以處理第二個例外狀況，以檢視其他額外的資訊。 例如，假設您有一個方法會接收格式不正確的引數。  此程式碼會嘗試讀取引數，但擲回例外狀況。 此方法會攔截例外狀況並擲回 <xref:System.FormatException>。 為了改善呼叫端判斷所擲回例外狀況原因的能力，有時需要讓方法攔截 Helper 常式所擲回的例外狀況，再擲回更清楚指出所發生錯誤的例外狀況。 您可以建立全新且更有意義的例外狀況，其中的內部例外狀況參考可設定為原始例外狀況。 這個更有意義的例外狀況接著會擲回給呼叫端。 請注意，透過這項功能，您可以建立一系列的連結例外狀況，每個例外狀況後面接著先前擲回的例外狀況。 |
| <xref:System.Exception.Message> | 提供有關例外狀況原因的詳細資料。
| <xref:System.Exception.Source> | 取得或設定造成錯誤的應用程式或物件的名稱。 |
| <xref:System.Exception.StackTrace>| 包含可用來判斷發生錯誤位置的堆疊追蹤。 堆疊追蹤包括原始程式檔名稱和程式行號 (若有偵錯資訊的話)。 |

大部分繼承自 <xref:System.Exception> 的類別不會實作其他成員或提供其他功能；它們只會繼承自 <xref:System.Exception>。 因此，您可以在例外狀況類別階層架構、例外狀況名稱和例外狀況所包含的資訊中，找到例外狀況的最重要資訊。

建議只擲回及攔截衍生自 <xref:System.Exception> 的物件，但您可以擲回任何衍生自 <xref:System.Object> 類別的物件作為例外狀況。 請注意，並非所有語言都能擲回及攔截不是衍生自 <xref:System.Exception> 的物件。
  
## <a name="see-also"></a>請參閱  
[例外狀況](index.md)
