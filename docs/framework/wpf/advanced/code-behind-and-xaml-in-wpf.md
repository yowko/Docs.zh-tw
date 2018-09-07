---
title: WPF 中的程式碼後置和 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: ee08dc22588264b25d40b3fd818ef9ee1da90319
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085661"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF 中的程式碼後置和 XAML
<a name="introduction"></a> 程式碼後置指的是用來描述與標記定義的物件，聯結的程式碼時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面是進行標記編譯。 本主題描述程式碼後置的需求，以及在程式碼的替代的內嵌程式碼機制[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 此主題包括下列章節：  
  
-   [必要條件](#Prerequisites)  
  
-   [程式碼後置和 XAML 語言](#codebehind_and_the_xaml_language)  
  
-   [程式碼後置、 事件處理常式，並在 WPF 中的部分類別需求](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x： 程式碼](#x_Code)  
  
-   [內嵌程式碼的限制](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已閱讀[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)具備的一些基本知識和[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]和物件導向程式設計。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>程式碼後置和 XAML 語言  
 XAML 語言包含語言層級功能，使您能夠標記檔案，從標記檔端相關聯的程式碼檔案。 具體而言，XAML 語言定義的語言功能[X:class 指示詞](../../../../docs/framework/xaml-services/x-class-directive.md)， [X:subclass 指示詞](../../../../docs/framework/xaml-services/x-subclass-directive.md)，並[X:classmodifier 指示詞](../../../../docs/framework/xaml-services/x-classmodifier-directive.md)。 完全的程式碼應該如何產生，以及如何將整合標記和程式碼，不是 XAML 語言所指定的一部分。 保留最多架構，例如 WPF 來判斷如何將整合程式碼、 如何使用 XAML 應用程式和程式設計模型，以及組建中的動作或其他支援，這一切需要。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>程式碼後置、 事件處理常式，並在 WPF 中的部分類別需求  
  
-   部分類別必須衍生自支援的根項目類型。  
  
-   請注意，在標記編譯建置動作的預設行為，可以讓衍生空白部分類別定義中的程式碼後置的一端。 編譯的結果會假設為部分類別中，基礎頁面根的支援類型，即使未指定。 不過，依賴此行為不是最佳的作法。  
  
-   您在程式碼後置中撰寫的事件處理常式必須是執行個體方法，而且不可為靜態方法。 這些方法必須由所識別之 CLR 命名空間內的部分類別定義`x:Class`。 您無法限定名稱的事件處理常式，以指示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器尋找事件連接不同的類別範圍中的事件處理常式。  
  
-   處理常式必須符合適當的事件的委派，在支援型別系統中。  
  
-   Microsoft Visual Basic 語言的具體來說，您可以使用語言特有`Handles`關鍵字來關聯執行個體和事件處理常式宣告，而不是附加處理常式中的屬性中的處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 不過，這項技術的確有些限制因為`Handles`關鍵字無法支援所有的特定功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統，例如特定路由事件的案例，或附加事件。 如需詳細資訊，請參閱 < [Visual Basic 和 WPF 事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x： 程式碼  
 [X:code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)指示詞的項目定義於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 `x:Code`指示詞項目可以包含內嵌程式碼。 是內嵌定義的程式碼可以互動[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]相同頁面上。 下列範例說明內嵌 C# 程式碼。 請注意，程式碼位於`x:Code`項目，並將程式碼，必須以括住`<CDATA[`...`]]>`逸出的內容[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]，以便[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器 (解譯其中一個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]結構描述或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]結構描述) 不會嘗試解譯內容實際上為[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>內嵌程式碼的限制  
 您應該考慮避免或限制的內嵌程式碼使用。 架構和程式碼的原理，維護在標記和程式碼後置之間有分隔會保留的設計工具] 和 [開發人員角色更多不同。 更技術性的層級中，您為內嵌程式碼撰寫的程式碼可能會很冗長，因此若要撰寫，因為您一律將寫入到[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]產生部分類別中，且只能使用預設 XML 命名空間對應。 因為您無法新增`using`陳述式，您必須完整限定的許多[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]您進行的呼叫。 預設值[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]對應包含大部分但非全部[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]在於的命名空間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件，您必須完整限定類型和成員包含在其他的 CLR 命名空間內的呼叫。 您也無法定義部分類別以外的項目中的內嵌程式碼中，且您參考的所有使用者程式碼實體都必須是成員或產生的部分類別中的變數。 其他語言特定程式設計功能，例如巨集或`#ifdef`針對全域變數或組建變數，也會不提供。 如需詳細資訊，請參閱 < [X:code 內建 XAML 類型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code 內建 XAML 類型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
