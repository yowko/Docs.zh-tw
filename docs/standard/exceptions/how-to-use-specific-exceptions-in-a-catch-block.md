---
title: 如何：使用 Catch 區塊中的特定例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 424db46c879974a9859637f9a2a5dfcd4494a3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571794"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>如何使用 Catch 區塊中的特定例外狀況

一般而言，比起使用基本 `catch` 陳述式，攔截特定例外狀況類型會是更佳的程式設計做法。

發生例外狀況時，該例外狀況會在堆疊中向上傳遞，讓每個 catch 區塊都有機會處理。 Catch 陳述式的順序很重要。 請將針對特定例外狀況的 catch 區塊放在一般例外狀況的 catch 區塊之前，否則編譯器可能會發出錯誤。 藉由比對 catch 區塊中指定的例外狀況類型與例外狀況名稱，即可決定正確的 catch 區塊。 如果沒有特定 catch 區塊，則會由一般 catch 區塊 (如果有的話) 攔截例外狀況。

下列程式碼範例使用 `try`/`catch` 區塊來攔截 <xref:System.InvalidCastException>。 此範例會建立具有員工層級 (`Emlevel`) 之單一屬性的類別，稱為 `Employee`。 `PromoteEmployee` 方法會採用一個物件並遞增員工層級。 <xref:System.InvalidCastException> 會在 <xref:System.DateTime> 執行個體傳遞給 `PromoteEmployee` 方法時發生。

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a>請參閱  
[例外狀況](index.md)
