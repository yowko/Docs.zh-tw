---
title: "如何：開啟並附加至記錄檔"
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a>如何：開啟並附加至記錄檔
<xref:System.IO.StreamWriter>和<xref:System.IO.StreamReader>寫入字元和從資料流讀取字元。 下列程式碼範例會開啟`log.txt`檔案輸入，或如果它不存在，並將資訊附加至檔案結尾建立檔案。 檔案的內容再寫入標準輸出顯示。 此範例的替代方法，為的資訊無法儲存成單一字串或字串陣列，而<xref:System.IO.File.WriteAllText%2A>或<xref:System.IO.File.WriteAllLines%2A>方法無法用來達成相同的功能。  
  
> [!NOTE]
>  Visual Basic 使用者可以選擇使用的方法和屬性所提供<xref:Microsoft.VisualBasic.Logging.Log>類別或<xref:Microsoft.VisualBasic.FileIO.FileSystem>類別來建立或寫入至記錄檔。  
  
## <a name="example"></a>範例  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [操作說明：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [如何：將字元寫入至字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)
