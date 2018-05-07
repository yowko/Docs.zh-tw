---
title: WebBrowser 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 730d8f692a44a06ea142bb870bbd961d5983c785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="webbrowser-security"></a>WebBrowser 安全性
<xref:System.Windows.Forms.WebBrowser>控制項設計成只在完全信任中運作。 在控制項中顯示的 HTML 內容可來自於外部 Web 伺服器，而且可能包含在指令碼或 Web 控制項的表單中的 unmanaged 程式碼。 如果您使用<xref:System.Windows.Forms.WebBrowser>控制項在此情況下，此控制項是比 Internet Explorer，但受管理的任何較不安全<xref:System.Windows.Forms.WebBrowser>控制項不會阻止這類 unmanaged 程式碼執行。  
  
 如需有關安全性問題相關的基礎 ActiveX`WebBrowser`控制，請參閱[WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=198812)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser 控制項概觀](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser 控制項](http://go.microsoft.com/fwlink/?LinkId=198812)
