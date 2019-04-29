---
title: 雙重緩衝的圖形
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: 20ec03e6b84110f7ea00c134dc18b23f233c5f58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756009"
---
# <a name="double-buffered-graphics"></a>雙重緩衝的圖形
閃爍是編寫圖形程式碼時常見的問題。 需要多個複雜繪製作業的圖形作業可能會導致轉譯的影像出現閃爍，或具有無法接受的外觀。 為了解決這些問題，.NET Framework 提供雙重緩衝的存取。  
  
 雙重緩衝會使用記憶體緩衝區來解決多個與繪製作業建立關聯的閃爍問題。 啟用雙重緩衝時，會將所有繪製作業都轉譯到記憶體緩衝區，而不是螢幕上的繪圖介面。 在所有繪製作業都完成之後，會直接將記憶體緩衝區複製到與其建立關聯的繪圖介面。 因為只對螢幕執行一個圖形作業，所以可排除與複雜繪製作業建立關聯的影像閃爍。  
  
## <a name="default-double-buffering"></a>預設雙重緩衝  
 在應用程式中使用雙重緩衝的最簡單方式，是使用 .NET Framework 所提供之表單和控制項的預設雙重緩衝。 您可以啟用預設雙重緩衝的 Windows Form，並藉由設定撰寫 Windows 控制項<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性，以`true`或使用<xref:System.Windows.Forms.Control.SetStyle%2A>方法。 如需詳細資訊，請參閱[如何：減少使用表單和控制項的雙重緩衝的圖形重繪閃動](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)。  
  
## <a name="manually-managing-buffered-graphics"></a>手動管理已緩衝的圖形  
 若是動畫或進階記憶體管理這類更進階雙重緩衝案例，您可以使用 .NET Framework 類別來實作您自己的雙重緩衝邏輯。 負責配置和管理個別圖形緩衝區的類別是<xref:System.Drawing.BufferedGraphicsContext>類別。 每個應用程式網域有它自己的預設值<xref:System.Drawing.BufferedGraphicsContext>管理所有預設雙重緩衝該應用程式的執行個體。 在大部分情況下會有一個應用程式定義域，每個應用程式，因此通常是一個預設<xref:System.Drawing.BufferedGraphicsContext>每個應用程式。 預設值<xref:System.Drawing.BufferedGraphicsContext>執行個體由<xref:System.Drawing.BufferedGraphicsManager>類別。 您可以擷取預設值的參考<xref:System.Drawing.BufferedGraphicsContext>藉由呼叫的執行個體<xref:System.Drawing.BufferedGraphicsManager.Current%2A>。 您也可以建立專用<xref:System.Drawing.BufferedGraphicsContext>執行個體，以改善大量繪圖應用程式的效能。 如需如何建立<xref:System.Drawing.BufferedGraphicsContext>執行個體，請參閱[How to:手動管理已緩衝的圖形](how-to-manually-manage-buffered-graphics.md)。  
  
## <a name="manually-displaying-buffered-graphics"></a>手動顯示已緩衝的圖形  
 您可以使用的執行個體<xref:System.Drawing.BufferedGraphicsContext>類別來建立圖形緩衝區，藉由呼叫<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>，它會傳回的執行個體<xref:System.Drawing.BufferedGraphics>類別。 A<xref:System.Drawing.BufferedGraphics>物件會管理轉譯介面，例如表單或控制項相關聯的記憶體緩衝區。  
  
 它會具現化之後，<xref:System.Drawing.BufferedGraphics>類別會管理轉譯到記憶體內圖形緩衝區。 您可以將圖形轉譯到記憶體緩衝區，透過<xref:System.Drawing.BufferedGraphics.Graphics%2A>，以公開<xref:System.Drawing.Graphics>直接代表記憶體緩衝區的物件。 您可以繪製至這個<xref:System.Drawing.Graphics>物件，就像您一樣以<xref:System.Drawing.Graphics>物件，表示繪圖介面。 所有圖形都繪製到緩衝區之後，您可以使用<xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType>緩衝區的內容複製到螢幕上的繪圖介面。  
  
 如需有關使用<xref:System.Drawing.BufferedGraphics>類別，請參閱[手動轉譯已緩衝的圖形](how-to-manually-render-buffered-graphics.md)。 如需轉譯圖形的詳細資訊，請參閱 [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.BufferedGraphics>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphicsManager>
- [如何：手動轉譯已緩衝的圖形](how-to-manually-render-buffered-graphics.md)
- [如何：減少使用表單和控制項的雙重緩衝的圖形重繪閃動](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)
- [如何：手動管理已緩衝的圖形](how-to-manually-manage-buffered-graphics.md)
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
