---
title: 圖形和繪圖
description: 瞭解圖形、畫筆、筆刷和色彩物件，以及如何執行如繪製圖形、繪製文字，或在 Windows Forms 中顯示影像之類的工作。
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618398"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Windows Form 中的圖形和繪圖
通用語言執行平臺會使用稱為 GDI + 的 Windows 圖形裝置介面（GDI）的先進實作為。 使用 GDI +，您可以建立圖形、繪製文字，並將圖形影像當做物件來操作。 GDI + 的設計可提供效能和方便使用。 您可以使用 GDI + 在 Windows Forms 和控制項上轉譯圖形影像。 雖然您無法直接在 Web Forms 上使用 GDI +，但是您可以透過影像 Web 服務器控制項顯示圖形影像。  
  
 在本節中，您會找到介紹 GDI + 程式設計基本概念的主題。 雖然本節不是完整的參考，但包含 <xref:System.Drawing.Graphics>、<xref:System.Drawing.Pen>、<xref:System.Drawing.Brush> 和 <xref:System.Drawing.Color> 物件的相關資訊，並說明如何執行繪製圖案、繪製文字或顯示影像等工作。 如需詳細資訊，請參閱[Gdi + 參考](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference)。  
  
 如果您想要參與並立即開始，請參閱[圖形程式設計入門](getting-started-with-graphics-programming.md)。 它包含如何使用程式碼在 Windows 表單上繪製線條、圖形、文字和其他項目的主題。  
  
## <a name="in-this-section"></a>本節內容  
 [圖形概觀](graphics-overview-windows-forms.md)  
 介紹與圖形相關的 Managed 類別。  
  
 [關於 GDI+ Managed 程式碼](about-gdi-managed-code.md)  
 提供 managed GDI + 類別的相關資訊。  
  
 [使用 Managed 圖形類別](using-managed-graphics-classes.md)  
 示範如何使用 GDI + managed 類別完成各種工作。  
  
## <a name="reference"></a>參考  
 <xref:System.Drawing>  
 提供對 GDI + 基本圖形功能的存取。  
  
 <xref:System.Drawing.Drawing2D>  
 提供進階二維和向量圖形功能。  
  
 <xref:System.Drawing.Imaging>  
 提供 advanced GDI + 影像處理功能。  
  
 <xref:System.Drawing.Text>  
 提供 advanced GDI + 印刷樣式功能。 這個命名空間中的類別可以用來建立及使用字型集合。  
  
 <xref:System.Drawing.Printing>  
 提供列印功能。  
  
## <a name="related-sections"></a>相關章節  
 [自訂控制項繪製和轉譯](../controls/custom-control-painting-and-rendering.md)  
 詳細說明如何提供繪製控制項的程式碼。
