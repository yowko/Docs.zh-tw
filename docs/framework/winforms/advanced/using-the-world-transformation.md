---
title: "使用全局轉換"
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
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5b2a8de0644e71a5e6ae1a5ca796f580f0c4f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-world-transformation"></a>使用全局轉換
全局轉換是屬性的<xref:System.Drawing.Graphics>類別。 指定全局轉換的數字會儲存在<xref:System.Drawing.Drawing2D.Matrix>物件，代表 3 × 3 矩陣。 <xref:System.Drawing.Drawing2D.Matrix>和<xref:System.Drawing.Graphics>類別有數種方法來設定數字的自然變換矩陣中。  
  
## <a name="different-types-of-transformations"></a>不同類型的轉換  
 在下列範例中，程式碼，先建立 50 × 50 矩形，並放在原點 （0，0）。 原點是在工作區的左上角。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 下列程式碼適用於 1.75 x 方向的因數來展開矩形，並壓縮矩形，因數為 0.5，在 y 方向縮放轉換：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 結果是一個矩形在 x 方向較長且少於 y 方向的原始。  
  
 若要旋轉的矩形，而不是調整它，請使用下列程式碼：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 若要翻譯的矩形，請使用下列程式碼：  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [使用 Managed GDI+ 中的轉換](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
