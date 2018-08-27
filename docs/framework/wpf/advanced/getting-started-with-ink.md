---
title: 在 Visual Studio 中的 WPF 應用程式中建立 InkCanvas
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 600d8528125606c6e1af5b031e2fc31aabb79206
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925040"
---
# <a name="get-started-with-ink-in-wpf"></a>開始使用 WPF 中的筆墨

Windows Presentation Foundation (WPF) 具有筆跡功能，可讓您輕鬆地將您的應用程式的數位筆跡。

## <a name="prerequisites"></a>必要條件

若要使用下列範例中，第一次[安裝 Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。 它也有助於了解如何撰寫基本的 WPF 應用程式。 開始使用 WPF 的協助，請參閱[逐步解說： 我第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。

## <a name="quick-start"></a>快速入門

本節可協助您撰寫簡單的 WPF 應用程式會收集筆跡。

### <a name="got-ink"></a>有筆墨嗎？

若要建立支援筆墨的 WPF 應用程式：

1. 開啟 Visual Studio。

2. 建立新**WPF 應用程式**。

   在 [**新的專案**] 對話方塊中，展開**已安裝** > **Visual C#** 或**Visual Basic**  >  **Windows 桌面**類別目錄。 然後，選取**WPF 應用程式 (.NET Framework)** 應用程式範本。 輸入名稱，然後按**確定**。

   Visual Studio 建立專案，並*MainWindow.xaml*會在設計工具中開啟。

3. 型別`<InkCanvas/>`之間`<Grid>`標記。

   ![InkCanvas 標記的 XAML 設計工具](media/getting-started-with-ink/inkcanvas-xaml.png)

4. 按下**F5**來啟動您的應用程式偵錯工具。

5. 使用手寫筆或滑鼠，撰寫**hello world**  視窗中。

您已撰寫筆墨相當於只有 12 的按鍵輸入的"hello world"應用程式 ！

### <a name="spice-up-your-app"></a>為您的應用程式增添

讓我們好好利用 WPF 的某些功能。 取代所有項目之間的開頭和結尾\<視窗 > 標記，以下列標記：

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

此 XAML 會建立漸層筆刷背景筆跡的介面上。

![在筆跡介面在 WPF 應用程式中的漸層色彩](media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>加入一些程式碼背後的 XAML

XAML 可以很容易就能設計使用者介面，而任何實際的應用程式必須加入程式碼來處理事件。 以下是簡單的範例，以滑鼠右鍵按一下的滑鼠回應中的筆墨會放大。

1. 設定`MouseRightButtonUp`在您的 XAML 中的處理常式：

   [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. 在 [**方案總管] 中**、 展開 MainWindow.xaml 並開啟程式碼後置檔案 （MainWindow.xaml.cs 或 MainWindow.xaml.vb）。 新增下列事件處理常式程式碼：

   [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. 執行應用程式。 新增一些墨水，然後以滑鼠右鍵按一下滑鼠或手寫筆使用中執行按保留對等項目。

   顯示您以滑鼠右鍵按一下 每次會放大。

### <a name="use-procedural-code-instead-of-xaml"></a>使用程序程式碼，而不是 XAML

您可以存取所有的 WPF 功能從程序性程式碼。 請遵循下列步驟來建立不使用任何 XAML 的 WPF 的"Hello 筆墨 World"應用程式。

1. Visual Studio 中建立新的主控台應用程式專案。

   在 [**新的專案**] 對話方塊中，展開**已安裝** > **Visual C#** 或**Visual Basic**  >  **Windows 桌面**類別目錄。 然後，選取**主控台應用程式 (.NET Framework)** 應用程式範本。 輸入名稱，然後按**確定**。

1. 將下列程式碼貼到 Program.cs 或 Program.vb 檔案中：

   [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. 新增 PresentationCore、 PresentationFramework、 與 WindowsBase 組件的參考，以滑鼠右鍵按一下**參考**中**方案總管**，然後選擇**加入參考**.

   ![顯示 PresentationCore 與 PresentationFramework 參考管理員](media/getting-started-with-ink/references.png)

1. 建置應用程式藉由按下**F5**。

## <a name="see-also"></a>另請參閱

- [數位筆跡](../../../../docs/framework/wpf/advanced/digital-ink.md)
- [收集筆墨](../../../../docs/framework/wpf/advanced/collecting-ink.md)
- [手寫辨識](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)
- [儲存筆墨](../../../../docs/framework/wpf/advanced/storing-ink.md)
