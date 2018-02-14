---
title: "如何：明確擲回例外狀況"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a>如何明確擲回例外狀況

您可以使用 `throw` 陳述式，明確擲回例外狀況。 您也可以使用 `throw` 陳述式，再次擲回所攔截的例外狀況。 建議您撰寫程式碼，將資訊加入要重新擲回的例外狀況，以在偵錯時提供更多資訊。

下列程式碼範例使用 `try`/`catch` 區塊來攔截可能的 <xref:System.IO.FileNotFoundException>。 `try` 區塊後面會接著 `catch` 區塊，該區塊可在找不到資料檔案時攔截 <xref:System.IO.FileNotFoundException>，並將訊息寫入主控台。 下一個陳述式是 `throw` 陳述式，會擲回新的 <xref:System.IO.FileNotFoundException> ，並將文字資訊新增到例外狀況。

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>請參閱  
[例外狀況](index.md)
