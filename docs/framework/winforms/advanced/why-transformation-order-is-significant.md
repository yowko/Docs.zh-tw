---
title: "為何轉換順序很重要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b170c9247b2415c724c1306a4c21d067c823b4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="why-transformation-order-is-significant"></a>為何轉換順序很重要
單一<xref:System.Drawing.Drawing2D.Matrix>物件可儲存單一轉換的序列。 後者稱為複合轉換。 取得複合的轉換矩陣乘以個別轉換的矩陣。  
  
## <a name="composite-transform-examples"></a>複合轉換範例  
 在複合轉換中，個別轉換的順序很重要的。 例如，如果第一次旋轉，再調整，然後轉譯，您取得不同的結果非先轉換，再旋轉，然後調整。 在[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，複合轉換建立從左到右。 如果 S、 R 和 T 分別是縮放、 旋轉和轉譯矩陣，然後產品 SRT （依該順序） 是複合的轉換矩陣的第一個標尺、 一個圖示旋轉，然後將轉譯。 產品所產生的矩陣 SRT 與不同產品 TRS 所產生的矩陣。  
  
 順序是很重要的其中一個原因是，完成像旋轉和縮放轉換，以根據座標系統的原點。 縮放的中心位於原點的物件產生不同的結果調整已移開原點的物件。 同樣地，旋轉的中心位於原點的物件所產生的旋轉已移開原點的物件不同的結果。  
  
 下列範例會結合以形成複合轉換縮放、 旋轉和轉譯 （依該順序）。 引數<xref:System.Drawing.Drawing2D.MatrixOrder.Append>傳遞至<xref:System.Drawing.Graphics.RotateTransform%2A>方法表示旋轉會遵循縮放比例。 同樣地，引數<xref:System.Drawing.Drawing2D.MatrixOrder.Append>傳遞至<xref:System.Drawing.Graphics.TranslateTransform%2A>方法表示轉譯會遵循旋轉。 <xref:System.Drawing.Drawing2D.MatrixOrder.Append>和<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>屬於<xref:System.Drawing.Drawing2D.MatrixOrder>列舉型別。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 下列範例使如同上述範例中，相同的方法呼叫，但呼叫的順序相反。 產生作業的順序會先轉換再旋轉，則小數位數，會產生第一個標尺非常不同的結果，再更換，然後轉換。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 複合轉換中的個別轉換的順序互換的其中一種方式是一系列的方法呼叫的順序互換。 控制作業的順序的第二個方式是變更矩陣的 order 引數。 下列範例是上述範例中，不同處在於相同<xref:System.Drawing.Drawing2D.MatrixOrder.Append>已變更為<xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>。 SRT，其中 S、 R、 T 縮放、 旋轉矩陣並分別將轉譯的順序是矩陣乘法。 複合轉換的順序會是第一個標尺，再旋轉，然後轉換。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 前一個範例的結果是相同的此主題中的第一個範例的結果。 這是因為我們反轉方法呼叫的順序和矩陣乘法的順序。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [使用 Managed GDI+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
