---
title: Direct3D9 和 WPF 互通性的效能考量
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 02a91c1824c5d6374f37b0af66a3308d33210c4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932486"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Direct3D9 和 WPF 互通性的效能考量
您可以使用<xref:System.Windows.Interop.D3DImage>類別來裝載 Direct3D9 內容。 裝載 Direct3D9 內容可能會影響應用程式的效能。 本主題描述在 Windows Presentation Foundation (WPF) 應用程式中裝載 Direct3D9 內容時, 將效能優化的最佳作法。 這些最佳作法包括當您使用<xref:System.Windows.Interop.D3DImage> windows Vista、windows XP 和多監視器顯示器時, 如何使用和最佳作法。  
  
> [!NOTE]
> 如需示範這些最佳做法的程式碼範例, 請參閱[WPF 和 Direct3D9 交互操作](wpf-and-direct3d9-interoperation.md)。  
  
## <a name="use-d3dimage-sparingly"></a>謹慎使用 System.windows.interop.d3dimage> 實作  
 在<xref:System.Windows.Interop.D3DImage>實例中裝載的 Direct3D9 內容不會像在純 Direct3D 應用程式中一樣快速地呈現。 複製介面和清除命令緩衝區可能是昂貴的作業。 當<xref:System.Windows.Interop.D3DImage>實例數目增加時, 就會發生更多清除, 並降低效能。 因此, 您應該謹慎<xref:System.Windows.Interop.D3DImage>使用。  
  
## <a name="best-practices-on-windows-vista"></a>Windows Vista 的最佳作法  
 若要在 windows Vista 上獲得最佳效能, 並將顯示設定為使用 Windows 顯示驅動程式模型 (WDDM), 請在`IDirect3DDevice9Ex`裝置上建立您的 Direct3D9 介面。 這會啟用介面共用。 視訊卡必須支援 Windows Vista `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`上`D3DCAPS2_CANSHARERESOURCE`的和驅動程式功能。 任何其他設定都會導致介面透過軟體複製, 這會大幅降低效能。  
  
> [!NOTE]
> 如果 Windows Vista 的顯示設定為使用 Windows XP 顯示驅動程式模型 (XDDM), 則不論設定為何, 介面一律會透過軟體複製。 有了適當的設定和視訊卡, 當您使用 WDDM 時, 您會在 Windows Vista 上看到較佳的效能, 因為表面複製是在硬體中執行。  
  
## <a name="best-practices-on-windows-xp"></a>Windows XP 上的最佳做法  
 為了在使用 windows xp 顯示驅動程式模型 (XDDM) 的 windows xp 上獲得最佳效能, 請建立可鎖定的`IDirect3DSurface9::GetDC`介面, 以在呼叫方法時正確運作。 就內部而言`BitBlt` , 方法會在硬體中的裝置之間傳輸介面。 `GetDC`方法一律適用于 XRGB 介面。 不過, 如果用戶端電腦執行的是 Windows XP SP3 或 SP2, 而且用戶端也具有多層式視窗功能的修補程式, 則這個方法只適用于 ARGB 表面。 視訊卡必須支援`D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`驅動程式功能。  
  
 16位桌面顯示器深度可以大幅降低效能。 建議使用32位桌面。  
  
 如果您是針對 Windows Vista 和 Windows XP 進行開發, 請在 Windows XP 上測試效能。 Windows XP 上的視訊記憶體即將用盡。 此外, <xref:System.Windows.Interop.D3DImage>在 windows XP 上, 由於需要額外的視訊記憶體複製, 因此使用比 windows Vista WDDM 更多的視訊記憶體和頻寬。 因此, 在 Windows XP 上的效能可能會比在 Windows Vista 上更糟, 適用于相同的影片硬體。  
  
> [!NOTE]
> XDDM 適用于 Windows XP 和 Windows Vista;不過, WDDM 僅適用于 Windows Vista。  
  
## <a name="general-best-practices"></a>一般最佳作法  
 當您建立裝置時, 請使用`D3DCREATE_MULTITHREADED`建立旗標。 這會降低效能, 但是 WPF 轉譯系統會從另一個執行緒呼叫此裝置上的方法。 請務必正確地遵循鎖定通訊協定, 如此一來, 就不會有兩個執行緒同時存取該裝置。  
  
 如果您的轉譯是在 WPF 管理的執行緒上執行, 則強烈建議您使用`D3DCREATE_FPU_PRESERVE`建立旗標來建立裝置。 如果沒有此設定, D3D 轉譯可以降低 WPF 雙精確度運算的精確度, 並引進轉譯問題。  
  
 並排顯示<xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> <xref:System.Windows.Interop.D3DImage>是快速的, 除非您在不支援硬體的情況下磚于非 pow2 介面, 或磚包含的或。 <xref:System.Windows.Interop.D3DImage>  
  
## <a name="best-practices-for-multi-monitor-displays"></a>多監視器顯示器的最佳做法  
 如果您使用的電腦有多個監視器, 您應該遵循先前所述的最佳作法。 多監視器設定也有一些額外的效能考慮。  
  
 當您建立後端緩衝區時, 它會建立在特定的裝置和介面卡上, 但是 WPF 可能會在任何介面卡上顯示前端緩衝區。 跨介面卡複製以更新前端緩衝區可能非常昂貴。 在設定為搭配多張視訊卡和`IDirect3DDevice9Ex`裝置使用 WDDM 的 Windows Vista 上, 如果前端緩衝區位於不同的介面卡上, 但仍然是相同的視訊卡, 則不會影響效能。 不過, 在 Windows XP 和具有多張視訊卡的 XDDM 上, 當前端緩衝區顯示在與背景緩衝區不同的介面卡上時, 會有明顯的效能影響。 如需詳細資訊, 請參閱[WPF 和 Direct3D9 交互操作](wpf-and-direct3d9-interoperation.md)。  
  
## <a name="performance-summary"></a>效能摘要  
 下表顯示前端緩衝區更新的效能, 做為作業系統、像素格式和 surface lockability 的功能。 前端緩衝區和背景緩衝區會假設在相同的介面卡上。 根據介面卡設定, 硬體更新的速度通常會比軟體更新快很多。  
  
|介面像素格式|Windows Vista、WDDM 和9Ex|其他 Windows Vista 設定|Windows XP SP3 或 SP2 (含修補程式)|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (不可鎖定)|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT_X8R8G8B8 (鎖定)|**硬體更新**|軟體更新|**硬體更新**|**硬體更新**|  
|D3DFMT_A8R8G8B8 (不可鎖定)|**硬體更新**|軟體更新|軟體更新|軟體更新|  
|D3DFMT_A8R8G8B8 (鎖定)|**硬體更新**|軟體更新|**硬體更新**|軟體更新|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.D3DImage>
- [WPF 和 Direct3D9 互通](wpf-and-direct3d9-interoperation.md)
- [逐步解說：建立在 WPF 中裝載的 Direct3D9 內容](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [逐步解說：在 WPF 中裝載 Direct3D9 內容](walkthrough-hosting-direct3d9-content-in-wpf.md)
