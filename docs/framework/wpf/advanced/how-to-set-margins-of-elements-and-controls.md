---
title: 如何：設定項目和控制項的邊界
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f32107074239e9713feaa9e0b9b7e1f89869d111
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>如何：設定項目和控制項的邊界
這個範例說明如何設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性，藉由變更任何現有的屬性值的程式碼後置中的邊界。 <xref:System.Windows.FrameworkElement.Margin%2A>屬性是屬性的<xref:System.Windows.FrameworkElement>基底項目，而且會因此繼承各種控制項和其他項目。  
  
 這個範例以撰寫[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，與程式碼後置檔案，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]參考。 顯示程式碼後置 C# 和 Visual Basic 版本。  
  
## <a name="example"></a>範例  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
