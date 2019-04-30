---
title: 逐步解說：將 Direct3D9 內容裝載在 WPF 中
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 07cfa5bed6e5af131a60a303f0702f18413043e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007110"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>逐步解說：將 Direct3D9 內容裝載在 WPF 中
本逐步解說示範如何裝載 Windows Presentation Foundation (WPF) 應用程式中的 Direct3D9 內容。  
  
 在這個逐步解說中，您將執行下列工作：  
  
- 建立 WPF 專案來裝載 Direct3D9 內容。  
  
- 匯入 Direct3D9 內容。  
  
- 使用顯示 Direct3D9 內容<xref:System.Windows.Interop.D3DImage>類別。  
  
 當您完成時，您會知道如何裝載在 WPF 應用程式中的 Direct3D9 內容。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
- Visual Studio。  
  
- DirectX 9 或更新版本的 SDK。  
  
- 包含與 WPF 相容的格式中的 Direct3D9 內容的 DLL。 如需詳細資訊，請參閱 < [WPF 和 Direct3D9 互通](wpf-and-direct3d9-interoperation.md)和[逐步解說：建立裝載在 WPF 中的 Direct3D9 內容](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)。  
  
## <a name="creating-the-wpf-project"></a>建立 WPF 專案  
 第一個步驟是建立 WPF 應用程式的專案。  
  
#### <a name="to-create-the-wpf-project"></a>若要建立 WPF 專案  
  
- 新的 WPF 應用程式專案中 Visual C# 建立名為`D3DHost`。 如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
     在中開啟 MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
## <a name="importing-the-direct3d9-content"></a>匯入 Direct3D9 內容  
 您使用匯入 Direct3D9 內容從 unmanaged DLL`DllImport`屬性。  
  
#### <a name="to-import-direct3d9-content"></a>若要匯入 Direct3D9 內容  
  
1. 在程式碼編輯器中開啟 MainWindow.xaml.cs。  
  
2. 下列程式碼取代自動產生的程式碼。  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>裝載 Direct3D9 內容  
 最後，使用<xref:System.Windows.Interop.D3DImage>類別，以裝載 Direct3D9 內容。  
  
#### <a name="to-host-the-direct3d9-content"></a>若要裝載 Direct3D9 內容  
  
1. 在 MainWindow.xaml 中，自動產生的 XAML 取代為下列 XAML。  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2. 建置專案。  
  
3. 複製包含 bin/Debug 資料夾的 Direct3D9 內容的 DLL。  
  
4. 按 F5 執行專案。  
  
     Direct3D9 內容會出現在 WPF 應用程式中。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 和 WPF 互通性的效能考量](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
