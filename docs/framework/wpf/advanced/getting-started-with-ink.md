---
title: "筆墨入門 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動畫, 漸層筆刷色彩"
  - "筆刷, 建立色彩動畫"
  - "漸層筆刷, 建立色彩動畫"
  - "程序性程式碼替代 XAML"
  - "XAML, 程序性程式碼替代"
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 筆墨入門
將數位筆墨加入應用程式要比以往更加簡單。  筆墨的演進發展對於 COM 和 Windows Forms 程式設計的方法，是達成與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 完全整合的必要關鍵。  您不一定要安裝個別的 SDK 或執行階段程式庫。  
  
## 必要條件  
 您必須先安裝 Microsoft Visual Studio 2005 和 [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]，才能使用下列範例。  也應該瞭解如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。  如需開始使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的詳細資訊，請參閱[逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## 快速入門  
 本節會協助您撰寫收集筆墨的簡單 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
 如果您尚未安裝 Microsoft Visual Studio 2005 和 [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]，請立即進行安裝。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式通常必須經過編譯，您才可以進行檢視，即使應用程式包含整個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 亦然。  但是，[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] 包含應用程式 XamlPad，XamlPad 是專為加入實作以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 為基礎之 UI 的處理速度而設計的。  您可以使用該應用程式，來檢視和修補本文件前幾個範例。  從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 建立已編譯應用程式的程序涵蓋在本文件稍後的部分。  
  
 若要啟動 XAMLPad，按一下 \[**開始**\] 功能表，依序指向 \[**所有程式**\]、\[**Microsoft Winndows SDK**\] 和 \[**工具**\]，然後按一下 \[**XAMLPad**\]。  在呈現窗格中，XAMLPad 會呈現在程式碼窗格中寫入的 XAML 程式碼。  您可以編輯 XAML 程式碼，所做變更會立即顯示在呈現窗格中。  
  
#### 取得筆墨  
 若要啟動您第一個支援筆墨的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式：  
  
1.  開啟 Microsoft Visual Studio 2005  
  
2.  建立新的 \[**Windows Application \(WPF\)**\]  
  
3.  在 `<Grid>` 標籤之間輸入 `<InkCanvas/>`  
  
4.  按下 **F5** 在偵錯工具中啟動應用程式  
  
5.  使用手寫筆或滑鼠，在視窗中寫入 hello world  
  
 您只用了 12 個按鍵，就寫入相當於 "hello world" 應用程式的筆墨！  
  
#### 為應用程式增添樂趣  
 讓我們利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的某些功能。  將開始 \<Window\> 和結束 \<\/Window\> 標籤之間的所有內容取代為下列標記，即可在筆墨表面上取得漸層筆刷背景。  
  
 [!code-xml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### 使用動畫  
 讓我們將漸層筆刷的色彩變成動畫，增添更多樂趣。  將下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入至結束 `</InkCanvas>` 標籤之後，結束 `</Page>` 標籤之前。  
  
 [!code-xml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### 在 XAML 背後加入某些程式碼  
 XAML 讓設計使用者介面變得非常容易的同時，任何實際的應用程式都必須加入程式碼，才能處理事件。  以下的簡單範例，會放大筆墨以回應滑鼠右鍵按一下的動作：  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定 `MouseRightButtonUp` 處理常式：  
  
 [!code-xml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 在 Visual Studio 的 \[方案總管\] 中，展開 Windows1.xaml 並開啟程式碼後置檔案，如果您使用的是 Visual Basic，則請開啟 Window1.xaml.cs 或 Window1.xaml.vb。  加入下列事件處理常式程式碼：  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 現在，請執行您的應用程式。  加入某些筆墨，然後以滑鼠右鍵按一下，或使用手寫筆執行按住的對等動作。  
  
#### 使用程序性程式碼，而不要使用 XAML  
 您可以從程序性程式碼存取所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能。  以下是將 "Hello Ink World" 用於完全不使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用情形。  將下列程式碼貼到 Visual Studio 中的空白主控台應用程式。  將參考加入至 PresentationCore、PresentationFramework 和 WindowsBase 組件，並按下 **F5** 建置應用程式：  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## 請參閱  
 [數位筆跡](../../../../docs/framework/wpf/advanced/digital-ink.md)   
 [收集筆墨](../../../../docs/framework/wpf/advanced/collecting-ink.md)   
 [手寫辨識](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)   
 [儲存筆墨](../../../../docs/framework/wpf/advanced/storing-ink.md)