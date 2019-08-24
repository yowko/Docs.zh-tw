---
title: 作法：使用 WebBrowser 控制項巡覽至 URL
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
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015821"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>作法：使用 WebBrowser 控制項巡覽至 URL
下列程式碼範例示範如何將<xref:System.Windows.Forms.WebBrowser>控制項導覽至特定的 URL。

 若要判斷新檔的完整載入時間, 請處理<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。 如需此事件的示範, 請[參閱如何:使用 WebBrowser 控制項](how-to-print-with-a-webbrowser-control.md)列印。

## <a name="example"></a>範例

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>編譯程式碼
 這個範例需要：

- 名為 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控制項。

- `System` 和 `System.Windows.Forms` 組件的參考。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser 控制項](webbrowser-control-windows-forms.md)
- [如何：使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)
