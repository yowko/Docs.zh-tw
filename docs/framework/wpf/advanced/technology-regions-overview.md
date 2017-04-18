---
title: "技術領域概觀 | Microsoft Docs"
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
  - "空間"
  - "互通性 [WPF], 空間"
  - "Win32 程式碼, 空間"
  - "Win32 程式碼, 視窗區域"
  - "Win32 程式碼, WPF 互通"
  - "視窗區域"
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 技術領域概觀
如果在應用程式中使用了多項展示技術，例如 WPF、Win32 或 DirectX，則這些技術必須共用通用最上層視窗內的轉譯區域。  本主題說明可能會影響 WPF 互通性應用程式之展示和輸入的問題。  
  
## 區域  
 在最上層視窗內，您可以將組成其中一種互通性應用程式技術的每個 HWND，想像成各自擁有自己的區域 \(也稱為「空間」\)。  視窗內的每個像素各屬於一個 HWND，也構成該 HWND 的區域   \(嚴格來說，如果有一個以上的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND，則 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 區域也會超過一個，但是為了進行以下討論，可以假設只有一個這種區域\)。  這種區域表示，嘗試在應用程式存留期期間呈現在像素上方的所有分層或其他視窗，全都必須是相同呈現層級技術的一部分。  嘗試將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 像素呈現在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 上會造成非預期的結果，因此互通性 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 盡可能阻止這項嘗試。  
  
### 區域範例  
 下圖顯示混合了 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。  每一項技術都使用一組各自分開、不重疊的像素，因此沒有區域問題。  
  
 ![沒有空間問題的視窗](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 假設這個應用程式使用滑鼠指標位置來建立嘗試在這三個區域任何一個上方呈現的動畫。  不論負責動畫本身的技術為何，該技術都會侵犯另外兩項技術的區域。  下圖顯示嘗試在 Win32 區域上呈現 WPF 圓形時的情況。  
  
 ![Interop 圖表](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 另一種違規情形是您嘗試在不同的技術之間使用透明度\/Alpha 透明混色。  在下圖中，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 方塊違反 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 和 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 區域。  因為該 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 方塊的像素呈半透明狀，所以必須由 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 共同擁有，但這是不可能的。  因此這是另一項無法建置的違規情況。  
  
 ![Interop 圖表](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 前述三個範例使用的都是矩形區域，但也可能是其他形狀。  例如，區域可以有洞。  下圖顯示的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 區域具有矩形洞，大小為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 區域的結合。  
  
 ![Interop 圖表](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 區域也可能完全不是矩形，或是能以 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN \(區域\) 描述的任何形狀。  
  
 ![Interop 圖表](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## 透明度和最上層視窗  
 Windows 中的視窗管理員實際上只會處理 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND。  因此，每個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> 都是一個 HWND。  <xref:System.Windows.Window> HWND 必須遵守任何 HWND 的一般規則。  在該 HWND 中，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 支援的事情 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式碼都能做。  但對於在桌面上和其他 HWND 互動方面，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 必須遵從 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 處理和呈現規則。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 支援非矩形視窗，以 HRGN 支援非矩形視窗，以層次視窗支援每像素 Alpha 值。  
  
 常數 Alpha 和色彩鍵則不支援。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 層次視窗功能依平台而不同。  
  
 層次視窗可以透過指定要套用到視窗中各個像素的 Alpha 值，將整個視窗變成半透明   \(雖然 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 實際上可支援每像素 Alpha 值，但是在實際的程式中，要使用這項功能非常困難，因為在這種模式下，您必須自行繪製任何子 HWND，包括對話方塊和下拉式清單\)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援 HRGN，但是這項功能沒有 Managed [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  您可以使用平台叫用和 <xref:System.Windows.Interop.HwndSource> 呼叫相關的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  如需詳細資訊，請參閱[從 Managed 程式碼呼叫原生函式](../Topic/Calling%20Native%20Functions%20from%20Managed%20Code.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 層次視窗在不同的作業系統上具有不同的功能。  這是因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 來呈現，而層次視窗主要是針對 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 呈現所設計，而非 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 呈現。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援 [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] \(含\) 以後版本中的硬體加速層次視窗。  [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] 上的硬體加速層次視窗需要 [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] 的支援，因此其功能視該電腦上的 [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] 版本而定。  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不支援透明色彩鍵，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 無法保證能夠呈現您所要求的正確色彩，尤其是當採用硬體加速進行呈現時。  
  
-   如果您的應用程式是在 [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] 上執行，在呈現 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 應用程式時，[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 介面最上層的層次視窗會出現閃動的情況   \(實際的呈現順序是 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 隱藏層次視窗，接著由 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 進行繪製，然後 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 將層次放回原位\)。  非 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 層次視窗也有這項限制。  
  
## 請參閱  
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [逐步解說：在 Win32 中裝載 WPF 時鐘](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-clock-in-win32.md)   
 [在 WPF 中裝載 Win32 內容](../../../../docs/framework/wpf/advanced/hosting-win32-content-in-wpf.md)