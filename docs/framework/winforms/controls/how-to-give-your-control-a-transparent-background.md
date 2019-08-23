---
title: 作法：為控制項提供透明背景
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966645"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>HOW TO：為控制項提供透明背景
在舊版 .NET Framework 中，控制項必須先在表單建構函式中設定 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，才能支援設定透明背景色彩。 在最新版 Framework 中，您可以在設計階段於 [屬性] <xref:System.Drawing.Color.Transparent%2A>**視窗中，或透過表單建構函式中的程式碼，將大多數控制項的背景色彩設定為** 。  
  
> [!NOTE]
> Windows Form 控制項不支援純粹透明。 透明的 Windows Form 控制項的背景預設是由其父代所繪製。  
  
> [!NOTE]
> 即使 <xref:System.Windows.Controls.Button> 屬性設定為 <xref:System.Windows.Forms.ButtonBase.BackColor%2A> ， <xref:System.Drawing.Color.Transparent%2A>控制項也不支援透明背景色彩。  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>為控制項提供透明背景色彩  
  
- 在 [屬性] 視窗中，選擇 <xref:System.Windows.Forms.ButtonBase.BackColor%2A> 屬性並將其設定為 <xref:System.Drawing.Color.Transparent%2A>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Color.FromArgb%2A>
- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
- [使用 Managed 圖形類別](../advanced/using-managed-graphics-classes.md)
- [如何：繪製不透明和半透明線條](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
