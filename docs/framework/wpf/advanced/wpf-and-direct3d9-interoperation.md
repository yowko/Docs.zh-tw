---
title: WPF 和 Direct3D9 interop
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 9ec83c48052e1ef29bb91a6b40b7c76f671bb99f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735190"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF 和 Direct3D9 互通
您可以將 Direct3D9 內容包含在 Windows Presentation Foundation （WPF）應用程式中。 本主題說明如何建立 Direct3D9 內容，以便與 WPF 有效率地互通。  
  
> [!NOTE]
> 在 WPF 中使用 Direct3D9 內容時，您也必須考慮效能。 如需如何優化效能的詳細資訊，請參閱[Direct3D9 和 WPF 互通性的效能考慮](performance-considerations-for-direct3d9-and-wpf-interoperability.md)。  
  
## <a name="display-buffers"></a>顯示緩衝區  
 <xref:System.Windows.Interop.D3DImage> 類別會管理兩個顯示緩衝區，稱為「*後緩衝區*」和「*前端緩衝區*」。 背景工作緩衝區是您的 Direct3D9 介面。 當您呼叫 <xref:System.Windows.Interop.D3DImage.Unlock%2A> 方法時，會將後端緩衝區的變更向前複製到前一個緩衝區。  
  
 下圖顯示背景工作緩衝區與前端緩衝區之間的關聯性。  
  
 ![System.windows.interop.d3dimage> 實作顯示緩衝區](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>建立 Direct3D9 裝置  
 若要呈現 Direct3D9 內容，您必須建立 Direct3D9 裝置。 有兩個 Direct3D9 物件可用來建立裝置，`IDirect3D9` 和 `IDirect3D9Ex`。 使用這些物件分別建立 `IDirect3DDevice9` 和 `IDirect3DDevice9Ex` 裝置。  
  
 藉由呼叫下列其中一種方法來建立裝置。  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 在 Windows Vista 或更新版本的作業系統上，請使用 `Direct3DCreate9Ex` 方法，並搭配設定為使用 Windows 顯示驅動程式模型（WDDM）的顯示。 在任何其他平臺上使用 `Direct3DCreate9` 方法。  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Direct3DCreate9Ex 方法的可用性  
 D3d9 只在 Windows Vista 或更新版本的作業系統上具有 `Direct3DCreate9Ex` 方法。 如果您直接連結 Windows XP 上的函式，您的應用程式將無法載入。 若要判斷是否支援 `Direct3DCreate9Ex` 方法，請載入 DLL 並尋找 proc 位址。 下列程式碼顯示如何測試 `Direct3DCreate9Ex` 方法。 如需完整的程式碼範例，請參閱[逐步解說：建立在 WPF 中裝載的 Direct3D9 內容](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>HWND 建立  
 建立裝置需要 HWND。 一般來說，您會建立虛擬 HWND 供 Direct3D9 使用。 下列程式碼範例顯示如何建立虛擬 HWND。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>呈現參數  
 建立裝置也需要 `D3DPRESENT_PARAMETERS` 結構，但只有幾個參數很重要。 選擇這些參數可將記憶體使用量降到最低。  
  
 將 `BackBufferHeight` 和 `BackBufferWidth` 欄位設定為1。 將它們設定為0會使它們設定為 HWND 的維度。  
  
 請一律設定 `D3DCREATE_MULTITHREADED` 和 `D3DCREATE_FPU_PRESERVE` 旗標，以防止 Direct3D9 所使用的記憶體損毀，並防止 Direct3D9 變更 FPU 設定。  
  
 下列程式碼顯示如何初始化 `D3DPRESENT_PARAMETERS` 結構。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>建立背景緩衝區呈現目標  
 若要在 <xref:System.Windows.Interop.D3DImage>中顯示 Direct3D9 內容，您可以建立 Direct3D9 介面，並藉由呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法來指派它。  
  
### <a name="verifying-adapter-support"></a>驗證介面卡支援  
 建立介面之前，請確認所有介面卡都支援您需要的介面屬性。 即使您只轉譯為一個介面卡，WPF 視窗可能還是會顯示在系統中的任何介面卡上。 您應該一律撰寫 Direct3D9 程式碼來處理多個介面卡設定，而且您應該檢查所有介面卡的支援，因為 WPF 可能會在可用的介面卡之間移動介面。  
  
 下列程式碼範例顯示如何檢查系統上的所有介面卡是否有 Direct3D9 支援。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>建立介面  
 建立介面之前，請確認裝置功能在目標作業系統上支援良好的效能。 如需詳細資訊，請參閱[Direct3D9 和 WPF 互通性的效能考慮](performance-considerations-for-direct3d9-and-wpf-interoperability.md)。  
  
 當您已驗證裝置功能時，您可以建立介面。 下列程式碼範例顯示如何建立轉譯目標。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 在設定為使用 WDDM 的 Windows Vista 和更新版本作業系統上，您可以建立轉譯目標材質，並將層級0介面傳遞至 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法。 在 Windows XP 上不建議使用此方法，因為您無法建立可鎖定的轉譯目標材質，而且效能將會降低。  
  
## <a name="handling-device-state"></a>處理裝置狀態  
 <xref:System.Windows.Interop.D3DImage> 類別會管理兩個顯示緩衝區，稱為「*後緩衝區*」和「*前端緩衝區*」。 背景緩衝區是您的 Direct3D 介面。  當您呼叫 <xref:System.Windows.Interop.D3DImage.Unlock%2A> 方法（在硬體上顯示）時，會將後端緩衝區的變更向前複製到前端緩衝區。 有時，前端緩衝區會變成無法使用。 此缺乏可用性的原因可能是螢幕鎖定、全螢幕專有 Direct3D 應用程式、使用者切換或其他系統活動。 發生這種情況時，您的 WPF 應用程式會藉由處理 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> 事件來收到通知。  您的應用程式如何回應前端緩衝區變得無法使用，取決於是否已啟用 WPF 來切換回軟體轉譯。 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 的方法具有多載，可接受指定 WPF 是否切換回軟體呈現的參數。  
  
 當您呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> 多載，或使用設定為 `false`的 `enableSoftwareFallback` 參數來呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> 多載時，轉譯系統會在前端緩衝區無法使用且沒有顯示任何內容時，釋放它對後端緩衝區的參考。 當前端緩衝區再次可供使用時，轉譯系統會引發 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> 事件來通知您的 WPF 應用程式。  您可以為 <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> 事件建立事件處理常式，以使用有效的 Direct3D 介面重新開機轉譯。 若要重新開機轉譯，您必須呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>。  
  
 當您呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> 多載，並將 `enableSoftwareFallback` 參數設定為 `true`時，轉譯系統會在前端緩衝區無法使用時，保留其對後端緩衝區的參考，因此當前端緩衝區再次可用時，不需要呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>。  
  
 啟用軟體轉譯時，可能會發生使用者裝置無法使用的情況，但是轉譯系統會保留 Direct3D 介面的參考。 若要檢查 Direct3D9 裝置是否無法使用，請呼叫 `TestCooperativeLevel` 方法。 若要檢查 Direct3D9Ex 裝置，請呼叫 `CheckDeviceState` 方法，因為 `TestCooperativeLevel` 方法已被取代，且一律會傳回成功。 如果使用者裝置變得無法使用，請呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 以釋放對後緩衝區的 WPF 參考。  如果您需要重設裝置，請呼叫 `backBuffer` 參數設定為 `null`的 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>，然後再次呼叫 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>，並將 `backBuffer` 設定為有效的 Direct3D 介面。  
  
 只有在您執行多介面卡支援時，才能呼叫 `Reset` 方法，從不正確裝置進行復原。 否則，請釋放所有 Direct3D9 介面，並完全重新建立它們。 如果介面卡配置已變更，則在變更之前建立的 Direct3D9 物件不會更新。  
  
## <a name="handling-resizing"></a>處理調整大小  
 如果 <xref:System.Windows.Interop.D3DImage> 顯示于其原生大小以外的解析度，則會根據目前的 <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>進行調整，但 <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> 會取代為 <xref:System.Windows.Media.BitmapScalingMode.Fant>。  
  
 如果您需要更高的精確度，當 <xref:System.Windows.Interop.D3DImage> 的容器變更大小時，您必須建立新的介面。  
  
 有三種可能的方法可以處理調整大小。  
  
- 參與版面配置系統，並在大小變更時建立新的表面。 請勿建立太多表面，因為您可能會耗盡或分段視訊記憶體。  
  
- 等到有一段固定的時間未發生調整大小事件，才能建立新的表面。  
  
- 建立每秒檢查容器維度數次的 <xref:System.Windows.Threading.DispatcherTimer>。  
  
## <a name="multi-monitor-optimization"></a>多監視器優化  
 當轉譯系統將 <xref:System.Windows.Interop.D3DImage> 移到另一個監視器時，可能會導致效能大幅降低。  
  
 在 WDDM 上，只要監視器位於相同的視訊卡上，而且您使用 `Direct3DCreate9Ex`，就不會降低效能。 如果監視器位於不同的視訊卡上，效能就會降低。 在 Windows XP 上，一律會降低效能。  
  
 當 <xref:System.Windows.Interop.D3DImage> 移到另一個監視器時，您可以在對應的介面卡上建立新的介面，以還原良好的效能。  
  
 若要避免效能降低，請特別針對多監視器案例撰寫程式碼。 下列清單顯示撰寫多監視器程式碼的一種方式。  
  
1. 使用 `Visual.ProjectToScreen` 方法尋找螢幕空間中的 <xref:System.Windows.Interop.D3DImage> 點。  
  
2. 使用 `MonitorFromPoint` GDI 方法來尋找顯示點的監視器。  
  
3. 使用 `IDirect3D9::GetAdapterMonitor` 方法來尋找監視器所在的 Direct3D9 介面卡。  
  
4. 如果介面卡與背面緩衝區不同，請在新的監視器上建立新的後置緩衝區，並將它指派給 <xref:System.Windows.Interop.D3DImage> 的背景緩衝區。  
  
> [!NOTE]
> 如果 <xref:System.Windows.Interop.D3DImage> 跨越監視，則效能會變慢，除非 WDDM 和 `IDirect3D9Ex` 在相同介面卡上。 在這種情況下，沒有任何方法可以改善效能。  
  
 下列程式碼範例顯示如何尋找目前的監視器。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 當 <xref:System.Windows.Interop.D3DImage> 容器的大小或位置變更時，請更新監視器，或使用每秒更新數次的 `DispatcherTimer` 更新監視器。  
  
## <a name="wpf-software-rendering"></a>WPF 軟體轉譯  
 WPF 會在下列情況中，以同步方式在軟體的 UI 執行緒上呈現。  
  
- 列印  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 發生上述其中一種情況時，轉譯系統會呼叫 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> 方法，將硬體緩衝區複製到軟體。 預設的實作為使用您的介面呼叫 `GetRenderTargetData` 方法。 因為此呼叫是在鎖定/解除鎖定模式以外發生，所以可能會失敗。 在此情況下，`CopyBackBuffer` 方法會傳回 `null` 而不會顯示任何影像。  
  
 您可以覆寫 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> 方法、呼叫基底實作為，如果它傳回 `null`，您就可以傳回 <xref:System.Windows.Media.Imaging.BitmapSource>的預留位置。  
  
 您也可以執行自己的軟體轉譯，而不是呼叫基底實作為。  
  
> [!NOTE]
> 如果 WPF 完全呈現在軟體中，則不會顯示 <xref:System.Windows.Interop.D3DImage>，因為 WPF 沒有前端緩衝區。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 和 WPF 互通性的效能考量](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [逐步解說：建立裝載於 WPF 中的 Direct3D9 內容](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [逐步解說：在 WPF 中裝載 Direct3D9 內容](walkthrough-hosting-direct3d9-content-in-wpf.md)
