---
title: "如何：以程式設計方式變更內容的 FlowDirection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>如何：以程式設計方式變更內容的 FlowDirection
此範例示範如何以程式設計方式變更<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性<xref:System.Windows.Controls.FlowDocumentReader>。  
  
## <a name="example"></a>範例  
 兩個<xref:System.Windows.Controls.Button>會建立項目，分別代表的可能值的其中一個<xref:System.Windows.FlowDirection>。 當按一下按鈕時，相關聯的屬性值會套用至內容<xref:System.Windows.Controls.FlowDocumentReader>名為`tf1`。  屬性值也會寫入<xref:System.Windows.Controls.TextBlock>名為`txt1`。  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>範例  
 定義於上方的按鈕按一下動作相關聯的事件會在處理[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]程式碼後置檔案。  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
