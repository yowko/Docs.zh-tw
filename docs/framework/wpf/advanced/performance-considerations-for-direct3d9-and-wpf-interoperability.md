---
title: Direct3D9 和 WPF 互通性的效能考量
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 52085579c2a432e7db1ebec096a931e0d51718f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 和 WPF 互通性的效能考量
您可以使用主控 Direct3D9 內容<xref:System.Windows.Interop.D3DImage>類別。 裝載 Direct3D9 內容可能會影響應用程式的效能。 本主題說明裝載 Direct3D9 Windows Presentation Foundation (WPF) 應用程式中的內容時最佳化效能的最佳作法。 這些最佳作法 」 包含如何使用<xref:System.Windows.Interop.D3DImage>和最佳作法，當您使用 Windows Vista、 Windows XP 中，並多螢幕顯示。  
  
> [!NOTE]
>  如需程式碼範例示範這些最佳作法，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。  
  
## <a name="use-d3dimage-sparingly"></a>盡量不要使用 D3DImage  
 Direct3D9 內容裝載在<xref:System.Windows.Interop.D3DImage>一樣快，如同在單純的 Direct3D 應用程式不會呈現執行個體。 複製介面和命令緩衝區排清可能耗費資源的作業。 以數<xref:System.Windows.Interop.D3DImage>執行個體增加更多排清進行，而且會降低效能。 因此，您應該使用<xref:System.Windows.Interop.D3DImage>謹慎使用。  
  
## <a name="best-practices-on-windows-vista"></a>在 Windows Vista 上的最佳作法  
 與已設定為使用 Windows 顯示驅動程式模型 (WDDM) 顯示在 Windows Vista 上獲得最佳效能，請建立 Direct3D9 介面上`IDirect3DDevice9Ex`裝置。 這可讓設定共用的介面。 視訊卡必須支援`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`和`D3DCAPS2_CANSHARERESOURCE`Windows Vista 上的驅動程式功能。 任何其他設定會導致複製透過軟體會大幅降低效能的介面。  
  
> [!NOTE]
>  如果 Windows Vista 具有顯示設定為使用 Windows XP 顯示驅動程式模型 (XDDM)，在介面一律會複製透過軟體，不論設定為何。 設定適當的設定和視訊卡，您將更佳的效能在 Windows Vista 上使用時，看到 WDDM 因為介面的複本都執行中的硬體。  
  
## <a name="best-practices-on-windows-xp"></a>在 Windows XP 上的最佳作法  
 為了達到最佳效能，在 Windows XP 中，使用 Windows XP 顯示驅動程式模型 (XDDM)，可建立正確的行為可鎖定型介面時`IDirect3DSurface9::GetDC`方法呼叫。 就內部而言，`BitBlt`在硬體裝置之間傳輸介面的方法。 `GetDC`方法永遠都可運作 XRGB 表面上。 不過，如果用戶端電腦執行 Windows XP SP3 或 SP2，而且用戶端也會有適用於分層視窗功能的 hotfix，這個方法僅適用於 ARGB 介面。 視訊卡必須支援`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`驅動程式功能。  
  
 16 位元桌面顯示深度可以大幅降低效能。 建議使用 32 位元桌面。  
  
 如果您正在開發 Windows Vista 和 Windows XP 中，測試 Windows XP 上的效能。 在 Windows XP 上的視訊記憶體不足是一項考量。 此外，<xref:System.Windows.Interop.D3DImage>在 Windows XP 上使用多個視訊記憶體和頻寬比 Windows Vista WDDM，因為需要額外的視訊記憶體複本。 因此，您可以預期要在比 Windows Vista 上的 Windows XP 上更糟的是相同的視訊硬體的效能。  
  
> [!NOTE]
>  XDDM 是適用於 Windows XP 和 Windows Vista;不過，WDDM 是僅適用於 Windows Vista。  
  
## <a name="general-best-practices"></a>一般最佳作法  
 當您建立裝置時，使用`D3DCREATE_MULTITHREADED`建立旗標。 這樣會降低效能，但 WPF 呈現系統此裝置上呼叫方法，從另一個執行緒。 請務必遵循鎖定通訊協定正確，這樣沒有兩個執行緒同時存取裝置。  
  
 如果您呈現 WPF managed 執行緒上執行時，強烈建議您建立與裝置`D3DCREATE_FPU_PRESERVE`建立旗標。 未進行此設定，D3D 轉譯減少 WPF 雙精確度運算的精確度以及產生轉譯的問題。  
  
 並排<xref:System.Windows.Interop.D3DImage>是快速，除非您並排顯示不含硬體支援的非 pow2 介面，或您並排<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>包含<xref:System.Windows.Interop.D3DImage>。  
  
## <a name="best-practices-for-multi-monitor-displays"></a>多重監視器的顯示畫面的最佳作法  
 如果您使用具有多個監視器的電腦，您應該遵循先前所述的最佳作法。 另外還有一些其他的效能考量多監視器設定。  
  
 當您建立背景緩衝區時，建立在特定裝置和配接器，但 WPF 可能會顯示任何配接器前端的緩衝區。 配接器，來更新前端緩衝區之間複製是非常耗費資源。 在已設定為使用多個視訊卡與使用 WDDM 的 Windows Vista 上`IDirect3DDevice9Ex`裝置，如果前端緩衝區位於不同的介面卡，但仍相同的視訊卡，沒有任何效能產生負面影響。 不過，在 Windows XP 和多個視訊卡與 XDDM，顯著的效能損失時沒有前端緩衝區會顯示在背景緩衝區的配接器。 如需詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。  
  
## <a name="performance-summary"></a>效能摘要  
 下表顯示的作業系統、 像素格式和介面的前景函式的緩衝區更新的效能。 前端緩衝區和背景緩衝區會假設為相同的介面卡上。 根據配接器組態，硬體更新是一般速度比軟體更新。  
  
|介面的像素格式|Windows Vista、 WDDM 和 9Ex|Windows Vista 的其他組態|Windows XP SP3 或 SP2 與 hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 （不可鎖定型）|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT_X8R8G8B8 （可鎖定型）|**硬體更新**|軟體更新|**硬體更新**|**硬體更新**|  
|D3DFMT_A8R8G8B8 （不可鎖定型）|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT_A8R8G8B8 （可鎖定型）|**硬體更新**|軟體更新|**硬體更新**|軟體更新|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Interop.D3DImage>  
 [WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [逐步解說：建立裝載於 WPF 中的 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [逐步解說：在 WPF 中裝載 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
