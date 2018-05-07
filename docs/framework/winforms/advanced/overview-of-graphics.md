---
title: 圖形概觀
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a69bfc2e9983484f90b1b65abd234df2519b503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-graphics"></a>圖形概觀
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 為應用程式開發介面 (API) 構成 Microsoft Windows 作業系統的子系統。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會負責顯示螢幕和印表機上的資訊。 正如其名， [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 是 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 的後置項，該繪圖裝置介面包含在舊版 Windows 中。  
  
## <a name="managed-class-interface"></a>Managed 類別介面  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API 會公開一組部署為 managed 程式碼的類別。 這組類別稱為*managed 的類別介面*至[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。 下列命名空間組成 Managed 類別介面：  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 圖形裝置介面，例如[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以在螢幕或印表機上顯示資訊，而不須關心特定顯示裝置的詳細資料。 程式設計師會呼叫 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 類別所提供的方法。 這些方法接著會適當地呼叫特定裝置驅動程式。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 會從圖形硬體隔離應用程式。 它是隔離會讓程式設計人員能夠建立與裝置無關的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [圖形概觀](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
