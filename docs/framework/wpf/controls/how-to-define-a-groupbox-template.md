---
title: 如何：定義 GroupBox 範本
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: ed66d51e87a25f74e646d0d535ac9e4ee9c8a056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-groupbox-template"></a>如何：定義 GroupBox 範本
這個範例示範如何建立的範本<xref:System.Windows.Controls.GroupBox>控制項。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Controls.GroupBox>使用控制項範本<xref:System.Windows.Controls.Grid>版面配置控制項。 範本使用<xref:System.Windows.Controls.BorderGapMaskConverter>來定義的框線<xref:System.Windows.Controls.GroupBox>以便框線並不會遮住<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>內容。  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.GroupBox>  
 [GroupBox How-to 主題](http://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
