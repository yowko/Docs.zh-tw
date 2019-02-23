---
title: HOW TO：定義 GroupBox 範本
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: 6294a52d5914b52d191b564330f904e6a865c283
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745194"
---
# <a name="how-to-define-a-groupbox-template"></a>HOW TO：定義 GroupBox 範本
此範例示範如何建立範本<xref:System.Windows.Controls.GroupBox>控制項。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Controls.GroupBox>使用的控制項範本<xref:System.Windows.Controls.Grid>版面配置控制項。 此範本會使用<xref:System.Windows.Controls.BorderGapMaskConverter>定義的框線<xref:System.Windows.Controls.GroupBox>以便框線不會不會遮住<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>內容。  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.GroupBox>
- [如何：建立群組方塊](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))
