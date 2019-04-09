---
title: 初始化物件樹狀結構以外的物件項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- logical tree [WPF]
- visual tree [WPF]
- elements [WPF], initializing
- initializing elements [WPF]
ms.assetid: 7b8dfc9b-46ac-4ce8-b7bb-035734d688b7
ms.openlocfilehash: 6f3c8611b83977431038573eb1c5c880acbefdc4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108962"
---
# <a name="initialization-for-object-elements-not-in-an-object-tree"></a>初始化物件樹狀結構以外的物件項目
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 初始化的某些層面會延後處理，因為這些處理通常需要將該項目連接到邏輯樹狀結構或視覺化樹狀結構。 本主題說明為了初始化未連接到任一樹狀結構的項目所需的步驟。  

## <a name="elements-and-the-logical-tree"></a>項目和邏輯樹狀結構  
 當您在程式碼中建立 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的執行個體時，您應該注意到 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的物件初始化有幾個層面刻意不屬於呼叫類別建構函式時所執行的程式碼。 特別是控制項類別，該控制項的視覺表示大部分不是由建構函式定義， 而是由控制項的範本來定義視覺表示。 範本可能來自各種不同的來源，但最常會從佈景主題樣式取得範本。 範本實際上是晚期繫結；必須等到相關控制項可以開始配置之後，才能將所需的範本附加至該控制項。 此外，控制項必須等到附加至連接到根目錄之呈現介面的邏輯樹狀結構之後，才能開始配置。 根層級項目會依照邏輯樹狀結構中的定義，來啟始其所有子項目的呈現。  
  
 視覺化樹狀結構也會參與此程序。 透過範本成為視覺化樹狀結構一部分的項目，也必須等到連接之後才能完全具現化。  
  
 此行為的結果是，依賴某個項目之完整視覺特性的特定作業需要額外的步驟。 其中一個範例是您嘗試取得某個類別的視覺特性，而此類別已建構但尚未附加至樹狀結構。 比方說，如果您想要呼叫<xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A>上<xref:System.Windows.Media.Imaging.RenderTargetBitmap>您傳遞的視覺效果，而且 未連接的樹狀結構的項目才會完成額外的初始化步驟，該項目會以視覺化方式完成。  
  
### <a name="using-begininit-and-endinit-to-initialize-the-element"></a>使用 BeginInit 和 EndInit 來初始化項目  
 中的各種類別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作<xref:System.ComponentModel.ISupportInitialize>介面。 您使用<xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>和<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>表示區域，以在程式碼中包含初始化步驟 （例如設定屬性的值影響呈現的） 介面的方法。 之後<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>呼叫的順序，請配置系統可以處理項目，並開始尋找隱含樣式。  
  
 如果項目會設定屬性，在<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別，則您可以呼叫的類別版本<xref:System.Windows.FrameworkElement.BeginInit%2A>並<xref:System.Windows.FrameworkElement.EndInit%2A>而不是轉換至<xref:System.ComponentModel.ISupportInitialize>。  
  
### <a name="sample-code"></a>程式碼範例  
 下列範例會使用轉譯的主控台應用程式的範例程式碼[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]和<xref:System.Windows.Markup.XamlReader.Load%28System.IO.Stream%29?displayProperty=nameWithType>鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，以說明的位置正確<xref:System.Windows.FrameworkElement.BeginInit%2A>並<xref:System.Windows.FrameworkElement.EndInit%2A>周圍其他[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]呼叫可調整影響呈現的屬性。  
  
 此範例只會說明 main 函式。 `Rasterize` 和 `Save` 函式 (未顯示) 是負責影像處理和 IO 的公用程式函式。  
  
 [!code-csharp[InitializeElements#Main](~/samples/snippets/csharp/VS_Snippets_Wpf/InitializeElements/CSharp/initializeelements.cs#main)]
 [!code-vb[InitializeElements#Main](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InitializeElements/VisualBasic/initializeelements.vb#main)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的樹狀結構](trees-in-wpf.md)
- [WPF 圖形轉譯概觀](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
