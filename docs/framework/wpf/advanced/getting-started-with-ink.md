---
title: "筆墨入門"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c977e8a4a23f9739541cf28d9e34ad9e8db1daf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-ink"></a>筆墨入門
數位筆跡併入您的應用程式是比以往更為容易。 從 COM 和 Windows Form 的方法達到完整地整合到程式設計必然發展筆墨[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 您不需要安裝個別的 Sdk 或執行階段程式庫。  
  
## <a name="prerequisites"></a>必要條件  
 若要使用下列的範例，您必須先安裝 Microsoft Visual Studio 2005 和[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。 您也應該了解如何撰寫適用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。 如需開始使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="quick-start"></a>快速入門  
 本節可協助您撰寫簡單[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]收集筆墨的應用程式。  
  
 如果您尚未這樣做，請安裝 Microsoft Visual Studio 2005 和[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式通常必須經過編譯，您可以檢視它們，即使它們是完全組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 不過，[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]包含應用程式，XamlPad，設計來加速實作的處理序[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-基礎 UI。 若要檢視和修補這份文件中的前幾個範例，您可以使用該應用程式。 建立的程序編譯的應用程式從[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]涵蓋在本文件稍後。  
  
 若要啟動 XAMLPad，按一下 **啟動**功能表上，指向**所有程式**，指向**Microsoft Winndows SDK**，指向**工具**，然後按一下**XAMLPad**。 在 [轉譯] 窗格中，XAMLPad 會呈現撰寫程式碼窗格中的 XAML 程式碼。 您可以編輯 XAML 程式碼，所做的變更會立即顯示在 [轉譯] 窗格中。  
  
#### <a name="got-ink"></a>有筆墨嗎？  
 若要啟動您的第一個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援筆墨的應用程式：  
  
1.  開啟 Microsoft Visual Studio 2005  
  
2.  建立新**Windows 應用程式 (WPF)**  
  
3.  型別`<InkCanvas/>`之間`<Grid>`標記  
  
4.  按**F5**來偵錯工具中啟動應用程式  
  
5.  使用手寫筆或滑鼠，撰寫**hello world**視窗中  
  
 您已撰寫筆墨相當於使用只有 12 按鍵的"hello world"應用程式 ！  
  
#### <a name="spice-up-your-application"></a>您的應用程式讓動  
 讓我們來看的某些功能的優點[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  取代開頭之間的所有內容\<視窗 > 並關閉\</Window > 以取得筆墨表面背景漸層筆刷下列標記的標記。  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>使用動畫  
 玩看，我們製作動畫漸層筆刷的色彩。 加入下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]關閉後`</InkCanvas>`標記結束之前`</Page>`標記。  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>加入一些程式碼背後的 XAML  
 雖然 XAML 會很容易就能設計使用者介面，任何真實世界應用程式必須加入程式碼來處理事件。 以下是以滑鼠右鍵按一下回應來自滑鼠的筆墨會放大的簡單範例：  
  
 設定`MouseRightButtonUp`處理常式中的您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 在 Visual Studio 方案總管 中，展開 Windows1.xaml 並開啟 Window1.xaml.cs 或 Window1.xaml.vb，如果您使用 Visual Basic 的程式碼後置檔案。 加入下列事件處理常式程式碼：  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 現在，執行您的應用程式。 加入某些筆墨然後以滑鼠右鍵按一下使用滑鼠，或執行按保留對等項目具有手寫筆。  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>使用程序程式碼，而不 XAML  
 您可以存取所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程序程式碼中的功能。 以下是"Hello 筆墨 World"應用程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，不使用任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]完全。 將下列程式碼貼到空白 Visual Studio 中的主控台應用程式。 新增 PresentationCore、 PresentationFramework 和 WindowsBase 組件的參考，並按下建置應用程式**F5**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [數位筆跡](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [收集筆墨](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [手寫辨識](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [儲存筆墨](../../../../docs/framework/wpf/advanced/storing-ink.md)
