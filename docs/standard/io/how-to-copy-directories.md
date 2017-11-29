---
title: "如何：複製目錄"
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
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5602a4e227f3cd17e4a7c9a086bee69d3e3e506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-directories"></a>如何：複製目錄
本範例將示範如何使用 I/O 類別將某一個目錄的內容同步複製到另一個位置。 在此範例中，使用者可以指定是否要同時複製子目錄。 如果子目錄已複製，這個範例中的方法就會以遞迴方式複製子目錄，方法是在每個後續的子目錄上呼叫其本身，直到沒有其他要複製的子目錄為止。  
  
 如需以非同步方式複製檔案的範例，請參閱 [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [檔案和資料流 I/O](../../../docs/standard/io/index.md)  
 [一般 I/O 工作](../../../docs/standard/io/common-i-o-tasks.md)  
 [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)
