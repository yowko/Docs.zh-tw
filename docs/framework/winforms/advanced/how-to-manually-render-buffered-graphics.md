---
title: "如何：手動呈現已緩衝的圖形"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3a5d06da3a398782b0285fb55807df5832cf771
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a>如何：手動呈現已緩衝的圖形
如果您在管理自己的已緩衝圖形，將需要能夠建立及呈現圖形緩衝區。 您可以藉由呼叫類別 <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> 方法，針對與螢幕上繪圖介面相關聯的 <xref:System.Drawing.BufferedGraphics> 類別建立其執行個體。 這個方法會建立與特定轉譯介面 (例如表單或控制項) 相關聯之  <xref:System.Drawing.BufferedGraphics> 的執行個體。 建立 <xref:System.Drawing.BufferedGraphics> 執行個體之後，您可以透過 <xref:System.Drawing.BufferedGraphics.Graphics%2A> 屬性，繪製圖形到它所代表的緩衝區。 在您執行所有圖形作業之後，可以藉由呼叫 <xref:System.Drawing.BufferedGraphics.Render%2A> 方法，將緩衝區的內容複製到螢幕上。  
  
> [!NOTE]
>  如果您執行您自己的轉譯，將會增加記憶體耗用量，不過可能只會稍微增加。  
  
### <a name="to-manually-display-buffered-graphics"></a>手動顯示已緩衝的圖形  
  
1.  取得 <xref:System.Drawing.BufferedGraphicsContext> 類別執行個體的參考。 如需詳細資訊，請參閱[How to： 手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)。  
  
2.  藉由呼叫 <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> 方法，建立 <xref:System.Drawing.BufferedGraphics> 類別的執行個體，如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  藉由設定 <xref:System.Drawing.BufferedGraphics.Graphics%2A> 屬性，繪製圖形至圖形緩衝區。 例如:   
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  當您完成對圖形緩衝區的所有繪圖作業時，請呼叫 <xref:System.Drawing.BufferedGraphics.Render%2A> 方法以轉譯緩衝區，不論是轉譯到與該緩衝區關聯的繪圖介面，或是指定的繪圖介面，如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  完成轉譯圖形之後，請對 <xref:System.Drawing.BufferedGraphics> 執行個體呼叫 `Dispose` 方法以釋放系統資源。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [操作說明：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
