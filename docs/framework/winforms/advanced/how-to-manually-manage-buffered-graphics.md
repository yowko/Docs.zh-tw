---
title: 如何：手動管理已緩衝的圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: f8675582fe6bafefd94d6a740c3263e407dfd4e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523951"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>如何：手動管理已緩衝的圖形
您可以使用更進階的雙重緩衝狀況，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]類別以實作您自己的雙重緩衝邏輯。 類別負責配置及管理個別圖形緩衝區是<xref:System.Drawing.BufferedGraphicsContext>類別。 每個應用程式有自己的預設值<xref:System.Drawing.BufferedGraphicsContext>，管理所有的預設應用程式的雙重緩衝。 您可以藉由呼叫擷取此執行個體的參考<xref:System.Drawing.BufferedGraphicsManager.Current%2A>。  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>若要取得預設 BufferedGraphicsContext 的參考  
  
-   設定<xref:System.Drawing.BufferedGraphicsManager.Current%2A>屬性，如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  您不需要呼叫`Dispose`方法<xref:System.Drawing.BufferedGraphicsContext>參考，您會收到<xref:System.Drawing.BufferedGraphicsManager>類別。 <xref:System.Drawing.BufferedGraphicsManager>會處理所有的記憶體配置和預設散發<xref:System.Drawing.BufferedGraphicsContext>執行個體。  
  
     等動畫大量繪圖功能的應用程式，您有時可以改善效能使用專用<xref:System.Drawing.BufferedGraphicsContext>而不是<xref:System.Drawing.BufferedGraphicsContext>提供<xref:System.Drawing.BufferedGraphicsManager>。 這可讓您建立及管理圖形緩衝區個別，而不會管理所有其他已緩衝的圖形應用程式相關聯，但應用程式所耗用的記憶體更大的效能負荷。  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>若要建立專用的 BufferedGraphicsContext  
  
-   宣告和建立的新執行個體<xref:System.Drawing.BufferedGraphicsContext>類別，如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [操作說明：手動轉譯已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
