---
title: 如何：偵測有無安裝 Firefox 的 WPF 外掛程式
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: fdc7b516c316c7efc7056b549baf43191a5aedd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423753"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="67ceb-102">如何：偵測有無安裝 Firefox 的 WPF 外掛程式</span><span class="sxs-lookup"><span data-stu-id="67ceb-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="67ceb-103">適用于 Firefox 的 Windows Presentation Foundation （WPF）外掛程式可讓 XAML 瀏覽器應用程式（Xbap）和鬆散的 XAML 檔案在 Mozilla Firefox 瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="67ceb-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables XAML browser applications (XBAPs) and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="67ceb-104">本主題提供以 HTML 和 JavaScript 撰寫的腳本，可讓系統管理員用來判斷是否已安裝 Firefox 的 WPF 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="67ceb-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="67ceb-105">如需安裝、部署和偵測 .NET Framework 的詳細資訊，請參閱[安裝適用于開發人員的 .NET Framework](../../install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="67ceb-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="67ceb-106">範例</span><span class="sxs-lookup"><span data-stu-id="67ceb-106">Example</span></span>

<span data-ttu-id="67ceb-107">安裝 .NET Framework 3.5 時，會使用 Firefox 的 WPF 外掛程式來設定用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="67ceb-107">When the .NET Framework 3.5 is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="67ceb-108">下列範例腳本會檢查 Firefox 的 WPF 外掛程式，然後顯示適當的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="67ceb-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

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

<span data-ttu-id="67ceb-109">如果 Firefox 的 WPF 外掛程式檢查成功，則會顯示下列狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="67ceb-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="67ceb-110">否則，會顯示下列狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="67ceb-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="67ceb-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="67ceb-111">See also</span></span>

- [<span data-ttu-id="67ceb-112">偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="67ceb-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="67ceb-113">偵測有無安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="67ceb-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="67ceb-114">WPF XAML 瀏覽器應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="67ceb-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
