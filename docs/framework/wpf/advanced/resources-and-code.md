---
title: 資源和程式碼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys [WPF], using objects as
- resources [WPF], accessing from procedural code
- procedural code [WPF], creating resources with
- procedural code [WPF], accessing resources from
- resources [WPF], creating with procedural code
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
ms.openlocfilehash: 12f9acccfc23364795cd18ef1da2ced5b442c6f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367972"
---
# <a name="resources-and-code"></a>資源和程式碼
本概觀將著重於如何使用程式碼 (而非 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 語法) 來存取 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資源。 如需從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法觀點來了解一般資源使用方式和資源的詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。  
  
  
  
<a name="accessing"></a>   
## <a name="accessing-resources-from-code"></a>從程式碼存取資源  
 如果您利用程式碼要求資源，則用來識別資源是否要透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 所定義之資源的索引鍵，也可用來擷取特定的資源。 從程式碼擷取資源的最簡單方式是呼叫其中一個<xref:System.Windows.FrameworkElement.FindResource%2A>或<xref:System.Windows.FrameworkElement.TryFindResource%2A>從應用程式中的架構層級物件的方法。 這些方法之間的行為差異在於，找不到要求的索引鍵時會發生什麼情況。 <xref:System.Windows.FrameworkElement.FindResource%2A> 引發例外狀況;<xref:System.Windows.FrameworkElement.TryFindResource%2A>將不會引發例外狀況，但傳回`null`。 每個方法都會取得資源索引鍵做為輸入參數，並傳回弱類型的物件。 一般而言，資源索引鍵是一個字串，但偶而會有非字串的使用方式；如需詳細資訊，請參閱[使用物件做為索引鍵](#objectaskey)一節。 通常您會將傳回的物件轉型為您在要求資源時設定之屬性所需的類型。 程式碼資源解析的查閱邏輯會與動態資源參考 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 案例相同。 資源的搜尋會從呼叫元素開始，然後繼續進行邏輯樹狀結構中後續的父元素。 查閱會視需要繼續尋找應用程式資源、主題和系統資源。 資源的程式碼要求將實際負責處理資源字典中的執行階段變更，這些可能是在從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入該資源字典之後所進行的變更，同時也會負責處理即時系統資源變更。  
  
 以下是簡短的程式碼範例中，依索引鍵中尋找的資源，並使用傳回的值來設定屬性，實作為<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式。  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 指派資源參考的替代方法是<xref:System.Windows.FrameworkElement.SetResourceReference%2A>。 這個方法會採用兩個參數︰資源的索引鍵，以及特殊相依性屬性的識別碼，該屬性會出現在應指派資源值的元素執行個體上。 在功能上，這個方法是一樣的，而且優點是不需要對傳回值進行任何轉型。  
  
 以程式設計方式存取資源的另一個方式可存取的內容<xref:System.Windows.FrameworkElement.Resources%2A>做為字典的屬性。 同樣地，存取這個屬性所包含的字典包括，您如何將新資源新增至現有的集合、檢查以查看是否已經在集合中取得指定的索引鍵名稱，以及其他的字典/集合作業。 如果您正在撰寫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]完全以程式碼的應用程式，您也可以建立整個集合中的程式碼，將索引鍵指派給它，然後指派要完成的集合<xref:System.Windows.FrameworkElement.Resources%2A>建立元素的屬性。 下一節將說明此動作。  
  
 您可以在任何給定索引<xref:System.Windows.FrameworkElement.Resources%2A>集合，使用特定的索引鍵做為索引，但您應該注意，存取這種方式中的資源時，不符合資源解析的標準執行階段規則。 您只能存取該特定的集合。 如果在要求的索引鍵上在找不到任何有效的物件，資源查閱就不會將範圍周遊至根項目或應用程式。 不過，此方法在某些情況下恰巧具有效能優點，因為索引鍵的搜尋範圍更加限定。 請參閱<xref:System.Windows.ResourceDictionary>類別，如需有關如何直接使用的資源字典的詳細資訊。  
  
<a name="creating"></a>   
## <a name="creating-resources-with-code"></a>使用程式碼建立資源  
 如果您想要使用程式碼來建立整個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，也可以使用程式碼，在該應用程式中建立任何資源。 若要這麼做，請建立新<xref:System.Windows.ResourceDictionary>執行個體，然後再將所有資源都新增至使用後續呼叫的字典<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>。 然後，使用<xref:System.Windows.ResourceDictionary>以此方式建立設定<xref:System.Windows.FrameworkElement.Resources%2A>出現在頁面範圍的項目上的屬性或<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>。 您也可以保留<xref:System.Windows.ResourceDictionary>做為獨立物件，而不將它新增至項目。 不過，如果這麼做，您必須依項目索引鍵存取其中的資源，就如同它是泛型字典。 A <xref:System.Windows.ResourceDictionary> ，將不會附加至元素`Resources`屬性不會存在為元素樹狀結構的一部分，並不有可用的查閱序列中的任何範圍<xref:System.Windows.FrameworkElement.FindResource%2A>及相關方法。  
  
<a name="objectaskey"></a>   
## <a name="using-objects-as-keys"></a>使用物件做為索引鍵  
 大多數的資源使用方式會將資源的索引鍵設定為字串。 不過，各種 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能刻意不使用字串類型來指定索引鍵，而是此參數就是一個物件。 讓物件將資源當成索引鍵的功能，是透過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 樣式和佈景主題支援來使用。 在成為非樣式控制項的預設樣式的佈景主題樣式每個特定<xref:System.Type>它們應套用至的控制項。 依類型做為索引鍵，會提供可靠的查閱機制，在每個控制項類型的預設執行個體上運作，而且類型可以依反射來偵測，並用於設定衍生類型的樣式，即使衍生的類型不具預設樣式也一樣。 您可以指定<xref:System.Type>中所定義之資源的索引鍵[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]利用[X:type 標記延伸](../../xaml-services/x-type-markup-extension.md)。 還有類似的延伸可供支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能的其他非字串索引鍵使用方式使用，例如 [ComponentResourceKey 標記延伸](componentresourcekey-markup-extension.md)。  
  
## <a name="see-also"></a>另請參閱
- [XAML 資源](xaml-resources.md)
- [樣式設定和範本化](../controls/styling-and-templating.md)
