---
title: 如何：定義 GroupBox 範本
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: a47ce896be4d1c38147584dd80b1bc841737d526
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130652"
---
# <a name="how-to-define-a-groupbox-template"></a>如何：定義 GroupBox 範本
此範例示範如何建立範本<xref:System.Windows.Controls.GroupBox>控制項。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Controls.GroupBox>使用的控制項範本<xref:System.Windows.Controls.Grid>版面配置控制項。 此範本會使用<xref:System.Windows.Controls.BorderGapMaskConverter>定義的框線<xref:System.Windows.Controls.GroupBox>以便框線不會不會遮住<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>內容。  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.GroupBox>  
 [GroupBox how to 主題](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
