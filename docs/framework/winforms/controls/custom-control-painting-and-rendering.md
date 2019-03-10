---
title: 自訂控制項繪製和轉譯
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: ec9002ffa4a7e2c82f59d52344764a01afe4c568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722135"
---
# <a name="custom-control-painting-and-rendering"></a>自訂控制項繪製和轉譯
自訂繪製的控制項是其中一個輕鬆使用.NET framework 的許多複雜工作。 當撰寫自訂控制項，您會有相關控制項的圖形化外觀的許多選項。 如果您撰寫控制項是繼承自`Control`，您必須提供可讓您的控制項來呈現其圖形表示法的程式碼。 如果您要建立使用者控制項繼承自`UserControl`，繼承或從其中一個 Windows Form 控制項，您可能會覆寫標準的圖形化表示法，並提供您自己的圖形程式碼。 如果您想要提供的構成控制項的自訂轉譯`UserControl`您撰寫時，選項變得較少，但仍然允許廣泛的圖形化的能力，為您的控制項和應用程式。  
  
## <a name="in-this-section"></a>本節內容  
 [呈現 Windows Forms 控制項](rendering-a-windows-forms-control.md)  
 示範如何撰寫程式顯示控制項的邏輯。  
  
 [使用者自訂描繪控制項](user-drawn-controls.md)  
 提供撰寫和覆寫控制項的轉譯程式碼所需的步驟的概觀。  
  
 [組成控制項](constituent-controls.md)  
 描述如何在您的使用者控制項和表單中實作的組成控制項的自訂轉譯程式碼。  
  
 [如何：在執行階段隱藏控制項](how-to-make-your-control-invisible-at-run-time.md)  
 示範如何使用<xref:System.Windows.Forms.Control.Visible%2A>隱藏和顯示控制項的屬性。  
  
 [如何：為控制項提供透明背景](how-to-give-your-control-a-transparent-background.md)  
 示範如何使用<xref:System.Windows.Forms.Control.SetStyle%2A>方法用來建立不透明、 透明或部分透明的背景色彩。  
  
 [使用視覺化樣式呈現控制項](rendering-controls-with-visual-styles.md)  
 示範如何呈現在支援的作業系統中使用視覺化樣式的控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.UserControl>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 描述這個方法。  
  
## <a name="related-sections"></a>相關章節  
 [如何：建立繪圖的圖形物件](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 導入了[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]從 Visual Studio 中的檢視方塊，並提供連結的繪圖功能的詳細資訊。  
  
 [各種自訂控制項](varieties-of-custom-controls.md)  
 描述您可以撰寫自訂控制項的類型。
