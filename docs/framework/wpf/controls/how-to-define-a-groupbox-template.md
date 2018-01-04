---
title: "如何：定義 GroupBox 範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a63a79b298a45b4efd6d1cbd439d208744358ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-groupbox-template"></a>如何：定義 GroupBox 範本
這個範例示範如何建立的範本<xref:System.Windows.Controls.GroupBox>控制項。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Controls.GroupBox>使用控制項範本<xref:System.Windows.Controls.Grid>版面配置控制項。 範本使用<xref:System.Windows.Controls.BorderGapMaskConverter>來定義的框線<xref:System.Windows.Controls.GroupBox>以便框線並不會遮住<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>內容。  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.GroupBox>  
 [GroupBox How-to 主題](http://msdn.microsoft.com/en-us/7692e155-a4c6-428c-b7e0-64b3740daca7)
