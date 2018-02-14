---
title: "如何：使用 Finally 區塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 325be4836d661369326fbe3ea1f8b252bf251f3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-finally-blocks"></a>如何使用 finally 區塊

發生例外狀況時，執行會停止，並將控制權交給適當的例外狀況處理常式。 這通常表示會略過您預期要執行的程式碼行。 某些資源清除作業 (例如關閉檔案) 即使擲回例外狀況也必須執行。 若要這樣做，您可以使用 `finally` 區塊。 `finally` 區塊永遠會執行，而不論是否擲回例外狀況。

下列程式碼範例使用 `try`/`catch` 區塊來攔截 <xref:System.ArgumentOutOfRangeException>。 `Main` 方法會建立兩個陣列，並嘗試將其中一個陣列複製到另一個陣列。 此動作會產生 <xref:System.ArgumentOutOfRangeException>，並會將錯誤寫入主控台。 不論複製動作的結果為何，`finally` 區塊都會執行。

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>請參閱  
[例外狀況](index.md)   
