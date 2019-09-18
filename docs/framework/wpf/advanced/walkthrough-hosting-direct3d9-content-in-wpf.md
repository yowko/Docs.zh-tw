---
title: 逐步解說：將 Direct3D9 內容裝載在 WPF 中
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 2c31c044aa50a74255a61da1675037ab3d09f615
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053456"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>逐步解說：將 Direct3D9 內容裝載在 WPF 中

本逐步解說說明如何在 Windows Presentation Foundation （WPF）應用程式中裝載 Direct3D9 內容。

在這個逐步解說中，您將執行下列工作：

- 建立 WPF 專案來裝載 Direct3D9 內容。

- 匯入 Direct3D9 內容。

- 使用<xref:System.Windows.Interop.D3DImage>類別顯示 Direct3D9 內容。

 當您完成時，您會知道如何在 WPF 應用程式中裝載 Direct3D9 內容。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- Visual Studio。

- DirectX SDK 9 或更新版本。

- 包含 WPF 相容格式之 Direct3D9 內容的 DLL。 如需詳細資訊，請參閱[WPF 和 Direct3D9 交互操作](wpf-and-direct3d9-interoperation.md)性和[逐步解說：建立在 WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)中裝載的 Direct3D9 內容。

## <a name="creating-the-wpf-project"></a>建立 WPF 專案

第一個步驟是建立 WPF 應用程式的專案。

### <a name="to-create-the-wpf-project"></a>若要建立 WPF 專案

在 Visual C#中建立名為`D3DHost`的新 WPF 應用程式專案。 如需詳細資訊，請參閱[逐步解說：我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式。

Mainwindow.xaml 會在中[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]開啟。

## <a name="importing-the-direct3d9-content"></a>匯入 Direct3D9 內容

您可以使用`DllImport`屬性，從非受控 DLL 匯入 Direct3D9 的內容。

### <a name="to-import-direct3d9-content"></a>匯入 Direct3D9 內容

1. 在程式碼編輯器中開啟 MainWindow.xaml.cs。

2. 使用下列程式碼取代自動產生的程式碼。

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a>裝載 Direct3D9 內容

最後，使用<xref:System.Windows.Interop.D3DImage>類別來裝載 Direct3D9 內容。

### <a name="to-host-the-direct3d9-content"></a>裝載 Direct3D9 內容

1. 在 Mainwindow.xaml 中，以下列 XAML 取代自動產生的 XAML。

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. 建置專案。

3. 將包含 Direct3D9 內容的 DLL 複製到 bin/Debug 資料夾。

4. 按 F5 執行專案。

    Direct3D9 內容會出現在 WPF 應用程式中。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 和 WPF 互通性的效能考量](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
