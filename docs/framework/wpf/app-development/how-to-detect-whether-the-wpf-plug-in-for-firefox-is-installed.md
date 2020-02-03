---
title: 偵測是否已安裝 Firefox 的 WPF 外掛程式
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 91680859c1742e5d5443d626c81273a80504f4a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740392"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>如何：偵測有無安裝 Firefox 的 WPF 外掛程式

適用于 Firefox 的 Windows Presentation Foundation （WPF）外掛程式可讓 XAML 瀏覽器應用程式（Xbap）和鬆散的 XAML 檔案在 Mozilla Firefox 瀏覽器中執行。 本主題提供以 HTML 和 JavaScript 撰寫的腳本，可讓系統管理員用來判斷是否已安裝 Firefox 的 WPF 外掛程式。

> [!NOTE]
> 如需安裝、部署和偵測 .NET Framework 的詳細資訊，請參閱[安裝適用于開發人員的 .NET Framework](../../install/guide-for-developers.md)。

## <a name="example"></a>範例

安裝 .NET Framework 3.5 時，會使用 Firefox 的 WPF 外掛程式來設定用戶端電腦。 下列範例腳本會檢查 Firefox 的 WPF 外掛程式，然後顯示適當的狀態訊息。

```html
<HTML>

  <HEAD>
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />
    <SCRIPT type="text/javascript">
    <!--
    function OnLoad()
    {

       // Check for the WPF plug-in for Firefox and report
       var msg = "The WPF plug-in for Firefox is ";
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];
       if( wpfPlugin != null ) {
          document.writeln(msg + " installed.");
       }
       else {
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");
       }
    }
    -->
    </SCRIPT>
  </HEAD>

  <BODY onload="OnLoad()" />

</HTML>
```

如果 Firefox 的 WPF 外掛程式檢查成功，則會顯示下列狀態訊息：

`The WPF plug-in for Firefox is installed.`

否則，會顯示下列狀態訊息：

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>另請參閱

- [偵測有無安裝 .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [偵測有無安裝 .NET Framework 3.5](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)
