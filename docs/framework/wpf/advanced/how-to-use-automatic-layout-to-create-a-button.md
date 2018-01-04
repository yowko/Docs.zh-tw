---
title: "如何：使用自動配置建立按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c642e6491722e9bfe35337d066e3870f5a70f38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>如何：使用自動配置建立按鈕
此範例說明如何使用自動版面配置方法，以建立可當地語系化之應用程式中的按鈕。  
  
 當地語系化的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]是耗時的程序。 當地語系化人員除了翻譯文字以外，通常還需要調整項目的大小並重新置放項目。 在過去每種語言，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]需要調整的已調整。 現在與功能的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]您可以設計會減少需要調整的項目。 撰寫應用程式可以更輕鬆地調整大小和重新定位方法會呼叫`automatic layout`。  
  
 下面兩個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會建立具現化的按鈕; 一個用於英文字，另一個西班牙文字的應用程式。 請注意，除了文字之外，其餘程式碼都相同；按鈕會配合文字進行調整。  
  
## <a name="example"></a>範例  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![按鈕相同，但文字的語言不同](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
可自動調整大小的按鈕  
  
## <a name="see-also"></a>請參閱  
 [使用自動配置概觀](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [針對自動版面配置使用方格](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
