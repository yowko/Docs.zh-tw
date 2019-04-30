---
title: 應用程式效能規劃
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: 70dda68112d47d3e5a0609a5df7696920477c698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032860"
---
# <a name="planning-for-application-performance"></a>應用程式效能規劃
達成效能目標的成功取決於您開發效能策略的程度。 規劃是在開發任何產品的第一個階段。 本主題描述一些非常簡單的規則開發良好的效能策略。  
  
## <a name="think-in-terms-of-scenarios"></a>思考案例  
 案例可協助您專注於您的應用程式的重要元件。 案例通常衍生自您的客戶，以及競爭對手的產品。 請務必研究您的客戶，並找出其實兩者有何期待您的產品及競爭對手的產品。 您的客戶意見反應可協助您判斷您的應用程式的主要案例。 比方說，如果您要設計的元件，將使用在啟動時，很可能在應用程式啟動時，一次，呼叫該元件。 啟動時間會變成您重要的案例。 主要案例的其他範例可能是理想畫面播放速率動畫序列 (sequence)，或工作集的應用程式允許的最大值。  
  
## <a name="define-goals"></a>定義目標  
 目標可協助您判斷應用程式是否正在執行快或更慢。 您應該為所有案例的都定義目標。 您所定義的所有效能目標應該都根據您客戶的期望。 它可能難以設定效能目標，早在應用程式開發循環，仍有許多未解決的問題。 不過，最好是設定初始目標和晚到沒有目標完全地修正。  
  
## <a name="understand-your-platform"></a>了解您的平台  
 請務必測量、 調查、 應用程式開發週期改善/修正。 從開始到開發週期結尾時，您需要測量您的應用程式可靠、 穩定的環境中的效能。 您應該避免因為外部因素所造成的變化性。 比方說，當測試效能時，您應該停用防毒軟體或 SMS 等任何自動更新，以避免影響效能測試結果。 一旦您已測量您的應用程式效能，您需要識別將會導致最大的改進功能的變更。 一旦您已修改您的應用程式，請重新執行測試。  
  
## <a name="make-performance-tuning-an-iterative-process"></a>進行效能微調反覆的程序  
 您應該知道每項功能，您將使用的相對的成本。 比方說，使用 Microsoft.NET Framework 中通常是反映的效能密集大量運算資源，因此您會想要請斟酌使用。 這不表示若要避免使用反映，只有，您應該要特別注意您的應用程式效能需求，與您所使用的功能的效能需求之間取得平衡。  
  
## <a name="build-towards-graphical-richness"></a>建置豐富的圖形  
 一項重要技術來建立可調整的方法，達到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式效能是以圖形化的豐富功能和複雜度而建立。 開頭一律使用最少的效能密集的資源以達到您案例的目標。 一旦您達成這些目標，而使用多個耗損效能的功能，一律將您案例的目標並記住建立圖形的豐富功能。 請記住，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是一個非常豐富的平台，並提供非常豐富的圖形功能。 使用不需考慮的效能密集功能會對整體應用程式效能造成負面影響。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項是繼承可擴充讓普遍自訂其外觀，而不改變其控制項行為。 藉由運用樣式、 資料範本和控制項範本，您可以建立，並以累加方式發展可自訂[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，適應您的效能需求。  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
