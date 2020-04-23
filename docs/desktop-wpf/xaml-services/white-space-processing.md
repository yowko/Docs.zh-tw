---
title: XAML 中的空白字元處理
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 05f28c9115326424164b92e1b704c52bba31cf35
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071602"
---
# <a name="white-space-processing-in-xaml"></a>XAML 中的空白字元處理

XAML 的語言規則規定[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], 重要的空白必須由處理器實現處理。 本文記錄這些 XAML 語言規則。 它還記錄了由 XAML 處理器和 XAML[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]寫入器 實現序列化定義的其他空白處理。

## <a name="white-space-definition"></a>空白定義

與 XML 一致[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)],中的空白字元是空格、換行符和選項卡。它們分別對應於 Unicode 值 0020、000A 和 0009。

## <a name="white-space-normalization"></a>空白規格化

預設情況下,當[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理器處理[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]檔時,將發生以下空白規範化:

1. 東亞字元間的換行字元會遭到移除。 如需這個詞彙的定義，請參閱本主題稍後的＜東亞字元＞一節。

2. 所有空白字元(空白、換行元、選項卡)都將轉換為空格。

3. 所有連續的空格會被刪除並取代為一個空格。

4. 緊接在開始標記之後的空格會遭到刪除。

5. 緊接在結束標記之前的空格會遭到刪除。

「預設」會對應到 [xml:space](xml-space-handling.md) 屬性的預設值所表示的狀態。

## <a name="white-space-in-inner-text-and-string-primitives"></a>內部文字中的空白與字串基元

上述正規化規則適用於 XAML 項目中的內部文字。 正規化後，XAML 處理器會依據下列情況將任何內部文字轉換成適當的類型：

- 如果屬性的類型不是集合，但不是直接的 <xref:System.Object> 類型，XAML 處理器會嘗試使用該類型的類型轉換器，轉換成該類型。 在這裡轉換失敗會導致編譯時期錯誤。

- 如果屬性的類型是集合，而且內部文字是連續的 (未插入項目標記)，內部文字會剖析為單一 <xref:System.String>。 如果集合類型無法接受 <xref:System.String>，這也會導致編譯時期錯誤。

- 如果屬性的類型是 <xref:System.Object>，內部文字會剖析為單一 <xref:System.String>。 如果在其中插入項目標記，由於 <xref:System.Object> 類型即表示單一物件 (否則會是<xref:System.String> )，因此會導致編譯時期錯誤。

- 如果屬性的類型是集合，而且內部文字不是連續的，第一個子字串會轉換成 <xref:System.String> 並加入做為集合項目，插入的項目也會加入做為集合項目，而最後的結尾子字串 (如果有的話) 會加入做為集合的第三個 <xref:System.String> 項目。

## <a name="preserving-white-space"></a>保留空白

有幾個技術用於保留源[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]中的空白,以便最終呈現[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]不受 處理器空白規範化的影響。

**xml:space="保留":** 在需要空白保留的元素級別指定此屬性。 這樣做會保留所有空白字元，其中包括程式碼編輯應用程式為了以視覺上直覺的巢狀結構來「美化」對齊項目可能加入的空格。 不過，這些空格的呈現與否是由包含項目的內容模型所決定。 避免在`xml:space="preserve"`根級別指定,因為無論如何設置屬性,大多數物件模型都不認為空白很重要。 全域設定 `xml:space` 可能會對某些實作中的 XAML 處理 (特別是序列化) 帶來效能影響。 最好僅將屬性設置為在字串中呈現空白或為空白重要集合的元素級別。

**實體和非破斷空格**[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]: 支援將任何 Unicode 實體放置在文字物件模型中。 您可以使用專用實體,如非中斷空間(&\#160;在 UTF-8 編碼中)。 您也可以使用支援不分行空格字元的 RTF 文字控制項。 如果您使用實體來模擬縮排等版面配置特性，應該要特別小心，因為相較於在一般版面配置系統中產生縮排結果的功能 (例如適當使用面板和邊界)，實體的執行階段輸出會隨更多因素而改變。 例如，實體會回應使用者選取的字型，對應至相關字型並可能變更大小。

## <a name="east-asian-characters"></a>東亞字元

"東亞字元"定義為一組 Unicode 字元範圍 U+20000 到 U+2FFFD 和 U=30000 到 U+3FFFD。 這個子集有時也稱為「CJK 表意字元」。 如需詳細資訊，請參閱 <https://www.unicode.org>。

## <a name="white-space-and-text-content-models"></a>空白與文字內容模型

實際上,保留空白只是所有可能內容模型的子集所關心的。 組成該子集的內容模型可以接受某種形式的單一 <xref:System.String> 類型、專用 <xref:System.String> 集合，或者 <xref:System.String> 和 <xref:System.Collections.IList> 或 <xref:System.Collections.Generic.ICollection%601> 集合中其他類型的混合。

### <a name="white-space-and-text-content-models-in-wpf"></a>WPF 中的空白與文字內容模型

為了方便說明，本節的其餘部分將參考 WPF 所定義的特定類型。 本文中描述的空白處理功能與 .NET XAML 服務和 WPF 相關。 若要查看執行中的行為，您可以使用某個 WPF XAML 標記進行實驗，並在物件圖形中檢視結果，然後再重新序列化為標記。

即使對於可以採用字串的內容模型,這些內容模型中的默認行為是保留的任何空白都不被視為重要。 例如,<xref:System.Windows.Controls.ListBox>採用<xref:System.Collections.IList>, 但空格(<xref:System.Windows.Controls.ListBoxItem>如每個 )之間的換行符不保留且不呈現。 如果您嘗試使用換行字元做為 <xref:System.Windows.Controls.ListBoxItem> 項目之字串間的分隔符號，則完全無法運作；以換行字元分隔的字串會視為一個字串和一個項目。

那些確實將空白視為重要集合通常是流文檔模型的一部分。 支援空白儲存行為的主要集合是<xref:System.Windows.Documents.InlineCollection>。 此集合類別使用<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>宣告 。找到此屬性後,[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理器會將集合中的空白視為重要空間。 表示集合中的`xml:space="preserve"`和空白的組合是保留和呈現所有空白。 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 中`xml:space="default"`<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>的空白和空白的組合會導致前面描述的初始空白規範化,該規範化在某些位置留下一個空格,這些空間將保留並呈現。 您可以自行決定要使用哪一種行為，而且您應該選擇性地使用 `xml:space` 來允許您想要的行為。

此外,某些內聯元素表示流文檔模型中的換行符,即使在空白重要集合中,也不應引入額外的空間。 例如,<xref:System.Windows.Documents.LineBreak>元素的用途與\<HTML 中的 BR/> 標籤相同,對於標記中的可讀<xref:System.Windows.Documents.LineBreak>性,通常由創作的換行符與任何後續文本分隔。 該換行字元不應該正規化為下一行的前置空格。 為了啟用<xref:System.Windows.Documents.LineBreak>該行為,元素的類定義應用<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], 然後由處理器解釋該定義<xref:System.Windows.Documents.LineBreak>意味著周圍的 空白始終被修剪。

## <a name="see-also"></a>另請參閱

- [XAML 概述 (WPF)](../fundamentals/xaml.md)
- [XML字元實體和XAML](xml-character-entities.md)
- [xml:XAML 中的空間處理](xml-space-handling.md)
