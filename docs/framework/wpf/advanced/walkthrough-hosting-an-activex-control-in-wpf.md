---
title: 逐步解說：在 WPF 中裝載 ActiveX 控制項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc4f577da04fb8ed15bae3c0497b35803a46f08f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>逐步解說：在 WPF 中裝載 ActiveX 控制項
若要啟用改善的瀏覽器互動，您可以使用[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]控制在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。 本逐步解說示範您可以主控[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上的控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立專案。  
  
-   建立 ActiveX 控制項。  
  
-   ActiveX 控制項裝載到 WPF 頁面上。  
  
 當您完成這個逐步解說時，您將了解如何使用[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]控制中的程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 安裝 Visual Studio 電腦上安裝。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>建立專案  
  
#### <a name="to-create-and-set-up-the-project"></a>建立並設定專案  
  
1.  建立 WPF 應用程式專案，名為`HostingAxInWpf`。  
  
2.  將 Windows Form 控制項程式庫專案加入方案，並將專案命名`WmpAxLib`。  
  
3.  在 WmpAxLib 專案中，加入名為 wmp.dll 的 Windows Media Player 組件的參考。  
  
4.  開啟**工具箱**。  
  
5.  以滑鼠右鍵按一下**工具箱**，然後按一下 **選擇項目**。  
  
6.  按一下**COM 元件**索引標籤上，選取**Windows Media Player**控制項，然後再按一下**確定**。  
  
     Windows Media Player 控制項加入至**工具箱**。  
  
7.  在 [方案總管] 中，以滑鼠右鍵按一下**UserControl1**檔案，然後再按一下**重新命名**。  
  
8.  將名稱變更為`WmpAxControl.vb`或`WmpAxControl.cs`，取決於語言。  
  
9. 如果提示您重新命名的所有參考時，請按一下**是**。  
  
## <a name="creating-the-activex-control"></a>建立 ActiveX 控制項  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 會自動產生<xref:System.Windows.Forms.AxHost>包裝函式類別[!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)]控制控制項加入至設計介面時。 下列程序會建立名為 AxInterop.WMPLib.dll managed 組件。  
  
#### <a name="to-create-the-activex-control"></a>若要建立 ActiveX 控制項  
  
1.  在 Windows Form 設計工具中開啟 WmpAxControl.vb 或 WmpAxControl.cs。  
  
2.  從**工具箱**，將 Windows Media Player 控制項加入至設計介面。  
  
3.  在 [屬性] 視窗中，將 Windows Media Player 控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。  
  
4.  建置 WmpAxLib 控制項程式庫專案。  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>裝載 WPF 頁面上的 ActiveX 控制項  
  
#### <a name="to-host-the-activex-control"></a>裝載 ActiveX 控制項  
  
1.  在 HostingAxInWpf 專案中，新增至所產生的參考[!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)]互通性組件。  
  
     這個組件名為 AxInterop.WMPLib.dll，並且已加入至 WmpAxLib 專案的 Debug 資料夾中，當您匯入 Windows Media Player 控制項。  
  
2.  加入名為 WindowsFormsIntegration.dll WindowsFormsIntegration 組件的參考。  
  
3.  將參考加入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]System.Windows.Forms.dll 名為組件。  
  
4.  在 WPF 設計工具中開啟 MainWindow.xaml。  
  
5.  名稱<xref:System.Windows.Controls.Grid>元素`grid1`。  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>項目。  
  
7.  在 屬性 視窗中，按一下**事件** 索引標籤。  
  
8.  按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
9. 插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
     此程式碼建立的執行個體<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制，並將執行個體`AxWindowsMediaPlayer`做為其子系的控制項。  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. 按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
