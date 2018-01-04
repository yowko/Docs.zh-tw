---
title: "如何：實作相依性屬性"
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
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d63e66b2458fa4ff21a227bdc2898d97e5eb30f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-dependency-property"></a>如何：實作相依性屬性
這個範例示範如何備份[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]屬性<xref:System.Windows.DependencyProperty> 欄位中，進而定義相依性屬性。 如果您定義自己的屬性，並想要它們支援 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的許多層面 (包括樣式、資料繫結、繼承、動畫和預設值)，則應該將它們實作為相依性屬性。  
  
## <a name="example"></a>範例  
 下列範例會先註冊相依性屬性藉由呼叫<xref:System.Windows.DependencyProperty.Register%2A>方法。 您用來儲存名稱，而且必須是特性之相依性屬性的識別項欄位名稱<xref:System.Windows.DependencyProperty.Name%2A>您選擇的相依性屬性的一部分<xref:System.Windows.DependencyProperty.Register%2A>呼叫時，常值字串後面附加上`Property`。 比方說，如果您註冊相依性屬性與<xref:System.Windows.DependencyProperty.Name%2A>的`Location`，您定義的相依性屬性的識別項欄位也必須命名為`LocationProperty`。  
  
 在此範例中，相依性屬性的名稱和其[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]存取子是`State`; 識別項欄位是`StateProperty`; 屬性的型別是<xref:System.Boolean>; 登錄相依性屬性的型別和`MyStateControl`。  
  
 如果您無法遵循這個命名模式，則設計工具不一定會正確地報告您的屬性，而且屬性系統樣式應用程式的某些方面可能無法如預期運作。  
  
 您也可以指定相依性屬性的預設中繼資料。 此範例會將 `State` 相依性屬性的預設值註冊為 `false`。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 如需相依性屬性實作方式和原因的詳細資訊，而不是支援 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性與私用欄位的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
## <a name="see-also"></a>請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
