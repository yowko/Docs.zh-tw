---
title: 應用程式效能規劃
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: c8e763686b30ca9c8e1dc5a7f6234d77201e4cba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="planning-for-application-performance"></a>應用程式效能規劃
達成您的效能目標的成功取決於您開發效能策略的程度。 規劃是在開發任何產品的第一個階段。 本主題說明一些非常簡單的規則開發良好效能策略。  
  
## <a name="think-in-terms-of-scenarios"></a>將案例視為  
 案例可協助您專注於應用程式的重要元件。 案例通常衍生自您的客戶，以及競爭的產品。 請務必研究您的客戶，並找出真正令他們高興有關您的產品與競爭對手產品。 客戶的意見反應可協助您判斷您的應用程式的主要案例。 比方說，如果您要設計的元件，將使用在啟動時，可能是應用程式啟動時，一次，呼叫該元件。 啟動時間會變成主要案例。 重要案例的其他範例可能會想要的畫面播放速率的動畫順序，或工作集的應用程式允許的最大值。  
  
## <a name="define-goals"></a>定義目標  
 目標幫助您判斷應用程式是否正在執行更快或較慢。 您應該定義所有案例的目標。 您定義的所有效能目標應該都根據客戶的期望。 可能很難設定效能目標及早在開發應用程式循環，仍有許多未解決的問題。 不過，最好是設定初始的目標及晚於以沒有目標完全修改它。  
  
## <a name="understand-your-platform"></a>了解您的平台  
 請務必測量、 調查、 應用程式開發週期精簡/修正。 從開始到結束的開發週期中，您需要測量您的應用程式效能可靠且穩定的環境中。 您應該避免因為外部因素所造成的變化性。 比方說，當測試效能時，您應該停用防毒程式或任何自動更新，例如 SMS，為了避免影響效能測試結果。 一旦您擁有以測量應用程式的效能，您需要識別將會導致最大的增強功能的變更。 一旦您修改您的應用程式，請重新執行測試。  
  
## <a name="make-performance-tuning-an-iterative-process"></a>進行效能微調反覆的程序  
 您應該知道每項功能，您將使用的相對的成本。 例如，使用 Microsoft.NET Framework 中反映通常是效能耗用大量運算資源，所以您會想要使用明智。 這不表示若要避免使用反映，只有，您應該要特別注意應用程式的效能需求與您所使用的功能的效能需求之間取得平衡。  
  
## <a name="build-towards-graphical-richness"></a>建置豐富的圖形  
 建立達到擴充方法的關鍵技術[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的效能是很豐富，圖形化和複雜度而建立。 一律使用最少的效能密集的資源來達成目標案例以啟動。 一旦您達成這些目標，而使用多個效能大量功能，您的案例目標永遠處於記住建立圖形的豐富性。 請記住，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是一個非常豐富的平台，並提供非常豐富的圖形功能。 使用不需考慮的效能密集功能會對整體應用程式效能造成負面影響。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 藉由使用普遍自訂其外觀，而不改變其控制行為的控制項是原本就是可延伸。 您可以藉由運用樣式、 資料範本和控制項 範本，建立並以累加方式發展可自訂[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，會調整到您的效能需求。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [版面配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
