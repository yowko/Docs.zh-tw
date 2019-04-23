---
title: HOW TO：手動管理已緩衝的圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 965e3225f8cf1af6d61b81434089ebacac8ad13a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138667"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>HOW TO：手動管理已緩衝的圖形
您可以使用更進階雙重緩衝案例[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]類別以實作您自己的雙重緩衝邏輯。 負責配置和管理個別圖形緩衝區的類別是<xref:System.Drawing.BufferedGraphicsContext>類別。 每個應用程式有自己的預設值<xref:System.Drawing.BufferedGraphicsContext>可管理的所有預設雙重緩衝該應用程式。 您可以擷取此執行個體的參考，藉由呼叫<xref:System.Drawing.BufferedGraphicsManager.Current%2A>。  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>若要取得預設 BufferedGraphicsContext 的參考  
  
-   設定<xref:System.Drawing.BufferedGraphicsManager.Current%2A>屬性，如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  您不需要呼叫`Dispose`方法<xref:System.Drawing.BufferedGraphicsContext>參考，您會收到<xref:System.Drawing.BufferedGraphicsManager>類別。 <xref:System.Drawing.BufferedGraphicsManager>會處理所有的記憶體配置和預設值的分佈<xref:System.Drawing.BufferedGraphicsContext>執行個體。  
  
     大量繪圖應用程式，例如動畫，您有時可以改善效能使用專用<xref:System.Drawing.BufferedGraphicsContext>而非<xref:System.Drawing.BufferedGraphicsContext>所提供<xref:System.Drawing.BufferedGraphicsManager>。 這可讓您建立和個別管理圖形緩衝區，而不會產生管理所有其他已緩衝的圖形與您的應用程式相關聯，但應用程式所耗用的記憶體將會更高的效能負擔。  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>若要建立專用的 BufferedGraphicsContext  
  
-   宣告和建立的新執行個體<xref:System.Drawing.BufferedGraphicsContext>類別，如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.BufferedGraphicsContext>
- [雙重緩衝的圖形](double-buffered-graphics.md)
- [如何：手動轉譯已緩衝的圖形](how-to-manually-render-buffered-graphics.md)
