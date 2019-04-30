---
title: HOW TO：偵測有無安裝 Firefox 的 WPF 外掛程式
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 138c212e79654b8ac875628692b49bb6a38cb695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947871"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>HOW TO：偵測有無安裝 Firefox 的 WPF 外掛程式

Windows Presentation Foundation (WPF) Firefox 的外掛程式可讓[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]鬆散 XAML 檔案，以在 Mozilla Firefox 瀏覽器中執行。 本主題提供以 HTML 和系統管理員可用來判斷是否已安裝的 WPF 外掛程式適用於 Firefox 的 JavaScript 撰寫的指令碼。

> [!NOTE]
> 如需有關安裝、 部署和偵測[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，請參閱 <<c2> [ 安裝適用於開發人員的.NET Framework](../../install/guide-for-developers.md)。

## <a name="example"></a>範例

當[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]是安裝，用戶端電腦已使用的 WPF 外掛程式適用於 Firefox。 下列的範例指令碼會檢查適用於 Firefox 的 WPF 外掛程式，並接著會顯示適當的狀態訊息。

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
