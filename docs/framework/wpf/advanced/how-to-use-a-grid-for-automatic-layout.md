---
title: "如何：針對自動配置使用格線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbd8bd7e36b7b773837b839e77ec88a8e7c8f0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>如何：針對自動配置使用格線
此範例說明如何使用自動版面配置方法中的格線，以建立當地語系化的應用程式。  
  
 當地語系化的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]是耗時的程序。 當地語系化人員除了翻譯文字以外，通常還需要重新調整項目的大小並重新定位。 在過去每種語言，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]需要調整的已調整。 現在與功能的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]您可以設計會減少需要調整的項目。 撰寫應用程式可以更輕鬆地重新調整大小和重新定位方法會呼叫`auto layout`。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例示範如何使用方格來將部分按鈕和文字位置。 請注意，儲存格的寬度與高度設為`Auto`; 的資料格按鈕的影像，因此調整以符合影像。 因為<xref:System.Windows.Controls.Grid>項目可以調整其內容將非常有用設計可以當地語系化的應用程式進行自動配置方法。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用格線。  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![格線範例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Grid  
  
## <a name="see-also"></a>請參閱  
 [使用自動配置概觀](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [使用自動版面配置建立按鈕](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
