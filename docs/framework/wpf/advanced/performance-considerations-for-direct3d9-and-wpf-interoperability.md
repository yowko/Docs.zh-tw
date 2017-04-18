---
title: "Direct3D9 和 WPF 互通性的效能考量 | Microsoft Docs"
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
  - "Direct3D9 [WPF 互通性], 效能"
  - "WPF, Direct3D9 Interop 效能"
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Direct3D9 和 WPF 互通性的效能考量
您可以使用 <xref:System.Windows.Interop.D3DImage> 類別裝載 Direct3D9 內容。  裝載 Direct3D9 內容可能會影響應用程式的效能。  本主題說明在 Windows Presentation Foundation \(WPF\) 應用程式中裝載 Direct3D9 內容時，有關最佳化效能的最佳作法。  這些最佳作法包含使用 Windows Vista、Windows XP 和多監視器顯示環境時，有關 <xref:System.Windows.Interop.D3DImage> 的使用方式和最佳作法。  
  
> [!NOTE]
>  如需示範這些最佳作法的程式碼範例，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。  
  
## 謹慎使用 D3DImage  
 在 <xref:System.Windows.Interop.D3DImage> 執行個體中裝載 Direct3D9 內容的呈現速度，不如純 Direct3D 應用程式中的速度那麼快。  複製介面和清除命令緩衝區可能會是耗費資源的作業。  隨著 <xref:System.Windows.Interop.D3DImage> 執行個體數目的增加，會更頻繁地發生清除作業，進而降低效能。  因此，您應該謹慎使用 <xref:System.Windows.Interop.D3DImage>。  
  
## Windows Vista 上的最佳作法  
 對於顯示設定為使用 Windows 顯示驅動程式模型 \(WDDM\) 的 Windows Vista，若要獲得最佳效能，則要對 `IDirect3DDevice9Ex` 裝置建立 Direct3D9 介面。  這樣會啟用介面共用。  而視訊卡必須支援 Windows Vista 上的 `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` 和 `D3DCAPS2_CANSHARERESOURCE` 驅動程式功能。  至於任何其他透過軟體複製介面的設定，則會大幅降低效能。  
  
> [!NOTE]
>  如果 Windows Vista 的顯示設定是使用 Windows XP 顯示驅動程式模型 \(XDDM\)，則不管設定為何，一定會透過軟體複製介面。  搭配適當的設定和視訊卡，可以讓您在使用 WDDM 時看到較佳的 Windows Vista 效能，因為介面複製的作業是以硬體執行的。  
  
## Windows XP 上的最佳作法  
 對於使用 Windows XP 顯示驅動程式模型 \(XDDM\) 的 Windows XP，若要獲得最佳效能，則要建立呼叫 `IDirect3DSurface9::GetDC` 方法時能正確運作的可鎖定介面。  在內部處理上，`BitBlt` 方法是以硬體進行跨裝置傳輸介面的動作。  `GetDC` 方法在 XRGB 介面一定能夠運作。  但是，如果用戶端電腦執行的是 Windows XP SP3 或 SP2，以及用戶端同時具備層次視窗功能的 Hotfix，則此方法只能在 ARGB 介面運作。  而視訊卡必須支援 `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` 驅動程式功能。  
  
 16 位元桌面顯示深度會大幅降低效能，  建議使用 32 位元桌面。  
  
 如果是針對 Windows Vista 和 Windows XP 進行開發，請在 Windows XP 上測試效能。  這是考量到可能會耗盡 Windows XP 上的視訊記憶體。  除此之外，Windows XP 上的 <xref:System.Windows.Interop.D3DImage> 會比 Windows Vista WDDM 使用更多的視訊記憶體和頻寬，這是因為需要額外的視訊記憶體複製作業。  因此，對於相同的視訊硬體，您可以預期 Windows XP 上的效能會比 Windows Vista 來得差。  
  
> [!NOTE]
>  在 Windows XP 和 Windows Vista 上都可以使用 XDDM，但 WDDM 卻只能在 Windows Vista 上使用。  
  
## 一般最佳作法  
 建立裝置時，請使用 `D3DCREATE_MULTITHREADED` 建立旗標。  這樣會降低效能，但可以讓 WPF 呈現系統從其他執行緒呼叫這個裝置的方法。  請務必正確遵循鎖定通訊協定，這樣才不會有兩個執行緒同時存取該裝置。  
  
 如果呈現作業是在 WPF Managed 執行緒上執行的話，強烈建議您使用 `D3DCREATE_FPU_PRESERVE` 建立旗標來建立裝置。  如果沒有這個設定，D3D 呈現作業會降低 WPF 雙精度作業的準確性，並帶來呈現問題。  
  
 並排顯示 <xref:System.Windows.Interop.D3DImage> 是很快速的，除非您是在沒有硬體支援的情況下並排顯示非 pow2 介面，或者您並排顯示的 <xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush> 包含 <xref:System.Windows.Interop.D3DImage>。  
  
## 多監視器顯示環境的最佳作法  
 如果您使用的電腦具有多個監視器，則應該遵循前述的最佳作法。  對於多監視器組態，還有一些額外的效能考量。  
  
 建立背景緩衝區時，是針對特定裝置和配接器而建立的，但 WPF 卻可能會在任何配接器上顯示前景緩衝區。  以跨配接器的複製方式更新前景緩衝區是非常耗費資源的。  如果 Windows Vista 是設為使用 WDDM 並具有多個視訊卡和單一 `IDirect3DDevice9Ex` 裝置，當前景緩衝區是位於不同的配接器但仍在相同的視訊卡上時，並不會影響到效能。  然而，對於 Windows XP 和 XDDM 搭配多個視訊卡的情況，如果前景緩衝區不是在背景緩衝區的配接器上顯示的話，就會大幅影響效能。  如需詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。  
  
## 效能摘要  
 下表顯示隨著作業系統、像素格式和介面鎖定性的功能不同，前景緩衝區更新的效能狀況。  這裡假設前景緩衝區和背景緩衝區位於相同配接器上。  依據配接器的組態而定，硬體更新通常比軟體更新快很多。  
  
|介面像素格式|Windows Vista、WDDM 和 9Ex|其他 Windows Vista 組態|Windows XP SP3 或 SP2 搭配 Hotfix|Windows XP SP2|  
|------------|------------------------------|-------------------------|------------------------------------|--------------------|  
|D3DFMT\_X8R8G8B8 \(不可鎖定\)|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT\_X8R8G8B8 \(可鎖定\)|**硬體更新**|軟體更新|**硬體更新**|**硬體更新**|  
|D3DFMT\_A8R8G8B8 \(不可鎖定\)|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT\_A8R8G8B8 \(可鎖定\)|**硬體更新**|軟體更新|**硬體更新**|軟體更新|  
  
## 請參閱  
 <xref:System.Windows.Interop.D3DImage>   
 [WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)   
 [逐步解說：建立裝載於 WPF 中的 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)   
 [逐步解說：在 WPF 中裝載 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)