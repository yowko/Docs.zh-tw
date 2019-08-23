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
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968594"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>作法：手動管理已緩衝的圖形
針對更先進的雙重緩衝案例, 您可以使用 .NET Framework 類別來執行您自己的雙重緩衝處理邏輯。 負責配置和管理個別圖形緩衝區的類別是<xref:System.Drawing.BufferedGraphicsContext>類別。 每個應用程式都有<xref:System.Drawing.BufferedGraphicsContext>自己的預設值, 可管理該應用程式的所有預設雙重緩衝。 您可以藉由呼叫<xref:System.Drawing.BufferedGraphicsManager.Current%2A>來抓取這個實例的參考。  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>取得預設 BufferedGraphicsCoNtext 的參考  
  
- <xref:System.Drawing.BufferedGraphicsManager.Current%2A>設定屬性, 如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > 您不需要`Dispose` <xref:System.Drawing.BufferedGraphicsContext>在從<xref:System.Drawing.BufferedGraphicsManager>類別收到的參考上呼叫方法。 會處理預設<xref:System.Drawing.BufferedGraphicsContext>實例的所有記憶體配置和散發。 <xref:System.Drawing.BufferedGraphicsManager>  
  
     針對圖形密集的應用程式 (例如動畫), 您有時可以使用專用<xref:System.Drawing.BufferedGraphicsContext>而非所提供<xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsManager>的來改善效能。 這可讓您個別建立和管理圖形緩衝區, 而不會產生管理與應用程式相關聯的所有其他緩衝圖形的效能額外負荷, 不過應用程式所耗用的記憶體將會更大。  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>若要建立專用 BufferedGraphicsCoNtext  
  
- 宣告並建立<xref:System.Drawing.BufferedGraphicsContext>類別的新實例, 如下列程式碼範例所示。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.BufferedGraphicsContext>
- [雙重緩衝的圖形](double-buffered-graphics.md)
- [如何：手動呈現已緩衝的圖形](how-to-manually-render-buffered-graphics.md)
