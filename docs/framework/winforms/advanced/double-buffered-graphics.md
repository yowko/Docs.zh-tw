---
title: "雙重緩衝的圖形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89413e0958366dd39c62bfaedb7e36471123bc22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="double-buffered-graphics"></a>雙重緩衝的圖形
閃爍是編寫圖形程式碼時常見的問題。 需要多個複雜繪製作業的圖形作業可能會導致轉譯的影像出現閃爍，或具有無法接受的外觀。 為了解決這些問題，.NET Framework 提供雙重緩衝的存取。  
  
 雙重緩衝會使用記憶體緩衝區來解決多個與繪製作業建立關聯的閃爍問題。 啟用雙重緩衝時，會將所有繪製作業都轉譯到記憶體緩衝區，而不是螢幕上的繪圖介面。 在所有繪製作業都完成之後，會直接將記憶體緩衝區複製到與其建立關聯的繪圖介面。 因為只對螢幕執行一個圖形作業，所以可排除與複雜繪製作業建立關聯的影像閃爍。  
  
## <a name="default-double-buffering"></a>預設雙重緩衝  
 在應用程式中使用雙重緩衝的最簡單方式，是使用 .NET Framework 所提供之表單和控制項的預設雙重緩衝。 您可以啟用 Windows Form 的雙重緩衝的預設值，並撰寫 Windows 控制項，藉由設定<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性`true`或使用<xref:System.Windows.Forms.Control.SetStyle%2A>方法。 如需詳細資訊，請參閱[如何：使用表單和控制項的雙重緩衝以減少圖形閃爍](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)。  
  
## <a name="manually-managing-buffered-graphics"></a>手動管理已緩衝的圖形  
 若是動畫或進階記憶體管理這類更進階雙重緩衝案例，您可以使用 .NET Framework 類別來實作您自己的雙重緩衝邏輯。 類別負責配置及管理個別圖形緩衝區是<xref:System.Drawing.BufferedGraphicsContext>類別。 每個應用程式網域有它自己的預設值<xref:System.Drawing.BufferedGraphicsContext>管理所有該應用程式的雙重緩衝的預設執行個體。 在大部分情況下會有一個應用程式定義域，每個應用程式，因此通常是一個預設<xref:System.Drawing.BufferedGraphicsContext>每個應用程式。 預設<xref:System.Drawing.BufferedGraphicsContext>執行個體由<xref:System.Drawing.BufferedGraphicsManager>類別。 您可以擷取預設的參考<xref:System.Drawing.BufferedGraphicsContext>藉由呼叫的執行個體<xref:System.Drawing.BufferedGraphicsManager.Current%2A>。 您也可以建立專用<xref:System.Drawing.BufferedGraphicsContext>執行個體，這可以改善大量繪圖功能的應用程式的效能。 如需有關如何建立詳細<xref:System.Drawing.BufferedGraphicsContext>執行個體，請參閱[How to： 手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)。  
  
## <a name="manually-displaying-buffered-graphics"></a>手動顯示已緩衝的圖形  
 您可以使用的執行個體<xref:System.Drawing.BufferedGraphicsContext>類別來建立圖形緩衝區藉由呼叫<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>，它會傳回的執行個體<xref:System.Drawing.BufferedGraphics>類別。 A<xref:System.Drawing.BufferedGraphics>物件管理的呈現表面，例如表單或控制項相關聯的記憶體緩衝區。  
  
 具現化之後，<xref:System.Drawing.BufferedGraphics>類別管理的記憶體中的圖形緩衝區的呈現。 您可以呈現圖形記憶體緩衝區中，透過<xref:System.Drawing.BufferedGraphics.Graphics%2A>，哪一個公開<xref:System.Drawing.Graphics>直接代表記憶體緩衝區的物件。 您可以繪製至這個<xref:System.Drawing.Graphics>物件就和您對<xref:System.Drawing.Graphics>代表繪圖介面的物件。 所有圖形都已都繪製緩衝區之後，您可以使用<xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType>將緩衝區的內容複製到螢幕上的繪圖介面。  
  
 如需有關使用<xref:System.Drawing.BufferedGraphics>類別，請參閱[手動呈現已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)。 如需轉譯圖形的詳細資訊，請參閱 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [操作說明：手動轉譯已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [操作說明：使用表單和控制項的雙重緩衝以減少圖形閃爍](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [操作說明：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
