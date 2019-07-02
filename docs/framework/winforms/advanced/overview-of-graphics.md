---
title: 圖形概觀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505330"
---
# <a name="overview-of-graphics"></a>圖形概觀
GDI + 是應用程式開發介面 (API) 構成的 Microsoft Windows 作業系統的子系統。 GDI + 會負責顯示螢幕和印表機上的資訊。 正如其名，GDI + 是 GDI，隨附於舊版的 Windows 繪圖裝置介面的後續版本。  
  
## <a name="managed-class-interface"></a>Managed 類別介面  
 GDI + API 會透過一組部署為 managed 程式碼的類別公開。 這組類別稱為*managed 的類別介面*GDI +。 下列命名空間組成 Managed 類別介面：  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 圖形裝置介面，例如 GDI + 中，您可以顯示資訊的螢幕或印表機上而不須關心特定顯示裝置的詳細資料。 程式設計師會呼叫 GDI + 類別所提供的方法。 這些方法接著會適當地呼叫特定裝置驅動程式。 GDI + 隔離應用程式會從圖形硬體。 這是此隔離會讓程式設計人員能夠建立與裝置無關的應用程式。  
  
## <a name="see-also"></a>另請參閱

- [圖形概觀](graphics-overview-windows-forms.md)
