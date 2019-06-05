---
title: 作法：偵測有無安裝 Firefox 的 WPF 外掛程式
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: f84a0a2af43931b3ada1f674390ec5d841b79a1c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690427"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>作法：偵測有無安裝 Firefox 的 WPF 外掛程式

Windows Presentation Foundation (WPF) Firefox 的外掛程式可讓[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]鬆散 XAML 檔案，以在 Mozilla Firefox 瀏覽器中執行。 本主題提供以 HTML 和系統管理員可用來判斷是否已安裝的 WPF 外掛程式適用於 Firefox 的 JavaScript 撰寫的指令碼。

> [!NOTE]
> 如需有關安裝的詳細資訊，請部署，並偵測.NET Framework 中，請參閱[安裝適用於開發人員的.NET Framework](../../install/guide-for-developers.md)。

## <a name="example"></a>範例

安裝.NET Framework 3.5 時，用戶端電腦都設定搭配 WPF 外掛程式適用於 Firefox。 下列的範例指令碼會檢查適用於 Firefox 的 WPF 外掛程式，並接著會顯示適當的狀態訊息。

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

如果適用於 Firefox 的 WPF 外掛程式檢查成功，則會顯示下列狀態訊息：

`The WPF plug-in for Firefox is installed.`

否則，會顯示下列狀態訊息：

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>另請參閱

- [偵測有無安裝 .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [偵測有無安裝 .NET Framework 3.5](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [WPF XAML 瀏覽器應用程式概觀](wpf-xaml-browser-applications-overview.md)
