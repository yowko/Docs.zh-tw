---
title: HOW TO：使用 WebBrowser 控制項巡覽至 URL
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
ms.openlocfilehash: a174b6ae60f87e91e6f97e8fa7f8ad3892ef017a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913467"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>HOW TO：使用 WebBrowser 控制項巡覽至 URL
下列程式碼範例示範如何瀏覽<xref:System.Windows.Forms.WebBrowser>至特定 URL 的控制項。  
  
 若要判斷新的文件是完全載入時，處理<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。 如需示範此事件，請參閱[How to:使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)。  
  
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
- [WebBrowser 控制項](webbrowser-control-windows-forms.md)
- [如何：使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)
