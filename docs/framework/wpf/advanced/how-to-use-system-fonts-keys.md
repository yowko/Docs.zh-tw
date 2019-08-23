---
title: 作法：使用系統字型索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918391"
---
# <a name="how-to-use-system-fonts-keys"></a>HOW TO：使用系統字型索引鍵
系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemFonts>是一個類別, 其中同時包含系統字型值和系結至值的系統字型資源 (例如和<xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>)。  
  
 系統字型度量資訊可以當成靜態或動態資源使用。 如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源；否則請使用靜態資源。  
  
> [!NOTE]
> 動態資源會在屬性名稱後面附加關鍵字索引*鍵*。  
  
 下列範例示範如何存取及使用系統字型動態資源，以設定或自訂按鈕的樣式。 這個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會建立按鈕樣式, 將<xref:System.Windows.SystemFonts>值指派給按鈕。  
  
## <a name="example"></a>範例  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>另請參閱

- [使用系統筆刷繪製區域](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [使用 SystemParameters](how-to-use-systemparameters.md)
- [使用 SystemFonts](how-to-use-systemfonts.md)
