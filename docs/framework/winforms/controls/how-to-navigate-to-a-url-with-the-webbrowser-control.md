---
title: HOW TO：瀏覽至 URL，以使用 WebBrowser 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: 599ae9fbaed3240efa05dc04f5b6dc4180e55cfb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524217"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>HOW TO：瀏覽至 URL，以使用 WebBrowser 控制項
下列程式碼範例示範如何瀏覽<xref:System.Windows.Forms.WebBrowser>至特定 URL 的控制項。  
  
 若要判斷新的文件是完全載入時，處理<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。 如需示範此事件，請參閱[How to:使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)。  
  
## <a name="example"></a>範例  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。  
  
-   `System` 和 `System.Windows.Forms` 組件的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser 控制項](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
- [如何：使用 WebBrowser 控制項列印](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
