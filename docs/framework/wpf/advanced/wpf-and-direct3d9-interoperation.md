---
title: "WPF 和 Direct3D9 互通 | Microsoft Docs"
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
  - "Direct3D9 [WPF 互通性], 建立 Direct3D9 內容"
  - "WPF, 建立 Direct3D9 內容"
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# WPF 和 Direct3D9 互通
您可以將 Direct3D9 內容包含在 Windows Presentation Foundation \(WPF\) 應用程式中。  這個主題會說明如何建立 Direct3D9 內容，以能有效率地和 WPF 交互操作。  
  
> [!NOTE]
>  在 WPF 中使用 Direct3D9 內容時，您也需要考慮效能。  如需如何最佳化效能的詳細資訊，請參閱 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)。  
  
## 顯示緩衝區  
 <xref:System.Windows.Interop.D3DImage> 類別管理兩個顯示緩衝區，分別稱為「*背景緩衝區*」\(Back Buffer\) 和「*前景緩衝區*」\(Front Buffer\)。  背景緩衝區是您的 Direct3D9 介面。  當您呼叫 <xref:System.Windows.Interop.D3DImage.Unlock%2A> 方法時，對背景緩衝區的變更會複製到前景緩衝區。  
  
 下圖顯示了背景緩衝區和前景緩衝區之間的關聯性 \(Relationship\)。  
  
 ![D3DImage 顯示緩衝區](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage\_buffers")  
  
## 建立 Direct3D9 裝置  
 若要呈現 Direct3D9 內容，您必須建立 Direct3D9 裝置。  有兩種 Direct3D9 物件可以用於建立裝置，分別是 `IDirect3D9` 和 `IDirect3D9Ex`。  請使用這些物件分別建立 `IDirect3DDevice9` 和 `IDirect3DDevice9Ex` 裝置。  
  
 透過呼叫下列方法之一建立裝置。  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 在 Windows Vista \(含\) 以後版本的作業系統上，請使用設定為使用 Windows 顯示驅動程式模型 \(WDDM\) 之顯示的 `Direct3DCreate9Ex` 方法。  對於其他的任何平台，請使用 `Direct3DCreate9` 方法。  
  
### Direct3DCreate9Ex 方法的可用性  
 這個 `Direct3DCreate9Ex` d3d9.dll 具有僅在 Windows Vista \(含\) 以後版本的作業系統。  如果您在 Windows XP 上直接連結此函式，您的應用程式將無法載入。  若要判斷是否支援 `Direct3DCreate9Ex` 方法，請載入 DLL 並尋找程序位址。  下列程式碼顯示如何測試 `Direct3DCreate9Ex` 方法。  如需完整的程式碼範例，請參閱[逐步解說：建立裝載於 WPF 中的 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### 建立 HWND  
 建立需要 HWND 的裝置。  一般而言，您可以建立空的 HWND 供 Direct3D9 使用。  下列程式碼範例顯示如何建立空的 HWND。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### 呈現參數  
 建立裝置也需要 `D3DPRESENT_PARAMETERS` 結構，但只有少數參數比較重要。  選擇這些參數是為了最小化記憶體耗用量。  
  
 將 `BackBufferHeight` 和 `BackBufferWidth` 欄位設定為 1。  將這兩個欄位設定為 0 會使它們設為 HWND 的維度。  
  
 一定要設定 `D3DCREATE_MULTITHREADED` 和 `D3DCREATE_FPU_PRESERVE` 旗標，以避免中斷 Direct3D9 使用的記憶體，以及避免 Direct3D9 變更 FPU 設定。  
  
 下列程式碼顯示如何初始化 `D3DPRESENT_PARAMETERS` 結構。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## 建立背景緩衝區呈現目標  
 若要在 <xref:System.Windows.Interop.D3DImage> 中顯示 Direct3D9 內容，則建立 Direct3D9 介面，並呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法，以對 Direct3D9 介面進行指派。  
  
### 驗證配接器支援  
 在建立介面前，驗證是否所有的配接器都支援您需要的介面屬性。  就算您僅呈現至一種配接器，在系統中的任何一個配接器上都可能顯示此 WPF 視窗。  您應該永遠撰寫處理多配接器設定的 Direct3D9 程式碼，並應該檢查所有的配接器以取得支援，因為 WPF 可能在可用的配接器間移動介面。  
  
 下列程式碼範例示範如何檢查系統上所有配接器的 Direct3D9 支援。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### 建立介面  
 在建立介面前，驗證裝置的功能是否支援在目標作業系統上產生良好的效能。  如需詳細資訊，請參閱 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)。  
  
 在您已驗證裝置的功能後，就可以建立介面。  下列程式碼範例示範如何建立呈現目標。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### WDDM  
 在 Windows Vista \(含\) 以後版本的作業系統上，設定為使用 WDDM，您可以建立呈現目標紋理並將層級 0 的介面傳遞給 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法。  我們不建議在 Windows XP 上使用這個方法，因為您無法建立可鎖定的呈現目標紋理，效能將因此降低。  
  
## 處理裝置狀態  
 <xref:System.Windows.Interop.D3DImage> 類別管理兩個顯示緩衝區，分別稱為「*背景緩衝區*」\(Back Buffer\) 和「*前景緩衝區*」\(Front Buffer\)。  背景緩衝區為您的 Direct3D 介面。  對背景緩衝區的變更會複製到前景緩衝區 <xref:System.Windows.Interop.D3DImage.Unlock%2A> ，當您呼叫方法時，會在硬體中顯示。  有時候，前景緩衝區將無法使用。  可能造成無法使用的情況有：畫面鎖定、獨佔全螢幕的 Direct3D 應用程式、使用者切換或其他系統活動等。  發生這種情況時，您的 WPF 應用程式處理 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> 事件通知。  您的應用程式如何回應變成前端緩衝區無法使用相依於 WPF 是否啟用切換回軟體轉譯。  <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法具有接受參數的多載 WPF 是否切換回軟體轉譯。  
  
 當您呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> 多載或 `enableSoftwareFallback` 呼叫具有參數的多載 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> 設為 `false`時，呈現系統會釋放對背景緩衝區的參考，如果前景緩衝區無法使用時，而則不會顯示。  如果前景緩衝區可以再次使用時，呈現系統會引發 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> 事件告知您的 WPF 應用程式。  您可以建立 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> 事件的事件處理常式可以重新啟動重新呈現具有有效的 Direct3D 介面。  若要重新開始轉換，您必須呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>。  
  
 當您呼叫與 `enableSoftwareFallback` 參數的多載 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> 設為 `true`時，呈現系統會保留它對背景緩衝區的參考，如果前景緩衝區無法使用時，因此不需要呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 的情況，如果前景緩衝區可以再次使用時。  
  
 當軟體轉譯啟用時，可能會有使用者裝置無法使用的情況，不過，呈現系統保留 Direct3D 介面的參考。  若要檢查 Direct3D9 裝置是否無法使用，請呼叫方法。 `TestCooperativeLevel` 因為 `TestCooperativeLevel` 方法已被取代，且永遠傳回成功想要檢查 Direct3D9Ex 裝置 `CheckDeviceState` 呼叫方法。  如果使用者裝置無法使用，呼叫釋放背景緩衝區的 WPF 中參考的 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 。  如果您需要重設裝置，請使用 `backBuffer` 參數的 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 設為 `null`，然後再次呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 和 `backBuffer` 設為有效的 Direct3D 介面。  
  
 只有當您實作多配接器支援時，才呼叫 `Reset` 方法，由無效的裝置復原。  不然就釋放所有的 Direct3D9 介面，全部重新建立。  如果配接器的版面配置改變，在變更前建立的 Direct3D9 物件不會更新。  
  
## 處理大小調整  
 不是原生大小之外，如果 <xref:System.Windows.Interop.D3DImage> 所顯示的解析度，它會根據目前 <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>縮放，不同的是， <xref:System.Windows.Media.Effects.SamplingMode> 以 <xref:System.Windows.Media.BitmapScalingMode>替代。  
  
 如果您需要更高的精確度，則必須在 <xref:System.Windows.Interop.D3DImage> 的容器大小變更時建立新的介面。  
  
 能夠處理大小調整的方法有三種。  
  
-   加入配置系統，並在大小變更時建立新的介面。  不要建立太多介面，因為您可能會讓視訊記憶體耗盡或分割化。  
  
-   在等待一定時間後，如果重新調整大小的事件沒有發生，再建立新的介面。  
  
-   建立 <xref:System.Windows.Threading.DispatcherTimer>，每秒鐘檢查幾次容器維度。  
  
## 多監視器最佳化  
 當呈現系統將 <xref:System.Windows.Interop.D3DImage> 移動至另一個監視器，可能造成效能大幅降低。  
  
 在 WDDM 上，只要監視器在同一個視訊卡上，且您使用 `Direct3DCreate9Ex`，效能就不會降低。  如果監視器在不同的視訊卡上，效能會降低。  在 Windows XP 上，效能一定會降低。  
  
 當 <xref:System.Windows.Interop.D3DImage> 移動至另一個監視器時，您可以在對應的配接器上建立新的介面，以還原為良好的效能。  
  
 若要避免效能減損，請特別為多監視器的情形撰寫程式碼。  下列清單顯示撰寫多監視器程式碼的一種方法。  
  
1.  以 `Visual.ProjectToScreen` 方法在螢幕空間中找到 <xref:System.Windows.Interop.D3DImage> 的一個點。  
  
2.  使用 `MonitorFromPoint` GDI 方法尋找顯示這個點的監視器。  
  
3.  使用 `IDirect3D9::GetAdapterMonitor` 方法尋找這個監視器所在的 Direct3D9 配接器。  
  
4.  如果配接器和有背景緩衝區的配接器不同，就在新的監視器上建立新的背景緩衝區，並指派至 <xref:System.Windows.Interop.D3DImage> 背景緩衝區。  
  
> [!NOTE]
>  如果 <xref:System.Windows.Interop.D3DImage> 橫跨多個監視器，效能會變低，除非 WDDM 和 `IDirect3D9Ex` 是在同一個配接器。  在這樣的情況中沒有任何方法可以提升效能。  
  
 下列程式碼範例顯示如何尋找目前的監視器。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 當 <xref:System.Windows.Interop.D3DImage> 容器的大小或位置改變時更新監視器，或使用每秒鐘更新幾次的 `DispatcherTimer` 更新監視器。  
  
## WPF 軟體呈現  
 在下列情況中，WPF 會在軟體中的 UI 執行緒上同步呈現。  
  
-   列印  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 當發生這些情況之一時，呈現系統會呼叫 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> 方法以將硬體緩衝區複製到軟體。  預設實作會以您的介面呼叫 `GetRenderTargetData` 方法。  由於這個呼叫發生於 Lock\/Unlock 模式外，因此可能會發生失敗。  在這個情況中，`CopyBackBuffer` 方法會傳回 `null` 且不會顯示任何影像。  
  
 您可以覆寫 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> 方法，呼叫基底實作，如果傳回 `null`，您可以傳回預留位置 <xref:System.Windows.Media.Imaging.BitmapSource>。  
  
 您也可以實作自己的軟體呈現，而不要呼叫基底實作。  
  
> [!NOTE]
>  如果 WPF 在軟體中完整呈現，因為 WPF 沒有前景緩衝區，就不會顯示 <xref:System.Windows.Interop.D3DImage>。  
  
## 請參閱  
 <xref:System.Windows.Interop.D3DImage>   
 [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)   
 [逐步解說：建立裝載於 WPF 中的 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)   
 [逐步解說：在 WPF 中裝載 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)