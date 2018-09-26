---
title: JSON 和 XML 之間的對應
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 075f85887f99708dd1f3479bf0b036203886af71
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156672"
---
# <a name="mapping-between-json-and-xml"></a>JSON 和 XML 之間的對應
<xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> 所產生的讀取器與寫入器會透過 JavaScript 物件標記法 (JSON) 內容來提供 XML API。 JSON 使用 JavaScript 物件常值的子集對資料進行編碼。 讀取器和寫入器所產生的這個處理站時也會使用 JSON 內容所使用的 Windows Communication Foundation (WCF) 應用程式傳送或接收<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>或<xref:System.ServiceModel.WebHttpBinding>。

使用 JSON 內容進行初始化時，JSON 讀取器行為將與 XML 文字讀取器對 XML 執行個體所執行的動作相同。 當您針對 JSON 讀取器進行一系列的呼叫，進而在 XML 文字讀取器產生特定 XML 執行個體時，就會寫出 JSON 內容。 本主題將說明此 XML 執行個體與 JSON 內容之間的對應，以供進階案例使用。

就內部而言，JSON 會表示為 XML infoset 時由 WCF 所處理。 一般來說，您不需要關心這個內部表示法，因為對應只是一個邏輯概念：通常，JSON 不會在記憶體中實際轉換為 XML，或是從 XML 轉換為 JSON。 對應代表 XML API 可用來存取 JSON 內容。

WCF 會使用 JSON，常見的情況時，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>自動插入所<xref:System.ServiceModel.Description.WebScriptEnablingBehavior>行為，或由<xref:System.ServiceModel.Description.WebHttpBehavior>時適當的行為。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 了解 JSON 和 XML InfoSet 之間的對應關係，其運作方式就好像是直接處理 JSON 一樣  (您可以使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 來搭配任何的 XML 讀取器或寫入器，前提是您必須了解 XML 需符合下列對應關係)。

在進階案例中，您可能需要直接存取下列對應。 這些情況通常會在您想要以自訂方式來序列化或還原序列化 JSON，而且不想仰賴 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>，或是當您針對包含 JSON 的訊息直接處理 <xref:System.ServiceModel.Channels.Message> 型別時才會發生。 JSON-XML 對應同時可適用於訊息記錄。 當在 WCF 中使用的訊息記錄功能，JSON 訊息會記錄為 XML，根據下一節中所述的對應。

若要釐清對應的概念，請參閱下列 JSON 文件範例。

```json
{"product":"pencil","price":12}
```

若要使用先前所述的其中一種讀取器來讀取此 JSON 文件，請使用您通常用來讀取下列文件的相同 <xref:System.Xml.XmlDictionaryReader> 呼叫序列。

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

此外，如果在範例中的 JSON 訊息是接收 WCF，且記錄，您會看到上述記錄檔中的 XML 片段。

## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON 和 XML InfoSet 之間的對應
正式地說，對應是之間 JSON 中所述[RFC 4627](https://go.microsoft.com/fwlink/?LinkId=98808) （除非有特定限制寬鬆及某些加入其他限制） 和 XML infoset （以及非文字 XML） 中所述[XML 資訊設定](https://go.microsoft.com/fwlink/?LinkId=98809)。 請參閱本主題適用於定義*資訊項目*和 [方括號] 中的欄位。

空白的 JSON 文件對應到空白的 XML 文件，而是空白的 XML 文件對應至空白的 JSON 文件。 在 XML 對 JSON 的對應，泛空白字元開頭與結尾泛空白字元的文件之後不允許。

此對應會在文件資訊項目 (Document Information Item，DII) 或項目資訊項目 (Element Information Item，EII) 與 JSON 之間定義。 EII (或 DII 之 [document element] 屬性)，將稱為 JSON 根項目。 請注意，本對應不支援文件片段 (包含多個根項目的 XML)。

範例：下列文件：

```xml
<?xml version="1.0"?>
<root type="number">42</root>`
```

以及下列項目：

```xml
<root type="number">42</root>
```

兩者都對應至 JSON。 <`root`> 元素是根 JSON 元素，這兩種情況。

此外，在 DII 情況中，您應該考量下列事項：

- 某些 [children] 清單中的項目不得出現。 當您讀取從 JSON 開始對應的 XML 時，請勿以此事實為基準。

- [children] 清單不包含任何註解資訊項目。

- [children] 清單不包含任何 DTD 資訊項目。

- [Children] 清單不包含任何個人資訊 (PI) 資訊項目 (`<?xml…>`宣告不會被視為 PI 資訊項目)

- [notations] 集合是空的。

- [unparsed entities] 集合是空的。

範例：下列文件未對應至 JSON，因為 [children] 保留一個 PI 和文件。

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

JSON 根項目的 EII 具有下列特性：

- [local name] 包含值 "root"。

- [namespace name] 沒有值。

- [prefix] 沒有值。

- [children] 可能包含 EII (代表將進一步介紹的「內部項目」) 或 CII (將進一步介紹的字元資訊項目) 或不包含任何一項，但並非兩者都不包含。

- [attributes] 可能包含下列選擇性屬性資訊項目 (AII)

- 如進一步介紹的 JSON 型別屬性 ("type")。 此屬性可用來保存對應 XML 中的 JSON 型別 (字串、數字、布林值、物件、陣列或 Null)。

- 資料合約名稱屬性 ("\_\_類型 」) 進一步所述。 如果 JSON 型別屬性同時存在，且其 [normalized value] 為 "object" 的話，才會存在此屬性。 `DataContractJsonSerializer` 可使用此屬性來保存資料合約型別資訊，例如，一個衍生型別已序列化且預期基底型別的多型案例。 如果您不是使用 `DataContractJsonSerializer`，在大部分情況下會忽略此屬性。

- 在 [in-scope namespaces] 包含"xml"的繫結至`http://www.w3.org/XML/1998/namespace`如 infoset 規格所託管。

- [children]、[attributes] 和 [in-scope namespaces] 只能包含先前指定的項目，而 [namespace attributes] 不得包含任何成員，但是在讀取從 JSON 對應過來的 XML 時，不能以這些事實為基礎。

範例：下列文件未對應至 JSON，因為 [namespace attributes] 不是空的。

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

JSON 型別屬性的 AII 具有下列特性：

- [namespace name] 沒有值。
- [prefix] 沒有值。
- [local name] 為 "type"。
- [normalized value] 是將於下一節中說明的其中一個可能的型別值。
- [specified] 為 `true`。
- [attribute type] 沒有值。
- [references] 沒有值。

資料合約名稱屬性的 AII 具有下列特性：

- [namespace name] 沒有值。
- [prefix] 沒有值。
- [local name] 是"\_\_類型 」 （兩個底線和"type"）。
- [normalized value] 是任何有效的 Unicode 字串 – 下一節將說明此字串與 JSON 的對應。
- [specified] 為 `true`。
- [attribute type] 沒有值。
- [references] 沒有值。

包含在 JSON 根項目的內部項目或其他內部項目都具有下列特性：

- 如進一步介紹，[區域名稱] 可能會有任何值。
- [namespace name]、[prefix]、[children]、[attributes]、[namespace attributes]，和 [in-scope namespaces] 都和 JSON 根項目受制於相同的規則。

同時在 JSON 根項目與內部項目之中，JSON 型別屬性會定義對 JSON 及可能的 [children] 和其解譯的對應關係。 屬性的 [normalized value] 會區分大小寫都必須是小寫，並不能包含空白字元。

|[normalized 值] 的 JSON 型別屬性的 AII|對應 EII 的已允許 [children]|JSON 對應|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (或缺乏 JSON 型別 AII)<br /><br /> `string` 與 JSON 型別 AII 的缺席，雙雙都會導致 `string` 成為預設值。<br /><br /> 因此，`<root> string1</root>` 會對應至 JSON `string` "string1"。|0 或更多 Cii|JSON `string` (JSON RFC，2.5 節)。 每個 `char` 字元都會對應至 CII 的 [character code]。 如果沒有任何 CII，就會對應至空的 JSON `string`。<br /><br /> 範例：下列項目對應至 JSON 片段：<br /><br /> `<root type="string">42</root>`<br /><br /> JSON 片段為 "42"。<br /><br /> 在 XML 對 JSON 的對應中，必須逸出的字元會對應至逸出字元，其他所有字元則是對應至尚未逸出的字元。 "/"為特殊字元 – 即使它不一定要逸出 (寫出做為 「\\/")。<br /><br /> 範例：下列項目對應至 JSON 片段。<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON 片段為" \\「 da\\/ta\\""。<br /><br /> 在 JSON 對 XML 的對應中，任何逸出的字元和尚未逸出的字元會正確地對應至相對應的 [character code]。<br /><br /> 範例：JSON 片段 "\u0041BC" 會對應至下列 XML 項目。<br /><br /> `<root type="string">ABC</root>`<br /><br /> 可以由未對應到 XML 的泛空白字元 (JSON RFC 的第 2 節中的 ' ws') 括住字串。<br /><br /> 範例：JSON 片段 "ABC" (在第一個雙引號之前留有一些空格) 會對應至下列 XML 項目。<br /><br /> `<root type="string">ABC</root>`<br /><br /> 在 XML 中的任何泛空白字元會對應至 JSON 中的泛空白字元。<br /><br /> 範例：下列 XML 項目對應至 JSON 片段。<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON 片段為 " A BC "。|
|`number`|1 或更多 CII|JSON `number` (JSON RFC，第 2.4 小節)，可能是括住空白字元。 數字/空格組合中的每個字元是字元的對應 cii 的 [character code]。<br /><br /> 範例：下列項目對應至 JSON 片段。<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON 片段為 42 <br /><br /> （會保留空白字元。）|
|`boolean`|4 或 5 個 Cii (對應至`true`或`false`) 可能會被其他空白 Cii 所。|對應至字串 "true" 的 CII 序列會對應至常值 `true`，而對應至字串 "false" 的 CII 序列則是對應至常值 `false`。 周圍的空白字元會保留。<br /><br /> 範例：下列項目對應至 JSON 片段。<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON 片段為 `false`。|
|`null`|全都不允許。|常值 `null`。 在 JSON 對 XML 的對應，`null`可能由未對應到 XML 的泛空白字元 (第 2 節中的 ' ws') 括住。<br /><br /> 範例：下列項目對應至 JSON 片段。<br /><br /> `<root type="null"/>`<br /><br /> 或<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> 兩個案例中的 JSON 片段都是 `Null`。|
|`object`|0 或更多 EII|如 JSON RFC，2.2 小節中所述之 `begin-object` (左側大括號)，後面接著每個 EII 的成員記錄 (如進一步介紹中所述)。 如果有一個以上的 EII，成員記錄之間就會存在數值分隔符號 (逗號)。 這些全部都會接著一個結尾物件 (右側大括號)。<br /><br /> 範例：下列項目對應至 JSON 片段。<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> JSON 片段為 `{"type1":"aaa","type2":"bbb"}`。<br /><br /> 如果資料合約型別屬性存在 XML 對 JSON 的對應中，則會在開頭插入額外的成員記錄。 其名稱是資料合約型別屬性 [local name] ("\_\_類型 」)，且其值為 [normalized value] 的屬性。 相反地，在 JSON 對 XML 的對應，如果第一個成員記錄名稱是資料合約型別屬性 [local name] (也就是 「\_\_類型 」)，對應的資料合約型別屬性會出現在對應的 XML 中，但相對應的 EII 不存在。 請注意，若要套用這個特殊對應，這項成員記錄必須先出現在 JSON 物件中。 這代表了從一般 JSON 處理中離開，其中成員記錄的順序並不重要。<br /><br /> 範例：<br /><br /> 下列 JSON 片段會對應至 XML。<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> 下列為 XML 程式碼。<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> 請注意， \_\_型別 AII 已存在，但沒有任何\_\_輸入 EII。<br /><br /> 但是，如果 JSON 中的順序如下列範例所示反轉過來的話，<br /><br /> {"name":"John"，"\_\_類型 」:"Person"}<br /><br /> 就會顯示相對應的 XML。<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> 也就是\_類型 （_t） 會停止具有特殊意義，並對應至 EII 像往常一樣，不是 AII。<br /><br /> 當 AII 對應至 JSON 值時，其 [normalized value] 的逸出/未逸出規則與 JSON 值的逸出/未逸出規則相同，下表中的 "string" 列將指定此規則。<br /><br /> 範例：<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> 先前範例可對應至下列 JSON。<br /><br /> `{"__type":"\\abc"}`<br /><br /> 在 XML 對 JSON 的對應，第一個 EII 的 [區域名稱] 必須不是 」\_\_類型 」。<br /><br /> 泛空白字元 (`ws`) 會一律不會產生 XML 對 JSON 的對應物件，並會忽略在 JSON 對 XML 的對應。<br /><br /> 範例：下列 JSON 片段會對應至 XML 項目。<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> 下列程式碼說明 XML 項目。<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|array|0 或更多 EII|如 JSON RFC，2.3 小節中所述之開始-陣列 (左側大括號)，後面接著每個 EII 的陣列記錄 (如進一步介紹中所述)。 如果有一個以上的 EII，陣列記錄之間就會存在數值分隔符號 (逗號)。 這些全部都會緊跟著結束-陣列。<br /><br /> 範例：下列 XML 項目對應至 JSON 片段。<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON 片段為 ["aaa","bbb"]<br /><br /> 泛空白字元 (`ws`) 會一律不會產生 XML 對 JSON 陣列的對應，並會忽略在 JSON 對 XML 的對應。<br /><br /> 範例： JSON 片段。<br /><br />`["aaa", "bbb"]`<br /><br /> 它所對應的 XML 項目。<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

成員記錄使用方式如下：

- 內部項目的 [local name] 會對應至 `string` 的 `member` 部分，如 JSON RFC，2.2 小節中所定義。

範例：下列項目對應至 JSON 片段。

`<root type="object"/>`

`<myLocalName type="string">aaa</myLocalName>`

`</root >`

下列將顯示 JSON 片段。

`{"myLocalName":"aaa"}`

- 在 XML 對 JSON 的對應中，JSON 中必須逸出的字元會逸出，其他字元則不會逸出。 雖然 "/" 不是必須逸出的字元，還是會逸出 (在 JSON 對 XML 的對應中，它不需要逸出)。 若您需要針對 JSON 中的 `DateTime` 資料支援使用 ASP.NET AJAX 格式，這是必要的條件。

- 在 JSON 對 XML 的對應中，會採用所有的字元 (必要時包括尚未逸出的字元) 來形成 `string` 以產生 [local name]。

- 根據 `JSON Type Attribute`，內部項目 [children] 會對應至 2.2 小節中的值，就像是 `Root JSON Element` 一樣。 可允許使用多層的巢狀 EII (包含陣列中的巢狀結構)。

範例：下列項目對應至 JSON 片段。

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

下列為它所對應的 JSON 片段。

`{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`

> [!NOTE]
> 在先前的對應中，沒有 XML 編碼步驟。 因此，WCF 只支援 JSON 文件，其中索引鍵的名稱中的所有字元都是 XML 項目名稱中有效的字元。 例如，由於 < 不是有效的 XML 項目名稱，因此不支援 JSON 文件 {"<":"a"}。

相反的情況 (在 XML 中為有效字元，但是在 JSON 中卻為無效) 並不會導致任何問題，因為先前的對應已經包含了 JSON 逸出/未逸出步驟。

陣列記錄使用方式如下：

- 內部項目的 [local name] 為 "item"。

- 內部項目的 [children] 會根據 JSON 型別屬性對應至 2.3 小節中的值，對 JSON 的根項目也是這麼做。 可允許使用多層的巢狀 EII (包含物件中的巢狀結構)。

範例：下列項目對應至 JSON 片段。

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

下列為 JSON 片段。

`["myValue1",2,[true,null]]`

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [獨立 JSON 序列化](stand-alone-json-serialization.md)