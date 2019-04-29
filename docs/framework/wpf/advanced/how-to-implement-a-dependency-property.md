---
title: HOW TO：實作相依性屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757452"
---
# <a name="how-to-implement-a-dependency-property"></a>HOW TO：實作相依性屬性
此範例示範如何備份[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]屬性與<xref:System.Windows.DependencyProperty>欄位，進而定義相依性屬性。 如果您定義自己的屬性，並想要它們支援 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的許多層面 (包括樣式、資料繫結、繼承、動畫和預設值)，則應該將它們實作為相依性屬性。  
  
## <a name="example"></a>範例  
 下列範例會先註冊相依性屬性呼叫<xref:System.Windows.DependencyProperty.Register%2A>方法。 您用來儲存名稱，而且必須是相依性屬性特性的識別碼欄位名稱<xref:System.Windows.DependencyProperty.Name%2A>您選擇的相依性屬性的一部分<xref:System.Windows.DependencyProperty.Register%2A>呼叫中，常值字串附加`Property`。 比方說，如果您註冊的相依性屬性<xref:System.Windows.DependencyProperty.Name%2A>的`Location`，然後您定義的相依性屬性識別碼欄位必須命名為`LocationProperty`。  
  
 在此範例中，相依性屬性的名稱及其[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]存取子是`State`; 的識別項欄位是`StateProperty`; 屬性的型別是<xref:System.Boolean>; 而註冊相依性屬性的類型是`MyStateControl`。  
  
 如果您無法遵循這個命名模式，則設計工具不一定會正確地報告您的屬性，而且屬性系統樣式應用程式的某些方面可能無法如預期運作。  
  
 您也可以指定相依性屬性的預設中繼資料。 此範例會將 `State` 相依性屬性的預設值註冊為 `false`。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 如需相依性屬性實作方式和原因的詳細資訊，而不是支援 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性與私用欄位的詳細資訊，請參閱[相依性屬性概觀](dependency-properties-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [HOW-TO 主題](properties-how-to-topics.md)
