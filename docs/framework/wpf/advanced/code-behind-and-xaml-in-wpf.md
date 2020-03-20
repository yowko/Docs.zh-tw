---
title: 代碼背後和XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145341"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF 中的程式碼後置和 XAML
<a name="introduction"></a>代碼後面是一個術語，用於描述在標記編譯時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]與標記定義物件聯接的代碼。 本主題介紹代碼後面的要求，以及 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]代碼的替代內聯代碼機制。  
  
 本主題包含下列幾節：  
  
- [必要條件](#Prerequisites)  
  
- [代碼背後和XAML語言](#codebehind_and_the_xaml_language)  
  
- [WPF 中的代碼落後、事件處理常式和部分類要求](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x：代碼](#x_Code)  
  
- [內聯代碼限制](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假定您已閱讀[XAML 概述 （WPF），](../../../desktop-wpf/fundamentals/xaml.md)並且對 CLR 和麵向物件程式設計有一些基本知識。  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>代碼背後和XAML語言  
 XAML 語言包括語言級功能，這些功能使得可以從標記檔端將代碼檔與標記檔相關聯。 具體來說，XAML 語言定義了語言功能[x：類指令](../../../desktop-wpf/xaml-services/xclass-directive.md) [、x：子類指令](../../../desktop-wpf/xaml-services/xsubclass-directive.md)和[x：類修改器指令](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md)。 代碼的生成方式以及如何集成標記和代碼並不是 XAML 語言指定的部分。 由 WPF 等框架來確定如何集成代碼、如何在應用程式和程式設計模型中使用 XAML 以及構建操作或所有所需的其他支援。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF 中的代碼落後、事件處理常式和部分類要求  
  
- 部分類必須派生自支援根項目的類型。  
  
- 請注意，在標記編譯生成操作的預設行為下，可以將派生留空于代碼後面的部分類定義中。 編譯的結果將假定頁面根的背襯類型是部分類的基礎，即使未指定。 但是，依賴此行為不是最佳做法。  
  
- 在代碼後面編寫的事件處理常式必須是實例方法，不能是靜態方法。 這些方法必須由 標識`x:Class`的 CLR 命名空間中的部分類定義。 不能限定事件處理常式的名稱來指示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器查找事件處理常式以查找其他類作用域中的事件佈線。  
  
- 處理常式必須匹配支援類型系統中相應事件的委託。  
  
- 具體對於 Microsoft Visual Basic 語言，可以使用特定于`Handles`語言的關鍵字將處理常式與處理常式聲明中的實例和事件相關聯，而不是將處理常式附加到 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的屬性。 但是，此技術確實有一些限制，`Handles`因為關鍵字不支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統的所有特定功能，例如某些路由事件方案或附加事件。 有關詳細資訊，請參閱[視覺化基本和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x：代碼  
 [x：代碼](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)是在 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義的指令元素。 `x:Code`指令元素可以包含內聯程式設計代碼。 內聯定義的代碼可以在同一頁上與 的代碼[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]進行交互。 下面的示例說明了內聯 C# 代碼。 請注意，代碼位於元素內`x:Code`，並且代碼必須由 ... `<CDATA[``]]>`以逃避 XML 的內容，以便[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器（解釋[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]架構或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]架構）不會嘗試將內容從字面上解釋為 XML。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>內聯代碼限制  
 應考慮避免或限制內聯代碼的使用。 在體系結構和編碼理念方面，保持標記和代碼後面的分離使設計人員和開發人員的角色更加明顯。 在更技術化的層面上，為內聯代碼編寫的代碼可能難以編寫，因為您始終寫入[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]生成的部分類，並且只能使用預設的 XML 命名空間映射。 由於無法添加`using`語句，因此必須完全限定您進行的許多 API 呼叫。 預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]映射包括[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式集中存在的大多數（但不是所有 CLR 命名空間）;您必須完全限定對其他 CLR 命名空間中包含的類型和成員的調用。 您也不能在內聯代碼中定義除部分類之外的任何內容，並且引用的所有使用者代碼實體都必須作為成員或變數存在於生成的部分類中。 其他特定于語言的程式設計功能（如宏或`#ifdef`針對全域變數或生成變數）也不可用。 有關詳細資訊，請參閱[x：代碼內部 XAML 類型](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code 內建 XAML 類型](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [建置 WPF 應用程式](../app-development/building-a-wpf-application-wpf.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
