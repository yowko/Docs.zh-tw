---
title: 自訂控制項繪製和轉譯
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 18a05a739f42d41a650e66723f44aae69c1707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526047"
---
# <a name="custom-control-painting-and-rendering"></a>自訂控制項繪製和轉譯
自訂繪製的控制項是容易由.NET Framework 的許多複雜工作。 撰寫的自訂控制項，當您有許多有關控制項的圖形的外觀。 如果您撰寫控制項是繼承自`Control`，您必須提供程式碼，讓您的控制項轉譯其圖形表示。 如果您要建立使用者控制項透過繼承自`UserControl`，繼承或從其中一個 Windows Form 控制項，您可能會覆寫標準的圖形表示，並提供您自己的圖形的程式碼。 如果您想要提供自訂的構成控制項轉譯`UserControl`撰寫時，您的選項變得更小，但仍然可讓各種不同的圖形化的控制項和應用程式的可能性。  
  
## <a name="in-this-section"></a>本節內容  
 [呈現 Windows Forms 控制項](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 示範如何撰寫程式顯示控制項的邏輯。  
  
 [使用者自訂描繪控制項](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 提供撰寫和覆寫控制項的轉譯程式碼所需的步驟的概觀。  
  
 [組成控制項](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 描述如何在使用者控制項和表單實作的組成控制項的自訂轉譯程式碼。  
  
 [操作說明：在執行階段期間隱藏控制項](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 示範如何使用<xref:System.Windows.Forms.Control.Visible%2A>隱藏和顯示控制項的屬性。  
  
 [操作說明：為控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 示範如何使用<xref:System.Windows.Forms.Control.SetStyle%2A>方法來建立不透明、 透明或透明部分的背景色彩。  
  
 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 示範如何呈現在支援的作業系統中使用視覺化樣式的控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.UserControl>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 描述這個方法。  
  
## <a name="related-sections"></a>相關章節  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 導入了[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]從 Visual Studio 中的檢視方塊並提供連結的圖形功能的詳細資訊。  
  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 描述您可以編寫自訂控制項類型。
