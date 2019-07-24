---
title: WPF 中的程式碼後置和 XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: acd8c9ff0a4ff718dba272958a3e63820bcf1354
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401616"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF 中的程式碼後置和 XAML
<a name="introduction"></a>程式碼後置是一個詞彙, 用來描述當[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面標記編譯時, 與標記定義的物件聯結的程式碼。 本主題描述程式碼後置的需求, 以及中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]程式碼的替代內嵌程式碼機制。  
  
 本主題包含下列幾節：  
  
- [必要條件](#Prerequisites)  
  
- [程式碼後置和 XAML 語言](#codebehind_and_the_xaml_language)  
  
- [WPF 中的程式碼後置、事件處理常式和部分類別需求](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [內嵌程式碼限制](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已閱讀[XAML 總覽 (WPF)](xaml-overview-wpf.md) , 並有一些 CLR 和麵向物件程式設計的基本知識。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>程式碼後置和 XAML 語言  
 XAML 語言包含語言層級功能, 可讓程式碼檔案與標記檔案建立關聯, 從標記檔案端。 具體而言, XAML 語言會定義語言功能[x:Class](../../xaml-services/x-class-directive.md)指示詞、 [x:Subclass](../../xaml-services/x-subclass-directive.md)指示詞和[x:ClassModifier](../../xaml-services/x-classmodifier-directive.md)指示詞。 確切的程式碼的產生方式, 以及如何整合標記和程式碼, 不是 XAML 語言所指定的部分。 它會留給 WPF 這類架構, 以決定如何整合程式碼、如何在應用程式和程式設計模型中使用 XAML, 以及所需的組建動作或其他支援。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF 中的程式碼後置、事件處理常式和部分類別需求  
  
- 部分類別必須衍生自支援根項目的類型。  
  
- 請注意, 在 [標記編譯組建] 動作的預設行為之下, 您可以在程式碼後置的部分類別定義中, 保留空白的衍生。 編譯的結果會假設頁面根目錄的支援類型是部分類別的基礎, 即使未指定, 也是如此。 不過, 依賴此行為並不是最佳作法。  
  
- 您在程式碼後置中撰寫的事件處理常式必須是實例方法, 而且不能是靜態方法。 這些方法必須由所識別`x:Class`之 CLR 命名空間內的部分類別來定義。 您無法限定事件處理常式的名稱, 以指示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器在不同的類別範圍中尋找事件連接的事件處理常式。  
  
- 處理常式必須符合支援型別系統中適當事件的委派。  
  
- 特別針對 Microsoft Visual Basic 語言, 您可以使用特定`Handles`語言的關鍵字, 將處理常式與處理常式宣告中的實例和事件產生關聯, 而不是在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]附加具有屬性的處理常式。 不過, 這項技術的確有一些限制, `Handles`因為關鍵字無法支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統的所有特定功能, 例如特定的路由事件案例或附加事件。 如需詳細資訊, 請參閱[Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x:Code](../../xaml-services/x-code-intrinsic-xaml-type.md)是在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義的指示詞元素。 `x:Code`指示詞元素可以包含內嵌程式設計程式碼。 以內嵌方式定義的程式碼可以與相同[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面上的互動。 下列範例說明內嵌C#程式碼。 請注意, 此程式碼位於`x:Code`元素內, 而且程式碼必須`<CDATA[`括在 .。。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]若要對的內容進行轉義, 讓處理器 (解讀架構或架構) 不會嘗試將內容以字面方式解讀為[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]。 `]]>`  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>內嵌程式碼限制  
 您應該考慮避免或限制使用內嵌程式碼。 就架構和編碼原理而言, 維護標記和程式碼後置之間的分隔可讓設計工具和開發人員角色更為獨特。 在更技術性的層級上, 您針對內嵌程式碼撰寫的程式碼可能很難撰寫, 因為您一律會寫入[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]產生的部分類別, 而且只能使用預設的 XML 命名空間對應。 因為您無法加入`using`語句, 所以您必須完全符合您所做的許多 API 呼叫。 預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]對應包括[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]元件中所存在的大部分 CLR 命名空間, 而非全部, 而您必須完整限定對包含在其他 clr 命名空間中的類型和成員的呼叫。 您也不能在內嵌程式碼中定義部分類別以外的任何專案, 而且您參考的所有使用者程式碼實體都必須以成員或變數的形式存在於所產生的部分類別內。 其他語言特定的程式設計功能, 例如宏`#ifdef`或針對全域變數或組建變數, 也無法使用。 如需詳細資訊, 請參閱 X:Code 內建[XAML 類型](../../xaml-services/x-code-intrinsic-xaml-type.md)。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [x:Code 內建 XAML 類型](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [建置 WPF 應用程式](../app-development/building-a-wpf-application-wpf.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
