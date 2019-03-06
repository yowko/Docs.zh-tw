---
title: Direct3D9 和 WPF 互通性的效能考量
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: fd3c99f22a1d097c82494ba6eff344820162ed87
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356711"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 和 WPF 互通性的效能考量
您可以使用來裝載 Direct3D9 內容<xref:System.Windows.Interop.D3DImage>類別。 裝載 Direct3D9 內容可能會影響您的應用程式的效能。 本主題說明裝載在 Windows Presentation Foundation (WPF) 應用程式中的 Direct3D9 內容時將效能最佳化的最佳作法。 這些最佳作法包括如何使用<xref:System.Windows.Interop.D3DImage>和最佳作法，當您使用 Windows Vista、 Windows XP 和多重監視器 」 會顯示。  
  
> [!NOTE]
>  如需程式碼範例示範這些最佳作法，請參閱[WPF 和 Direct3D9 互通](wpf-and-direct3d9-interoperation.md)。  
  
## <a name="use-d3dimage-sparingly"></a>盡量不要使用 D3DImage  
 在中裝載 Direct3D9 內容<xref:System.Windows.Interop.D3DImage>執行個體不會轉譯為純虛擬的 Direct3D 應用程式那樣快。 複製在介面和排清命令緩衝區可耗費資源的作業。 為數個<xref:System.Windows.Interop.D3DImage>執行個體增加更多的排清會進行，而且效能降低。 因此，您應該使用<xref:System.Windows.Interop.D3DImage>謹慎使用。  
  
## <a name="best-practices-on-windows-vista"></a>在 Windows Vista 上的最佳作法  
 與顯示設定為使用 Windows 顯示驅動程式模型 (WDDM) 在 Windows Vista 上達到最佳效能，請建立 Direct3D9 介面上`IDirect3DDevice9Ex`裝置。 這可讓設定共用的介面。 視訊卡必須支援`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`和`D3DCAPS2_CANSHARERESOURCE`在 Windows Vista 上的驅動程式功能。 任何其他設定會導致透過大幅降低效能的軟體要複製的介面。  
  
> [!NOTE]
>  如果 Windows Vista 具有顯示設定為使用 Windows XP 顯示驅動程式模型 (XDDM)，在介面一定會複製透過軟體，不論設定為何。 設定適當的設定和視訊卡，您會在 Windows Vista 上看到更佳的效能，當您使用 WDDM，因為介面的複本會在硬體中執行。  
  
## <a name="best-practices-on-windows-xp"></a>在 Windows XP 上的最佳作法  
 為了達到最佳效能，在 Windows XP 中，它會使用 Windows XP 顯示驅動程式模型 (XDDM)，建立一個可鎖定的介面，會正確運作時`IDirect3DSurface9::GetDC`呼叫方法。 就內部而言，`BitBlt`在硬體裝置間傳輸介面的方法。 `GetDC`方法永遠都可運作 XRGB 介面上。 不過，如果用戶端電腦執行 Windows XP SP3 或 SP2，而且用戶端也會有分層視窗功能的 hotfix，則這個方法僅適用於 ARGB 表面。 視訊卡必須支援`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`驅動程式功能。  
  
 16 位元桌面顯示深度可以大幅降低效能。 建議使用 32 位元桌面。  
  
 如果您正在開發適用於 Windows Vista 和 Windows XP，測試 Windows XP 上的效能。 在 Windows XP 上的 mimo rozsah video paměti 執行是一項考量。 颾魤 ㄛ<xref:System.Windows.Interop.D3DImage>在 Windows XP 上使用更多視訊記憶體和頻寬也比 Windows Vista WDDM，因為需要額外的視訊記憶體複本。 因此，您可以預期會比在 Windows Vista 上的 Windows xp 更糟的是相同的視訊硬體的效能。  
  
> [!NOTE]
>  XDDM 是適用於 Windows XP 和 Windows Vista;不過，WDDM 是僅適用於 Windows Vista。  
  
## <a name="general-best-practices"></a>一般最佳作法  
 當您建立裝置時，使用`D3DCREATE_MULTITHREADED`建立旗標。 這會降低效能，但 WPF 呈現系統此裝置上呼叫方法，從另一個執行緒。 請務必正確地遵循鎖定的通訊協定，讓任何兩個執行緒同時存取裝置。  
  
 如果 WPF managed 執行緒上執行您的轉譯，則強烈建議您建立與裝置`D3DCREATE_FPU_PRESERVE`建立旗標。 如果沒有此設定，D3D 轉譯可以減少 WPF 雙精確度運算的精確度，並造成轉譯問題。  
  
 並排<xref:System.Windows.Interop.D3DImage>很快速，除非您圖格的非 pow2 介面，而不需要硬體支援，或您並排<xref:System.Windows.Media.DrawingBrush>或是<xref:System.Windows.Media.VisualBrush>包含<xref:System.Windows.Interop.D3DImage>。  
  
## <a name="best-practices-for-multi-monitor-displays"></a>多重監視器的顯示畫面的最佳作法  
 如果您使用的有多個監視器的電腦，您應該遵循先前所述的最佳作法。 另外還有多監視器組態的一些額外的效能考量。  
  
 當您建立背景緩衝區時，建立特定裝置和配接器，但 WPF 可能會顯示任何配接器為前景緩衝區。 複製到更新前緩衝的介面卡可以是非常耗費資源。 在已設定為搭配多個視訊卡與使用 WDDM 的 Windows Vista 上`IDirect3DDevice9Ex`裝置，前景緩衝區是否位於不同的介面卡，但仍然相同的視訊卡上，沒有任何效能產生負面影響。 不過，在 Windows XP 和具有多個視訊卡 XDDM，沒有顯著的效能負面影響時前景緩衝區會顯示在不同的介面卡比背景緩衝區。 如需詳細資訊，請參閱 < [WPF 和 Direct3D9 互通](wpf-and-direct3d9-interoperation.md)。  
  
## <a name="performance-summary"></a>效能摘要  
 下表做為作業系統、 像素格式和介面的前景緩衝區更新的效能。 背景緩衝區與前景緩衝區會假設為相同的介面卡上。 根據配接器組態中，硬體更新是一般速度也比軟體更新。  
  
|介面的像素格式|Windows Vista，WDDM 9Ex|Windows Vista 中的其他組態|Windows XP SP3 或 SP2 與 hotfix|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 （沒有可鎖定）|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT_X8R8G8B8 (lockable)|**硬體更新**|軟體更新|**硬體更新**|**硬體更新**|  
|D3DFMT_A8R8G8B8 （沒有可鎖定）|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT_A8R8G8B8 (lockable)|**硬體更新**|軟體更新|**硬體更新**|軟體更新|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Interop.D3DImage>
- [WPF 和 Direct3D9 互通](wpf-and-direct3d9-interoperation.md)
- [逐步解說：建立裝載在 WPF 中的 Direct3D9 內容](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [逐步解說：在 WPF 中裝載 Direct3D9 內容](walkthrough-hosting-direct3d9-content-in-wpf.md)
