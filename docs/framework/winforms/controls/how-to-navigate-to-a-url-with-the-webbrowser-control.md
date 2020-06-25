---
title: 如何：使用 WebBrowser 控制項巡覽至 URL
description: 瞭解如何使用 Windows Forms WebBrowser. 導覽控制項來流覽至特定的 URL。 同時瞭解如何判斷新檔的載入時間。
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
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325574"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>如何：使用 WebBrowser 控制項巡覽至 URL
下列程式碼範例示範如何將控制項導覽 <xref:System.Windows.Forms.WebBrowser> 至特定的 URL。

 若要判斷新檔的完整載入時間，請處理 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件。 如需此事件的示範，請參閱[如何：使用 WebBrowser 控制項進行列印](how-to-print-with-a-webbrowser-control.md)。

## <a name="example"></a>範例

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
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
- [操作說明：使用 WebBrowser 控制項列印](how-to-print-with-a-webbrowser-control.md)
