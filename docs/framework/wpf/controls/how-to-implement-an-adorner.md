---
title: "如何：實作裝飾項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76bceae5b69fad4c217127617309484edcf18108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-adorner"></a>如何：實作裝飾項
此範例會顯示最少的裝飾項的實作。  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 請務必注意，裝飾項並不包括任何繼承的轉譯行為。裝飾項實作者必須負責確定裝飾項轉譯器。   實作轉譯行為的常見方式是覆寫<xref:System.Windows.UIElement.OnRender%2A>方法並使用一或多個<xref:System.Windows.Media.DrawingContext>物件來呈現裝飾項的視覺效果視 （如本範例所示）。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 藉由實作繼承自抽象類別建立的自訂裝飾項<xref:System.Windows.Documents.Adorner>類別。  範例裝飾項只 adorns 角落<xref:System.Windows.UIElement>使用圓形藉由覆寫<xref:System.Windows.UIElement.OnRender%2A>方法。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
