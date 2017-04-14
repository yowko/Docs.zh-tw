---
title: "逐步解說：當地語系化混合應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "混合應用程式 [WPF 互通性]"
  - "當地語系化 [WPF 互通性]"
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 逐步解說：當地語系化混合應用程式
此逐步解說將為您顯示如何當地語系化 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 架構混合應用程式中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目。  
  
 逐步解說將說明的工作包括：  
  
-   建立 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 主專案  
  
-   加入可當地語系化的內容  
  
-   啟用當地語系化  
  
-   指定資源識別項  
  
-   使用 LocBaml 工具產生附屬組件  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[當地語系化混合式應用程式範例](http://go.microsoft.com/fwlink/?LinkID=160015) \(英文\)。  
  
 完成作業後，您即具有當地語系化的混合應用程式。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## 建立 Windows Form 主專案  
 第一個步驟是建立 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式專案，並加入含有您要當地語系化之內容的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目。  
  
#### 若要建立主專案  
  
1.  建立名為 `LocalizingWpfInWf` 的 WPF 應用程式專案。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  將名為 `SimpleControl` 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 項目加入至專案。  
  
3.  使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項將 `SimpleControl` 項目放在表單上。  如需詳細資訊，請參閱 [逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)。  
  
## 加入可當地語系化的內容  
 接著，您必須加入 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 標籤控制項，並將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目的內容設為可當地語系化的字串。  
  
#### 若要加入可當地語系化的內容  
  
1.  在 \[方案總管\] 中按兩下 \[**SimpleControl.xaml**\]，以 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]開啟它。  
  
2.  使用下列程式碼設定 <xref:System.Windows.Controls.Button> 控制項的內容。  
  
     [!code-xml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  在 \[方案總管\] 中按兩下 \[**Form1**\]，以 \[Windows Form 設計工具\] 加以開啟。  
  
4.  開啟 \[工具箱\] 並按兩下 \[**標籤**\]，將標籤控制項加入至表單。  將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值設為 `"Hello"`。  
  
5.  按 F5 建置並執行應用程式。  
  
     `SimpleControl` 項目與標籤控制項都會顯示 **"Hello"** 字樣。  
  
## 啟用當地語系化  
 \[Windows Form 設計工具\] 提供了可在附屬組件中進行當地語系化的設定。  
  
#### 若要啟用當地語系化  
  
1.  在 \[方案總管\] 中按兩下 \[**Form1.cs**\]，以 \[Windows Form 設計工具\] 加以開啟。  
  
2.  在 \[屬性\] 視窗中，將表單的 \[**可當地語系化**\] 屬性值設為 `true`。  
  
3.  在 \[屬性\] 視窗中，將 \[**語言**\] 屬性的值設為 \[**西班牙文 \(西班牙\)**\]。  
  
4.  在 \[Windows Form 設計工具\] 中，選取標籤控制項。  
  
5.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值設為 `"Hola"`。  
  
     專案中即會加入名為 Form1.es\-ES.resx 的新資源檔。  
  
6.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**Form1.cs**\]，再按 \[**檢視程式碼**\] 以 \[程式碼編輯器\] 加以開啟。  
  
7.  呼叫 `InitializeComponent` 之前，將下列程式碼複製到 `Form1` 建構函式中。  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**LocalizingWpfInWf**\]，然後按一下 \[**卸載檔案**\]。  
  
     專案名稱會標記為 \[**\(無法使用\)**\]。  
  
9. 以滑鼠右鍵按一下 \[**LocalizingWpfInWf**\]，再按一下 \[**編輯 LocalizingWpfInWf.csproj**\]。  
  
     專案檔會以 \[程式碼編輯器\] 開啟。  
  
10. 將下行複製到專案檔的第一個 `PropertyGroup` 中。  
  
    ```  
    <UICulture>en-US</UICulture>   
    ```  
  
11. 儲存專案檔並予以關閉。  
  
12. 在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**LocalizingWpfInWf**\]，然後按一下 \[**重新載入檔案**\]。  
  
## 指定資源識別項  
 您可以使用資源識別項，將可當地語系化的內容對應至資源組件。  MsBuild.exe 應用程式會在您指定 `updateuid` 選項時自動指定資源識別項。  
  
#### 若要指定資源識別項  
  
1.  從 \[開始\] 功能表開啟 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 命令提示字元。  
  
2.  使用下列命令，將資源識別項指定給可當地語系化的內容。  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  在 \[方案總管\] 中按兩下 \[**SimpleControl.xaml**\]，以 \[程式碼編輯器\] 加以開啟。  您會看到 `msbuild` 命令已將 `Uid` 屬性加入至所有項目。  如此可透過資源識別項的指派而達成當地語系化。  
  
     [!code-xml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  按 F6 建置方案。  
  
## 使用 LocBaml 產生附屬組件  
 您的當地語系化內容會儲存在資源專用的「*附屬組件*」\(Satellite Assembly\) 中。  使用命令列工具 LocBaml.exe 為您的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容產生當地語系化的組件。  
  
#### 若要產生附屬組件  
  
1.  將 LocBaml.exe 複製到專案的 obj\\Debug 資料夾中。  如需詳細資訊，請參閱 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。  
  
2.  在 \[命令提示字元\] 視窗中，使用下列命令將資源字串擷取至暫存檔中。  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  以 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 或其他文字編輯器開啟 temp.csv 檔案。  將字串 `"Hello"` 取代為其西班牙文翻譯 `"Hola"`。  
  
4.  儲存 temp.csv 檔案。  
  
5.  使用下列命令產生當地語系化的資源檔。  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     LocalizingWpfInWf.g.es\-ES.resources 檔案會建立在 obj\\Debug 資料夾中。  
  
6.  使用下列命令建置當地語系化的附屬組件。  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     LocalizingWpfInWf.resources.dll 檔案會建立在 obj\\Debug 資料夾中。  
  
7.  將 LocalizingWpfInWf.resources.dll 檔案複製到專案的 bin\\Debug\\es\-ES 資料夾中。  取代現有的檔案。  
  
8.  執行 LocalizingWpfInWf.exe，此檔案位於專案的 bin\\Debug 資料夾中。  請不要重建應用程式，否則將會覆寫附屬組件。  
  
     應用程式會顯示當地語系化的字串，而非英文字串。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)