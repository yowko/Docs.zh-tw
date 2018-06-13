---
title: WPF 中的程式碼後置和 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 09d4f010ca53c5e3d2d9dede172e7ae2102261b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541544"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF 中的程式碼後置和 XAML
<a name="introduction"></a> 程式碼後置是用來描述與標記定義的物件，聯結的程式碼的詞彙時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面是標記編譯。 本主題描述程式碼後置的需求，以及程式碼中的替代的內嵌程式碼機制[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 此主題包括下列章節：  
  
-   [必要條件](#Prerequisites)  
  
-   [程式碼後置和 XAML 語言](#codebehind_and_the_xaml_language)  
  
-   [程式碼後置、 事件處理常式，並在 WPF 中的部分類別需求](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x： 程式碼](#x_Code)  
  
-   [內嵌程式碼的限制](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已閱讀[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)和具備一些基本知識的[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]與物件導向程式設計。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>程式碼後置和 XAML 語言  
 XAML 語言包含語言層級功能，使其可將程式碼檔案與標記檔案，從標記檔案端產生關聯。 具體而言，XAML 語言定義的語言功能[X:class 指示詞](../../../../docs/framework/xaml-services/x-class-directive.md)， [X:subclass 指示詞](../../../../docs/framework/xaml-services/x-subclass-directive.md)，和[X:classmodifier 指示詞](../../../../docs/framework/xaml-services/x-classmodifier-directive.md)。 完全方式應該產生程式碼，以及如何將整合標記和程式碼，不是為 XAML 語言的指定部分。 再由架構，例如 WPF 來判斷將整合程式碼的方式、 如何使用 XAML 應用程式和程式設計模型，以及組建中的動作或其他支援的所有這需要。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>程式碼後置、 事件處理常式，並在 WPF 中的部分類別需求  
  
-   部分類別必須衍生自支援的根項目類型。  
  
-   請注意下標記編譯建置動作的預設行為，您可以將衍生空白部分類別定義中的程式碼後置端上。 已編譯的結果會假設頁面根支援類型，作為部分類別中，為基礎，即使未指定。 不過，依賴此行為並不是最佳作法。  
  
-   您撰寫程式碼後置中的事件處理常式必須是執行個體方法，而且不可為靜態方法。 這些方法必須由所識別的 CLR 命名空間內的部分類別定義`x:Class`。 您無法限定名稱的事件處理常式，以指示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器尋找事件連接不同的類別範圍中的事件處理常式。  
  
-   處理常式必須符合在支援類型系統中的適當事件的委派。  
  
-   Microsoft Visual Basic 語言的具體來說，您可以使用特定語言`Handles`關鍵字來關聯執行個體，以及事件處理常式宣告，而不是附加與中屬性的處理常式中的處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 不過，這項技術還是有一些限制因為`Handles`關鍵字不能支援的特定功能的所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統，例如特定路由事件的案例，或附加事件。 如需詳細資訊，請參閱[Visual Basic 和 WPF 的事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x： 程式碼  
 [X:code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)指示詞的項目中定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 `x:Code`指示詞項目可以包含內嵌程式碼。 內嵌定義的程式碼可以與互動[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]相同頁面上。 下列範例說明內嵌 C# 程式碼。 請注意，程式碼位於`x:Code`項目和程式碼，必須以括住`<CDATA[`...`]]>`來逸出的內容[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]，如此[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器 (解譯 [[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]結構描述或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]結構描述) 不會嘗試解譯內容常值做為[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>內嵌程式碼的限制  
 您應該考慮避免或限制的內嵌程式碼使用。 架構和程式碼撰寫原理，維護的區隔標記和程式碼後置會保留的設計工具和開發人員角色更多相異。 在更多技術層級，您為內嵌程式碼撰寫的程式碼可以是很冗長，因此若要撰寫，因為永遠寫入至[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]產生部分類別，且只能使用預設 XML 命名空間對應。 因為您無法將`using`陳述式，您必須完整限定的許多[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]您進行的呼叫。 預設值[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]對應包含大部分但非全部[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]中出現的命名空間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件; 您必須完整限定型別和成員包含在其他的 CLR 命名空間內的呼叫。 您也不能超過的部分類別的任何項目中定義內嵌程式碼，且您參考的所有使用者程式碼實體都必須是成員或產生的部分類別中的變數。 其他語言特定程式設計功能，例如巨集或`#ifdef`針對全域變數或建置變數，也會不提供。 如需詳細資訊，請參閱[X:code 內建 XAML 類型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code 內建 XAML 類型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
