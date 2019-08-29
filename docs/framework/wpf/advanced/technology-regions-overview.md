---
title: 技術領域概觀
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: 4f1489065a70065700d2f8ceb974e66ecceeebd0
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133806"
---
# <a name="technology-regions-overview"></a>技術領域概觀
如果應用程式中使用了多種展示技術 (例如 WPF、Win32 或 DirectX)，它們就必須在通用的最上層視窗中共用轉譯區域。 本主題所描述的問題可能會影響您 WPF 交互操作應用程式的展示與輸入。  
  
## <a name="regions"></a>區域  
 您可以在最上層視窗中，將下列作業概念化：每個由交互操作應用程式的技術之一所組成的 HWND 都擁有自己的區域 (亦稱為「空間」)。 視窗內的每個像素只能屬於一個 HWND，其會構成該 HWND 的區域 (嚴格說來，如果有多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND，就會有一個以上的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 區域，但基於本討論的目的，您可以假設只有一個)。 區域意謂在應用程式存留期間，嘗試以高於該像素的方式來轉譯的所有層級或其他視窗都必須屬於相同轉譯層技術的一部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]嘗試轉譯[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]圖元會導致不想要的結果, 而且不允許透過交互操作 api 來執行。  
  
### <a name="region-examples"></a>區域範例  
 下圖顯示混合[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]、DirectX 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的應用程式。 每一種技術都會使用一組自己個別的非重疊像素，因此不會產生區域問題。  
  
 ![混合 Win32、DirectX 和 WPF 的應用程式範例。](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 假設此應用程式會使用滑鼠指標位置來建立動畫，此動畫會嘗試透過這三個區域的任一個來轉譯。 無論哪一個技術負責動畫本身，該技術都可能違反其他兩個區域。 下圖顯示嘗試透過 Win32 區域來轉譯 WPF 圓形。  
  
 ![嘗試在 Win32 區域上呈現 WPF 圓形。](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 另一項違反是，如果您嘗試在不同技術之間使用透明度/Alpha 透明混色。  在下圖中, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]方塊[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]違反和 DirectX 區域。 由於該方塊中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的圖元是半透明的, 因此必須由 DirectX 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]共同擁有, 這是不可能的。  因此，這是另一項違反且無法建置。  
  
 ![顯示 WPF 方塊違反 Win32 和 DirectX 區域的圖表。](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 前三個範例使用了矩形區域，但可能會有不同的圖形。  例如，區域可以有一個洞。 下圖顯示[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]具有矩形孔的區域, 這是與 DirectX 區域結合的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]大小。  
  
 ![顯示具有矩形孔之 Win32 區域的圖表。](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 區域不一定是矩形，也可以是 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (區域) 所描述的任何圖形。  
  
 ![顯示非矩形區域的圖表。](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>透明度和最上層視窗  
 事實上，只有 Windows 中的視窗管理員才能處理 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND。 因此, 每[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]個<xref:System.Windows.Window>都是 HWND。 <xref:System.Windows.Window> Hwnd 必須遵守任何 HWND 的一般規則。 在該 HWND 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 程式碼可以執行整體[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] api 支援的任何工作。 但與桌面上的其他 HWND 互動時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 必須遵守 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 處理和轉譯規則。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] api 支援非矩形視窗-非矩形視窗的 hrgn, 以及每個圖元 Alpha 的分層視窗。  
  
 不支援常數的 Alpha 和色鍵。  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 分層視窗功能會因平台而異。  
  
 分層視窗可讓整個視窗呈現半透明狀態，方法是指定要套用至視窗中每個像素的 Alpha 值  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 實際上支援每個像素的 Alpha，但這很難在實際程式中使用，因為在此模式中，您可能需要自行繪製任何子系 HWND，包括對話方塊和下拉式清單)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援 Hrgn;不過, 沒有適用于此功能的受控 Api。 您可以使用平台叫用和<xref:System.Windows.Interop.HwndSource>來呼叫相關[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]的 api。 如需詳細資訊，請參閱[從 Managed 程式碼呼叫原生函式](/cpp/dotnet/calling-native-functions-from-managed-code)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 分層視窗在不同作業系統上有不同的功能。 這是因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會使用 DirectX 來轉譯, 而分層視窗主要是針對 GDI 轉譯 (而非 DirectX 轉譯) 所設計。  
  
- WPF 支援硬體加速分層視窗。  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不支援透明色鍵，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 無法保證可確實呈現您要求的色彩，特別當轉譯是透過硬體加速時。  
  
## <a name="see-also"></a>另請參閱

- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [逐步解說：在 Win32 中裝載 WPF 時鐘](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [在 WPF 中裝載 Win32 內容](hosting-win32-content-in-wpf.md)
