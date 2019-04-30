---
title: HOW TO：使用系統字型索引鍵
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: e924f4c14d98380d9f4c0defe27d9f98c3293114
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001607"
---
# <a name="how-to-use-system-fonts-keys"></a>HOW TO：使用系統字型索引鍵
系統資源會將數個系統度量資訊公開為資源，協助開發人員建立與系統設定一致的視覺效果。 <xref:System.Windows.SystemFonts> 是包含系統字型值以及繫結至值的系統字型資源的類別，例如<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>和<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>。  
  
 系統字型度量資訊可以當成靜態或動態資源使用。 如果您想要在應用程式執行時自動更新字型度量資訊，請使用動態資源；否則請使用靜態資源。  
  
> [!NOTE]
>  動態資源具有關鍵字*金鑰*附加至屬性名稱。  
  
 下列範例示範如何存取及使用系統字型動態資源，以設定或自訂按鈕的樣式。 這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會建立將指派的按鈕樣式<xref:System.Windows.SystemFonts>至按鈕的值。  
  
## <a name="example"></a>範例  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>另請參閱

- [使用系統筆刷繪製區域](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [使用 SystemParameters](how-to-use-systemparameters.md)
- [使用 SystemFonts](how-to-use-systemfonts.md)
