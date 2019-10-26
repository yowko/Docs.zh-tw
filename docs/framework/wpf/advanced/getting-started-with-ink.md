---
title: 在 Visual Studio 的 WPF 應用程式中建立 InkCanvas
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920244"
---
# <a name="get-started-with-ink-in-wpf"></a>開始使用 WPF 中的筆跡

Windows Presentation Foundation （WPF）有一項筆墨功能，可讓您輕鬆地將數位筆跡併入應用程式中。

## <a name="prerequisites"></a>Prerequisites

若要使用下列範例，請先安裝[Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 它也有助於知道如何撰寫基本的 WPF 應用程式。 如需 WPF 入門的說明，請參閱[逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。

## <a name="quick-start"></a>快速入門

本節可協助您撰寫可收集筆跡的簡單 WPF 應用程式。

### <a name="got-ink"></a>有筆墨嗎？

若要建立支援筆墨的 WPF 應用程式：

1. 開啟 Visual Studio。

2. 建立新的**WPF 應用程式**。

   在 [**新增專案**] 對話方塊中，展開 [**已安裝**的 > **視覺效果C#**  ] 或 [ **Visual Basic** > **Windows 桌面**] 類別。 然後，選取 [ **WPF 應用程式（.NET Framework）** ] 應用程式範本。 輸入 [名稱]，然後選取 **[確定]** 。

   Visual Studio 會建立專案，而*mainwindow.xaml*會在設計工具中開啟。

3. 在 `<Grid>` 標記之間輸入 `<InkCanvas/>`。

   ![具有 InkCanvas 標記的 XAML 設計工具](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. 按**F5**以在偵錯工具中啟動您的應用程式。

5. 使用手寫筆或滑鼠，在視窗中寫入**hello world** 。

您撰寫了與 "hello world" 應用程式相同的筆墨，只需12次按鍵！

### <a name="spice-up-your-app"></a>Spice 您的應用程式

讓我們利用 WPF 的一些功能。 以下列標記取代開頭和結尾 \<視窗 > 標記之間的所有內容：

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

此 XAML 會在您的筆跡表面上建立漸層筆刷背景。

![WPF 應用程式中筆跡表面的漸層色彩](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>在 XAML 後面新增一些程式碼

雖然 XAML 可以讓您輕鬆地設計使用者介面，但任何真實世界的應用程式都必須加入程式碼來處理事件。 以下是一個簡單的範例，它會放大筆墨以回應滑鼠右鍵按一下。

1. 在您的 XAML 中設定 `MouseRightButtonUp` 處理常式：

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. 在**方案總管**中，展開 mainwindow.xaml，然後開啟程式碼後置檔案（MainWindow.xaml.cs 或 mainwindow.xaml）。 新增下列事件處理常式程式碼：

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. 執行應用程式。 新增一些筆墨，然後以滑鼠右鍵按一下滑鼠，或執行與手寫筆的按住等動作。

   每次按一下滑鼠右鍵時，畫面就會縮放。

### <a name="use-procedural-code-instead-of-xaml"></a>使用程式性程式碼，而不是 XAML

您可以從程式性程式碼存取所有 WPF 功能。 請遵循下列步驟來建立 WPF 的 "Hello Ink World" 應用程式，完全不使用任何 XAML。

1. 在 Visual Studio 中建立新的主控台應用程式專案。

   在 [**新增專案**] 對話方塊中，展開 [**已安裝**的 > **視覺效果C#**  ] 或 [ **Visual Basic** > **Windows 桌面**] 類別。 然後，選取 [**主控台應用程式（.NET Framework）** ] 應用程式範本。 輸入 [名稱]，然後選取 **[確定]** 。

1. 將下列程式碼貼入 Program.cs 或 Program .vb 檔案：

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. 以滑鼠右鍵按一下**方案總管**中的**參考**，然後選擇 [**加入參考**]，即可加入 PresentationCore、PresentationFramework 和 WindowsBase 元件的參考。

   ![顯示 PresentationCore 和 PresentationFramework 的參考管理員](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. 按**F5**來建立應用程式。

## <a name="see-also"></a>請參閱

- [數位筆跡](digital-ink.md)
- [收集筆墨](collecting-ink.md)
- [手寫辨識](handwriting-recognition.md)
- [儲存筆墨](storing-ink.md)
