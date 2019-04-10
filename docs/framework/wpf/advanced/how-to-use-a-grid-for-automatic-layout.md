---
title: HOW TO：針對自動版面配置使用格線
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 590ad7292fea572b20ccaa09ce2886724e004a6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227114"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>HOW TO：針對自動版面配置使用格線
此範例說明如何使用自動版面配置方法中的格線，以建立當地語系化的應用程式。  
  
 當地語系化[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]可以是耗時的程序。 當地語系化人員除了翻譯文字以外，通常還需要重新調整項目的大小並重新定位。 在過去每一種語言，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]已調整的需要調整。 現在使用的功能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，您可以設計可降低的需求調整的項目。 在呼叫的方法來撰寫應用程式都可以更輕鬆地重新調整大小和重新置放`auto layout`。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例示範如何使用格線來定位部分按鈕和文字。 請注意，儲存格的寬度與高度設為`Auto`; 因此包含影像的按鈕的資料格會調整，以符合影像大小。 因為<xref:System.Windows.Controls.Grid>項目可以調整它可用來設計可當地語系化的應用程式採用自動版面配置方法時其內容。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用格線。  
  
 [!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![格線範例](./media/glob-grid.png "glob_grid")  
Grid  
  
## <a name="see-also"></a>另請參閱

- [使用自動配置概觀](use-automatic-layout-overview.md)
- [使用自動配置建立按鈕](how-to-use-automatic-layout-to-create-a-button.md)
