---
title: "UriTemplate 與 UriTemplateTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9d08fa0e0ec556779d246af5ec11fcbeb54dedc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate 與 UriTemplateTable
Web 開發人員需要能夠描述其服務所回應的 URI 形式與配置。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 新增了兩個類別，讓開發人員可以更充分的掌控其 URI。 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中構成 URI 分派引擎的基礎。 這些類別可以自行利用，讓開發人員充分運用範本與 URI 對應機制，而無須實作 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
## <a name="templates"></a>範本  
 範本提供了一種用來描述相對 URI 集合的方式。 下表中的 URI 範本集將說明如何定義負責擷取各種氣象資訊型別的系統。  
  
|資料|範本|  
|----------|--------------|  
|國內趨勢預測|weather/national|  
|各州趨勢預測|weather/{state}|  
|城市趨勢預測|weather/{state}/{city}|  
|活動趨勢預測|weather/{state}/{city}/{activity}|  
  
 這份表格說明結構上類似的 URI 集合。 每個項目都是 URI 範本。 大括號內的片段描述變數， 大括號外的片段則描述常值字串。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範本類別可讓開發人員包含傳入的 URI，例如，"/weather/wa/seattle/cycling"，並將其對應至說明該類別的範本 "/weather/{state}/{city}/{activity}"。  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> 是一個會封裝 URI 範本的類別。 建構函式會包含用來定義範本的字串參數。 此字串會將範本包含在下一節中說明的格式裡。 <xref:System.UriTemplate> 類別所提供的方法可讓您將傳入的 URI 與範本進行比對、從範本產生 URI、擷取範本中使用的變數名稱集合，並判斷這兩個範本是否相等，然後傳回範本的字串。  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> 包含基底位址與候選 URI，並嘗試將 URI 與範本進行比對。 如果比對成功，則會傳回 <xref:System.UriTemplateMatch> 執行個體。 <xref:System.UriTemplateMatch>物件包含一個起始 URI、一個候選 URI、一個查詢參數的名稱/值集合、一個相對路徑片段陣列、一個相符的變數名稱/值集合、用來執行比對的<xref:System.UriTemplate>執行個體、一個包含候選 URI (當範本包含萬用字元時所使用) 中任何不相符部分的字串，以及一個與範本相關聯的物件。  
  
> [!NOTE]
>  <xref:System.UriTemplate> 類別在將範本與候選 URI 與進行比較時，會忽略配置和連接埠編號。  
  
 有兩種方法可讓您從範本中產生 URI：<xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> 和 <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>。 <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> 需要基底位址和參數的名稱/值集合。 當範本經過繫結，就會以這些參數來取代變數。 <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> 將會由左至右取代其接受的名稱/值組。  
  
 <xref:System.UriTemplate.ToString> 會傳回範本字串。  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A> 屬性包含範本字串之路徑片段中所使用的變數名稱集合。  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> 以 <xref:System.UriTemplate> 做為參數，並傳回布林值指出兩個範本是否相等。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]本主題稍後＜相等的範本＞一節。  
  
 <xref:System.UriTemplate> 的設計即是可與符合 HTTP URI 文法的任何 URI 配置搭配使用。 以下是支援的 URI 配置範例：  
  
-   http://  
  
-   https://  
  
-   net.tcp://  
  
-   net.pipe://  
  
-   sb://  
  
 如 file:// 及 urn:// 的配置並不符合 HTTP URI 文法，若搭配 URI 範本使用，會造成無法預期的結果。  
  
### <a name="template-string-syntax"></a>範本字串語法  
 範本包含三大部分：路徑、選擇性查詢以及選擇性片段。 例如，請參閱下列範本：  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 路徑包含 "/weather/{state}/{city}"，查詢包含 "?forecast={length}，而片段則包含 "#frag1"。  
  
 路徑運算式中的前置與句尾斜線是選用的， 查詢與片段運算式可以全部省略掉。 路徑包含一系列以分隔的區段 '/'，每個區段都有常值、 變數名稱 （寫在大括號 {}），或是一個萬用字元 (寫為\*')。 在先前的範本中，"\weather\ 片段是一個常值，而 "{state}" 與 "{city}" 則是變數。 變數會從其大括號的內容，其名稱和更新版本可以取代具象的值，才能建立與*關閉 URI*。 萬用字元是選用的但是只能出現在 URI，以便在邏輯上符合 「 其餘的部分路徑 」 的結尾。  
  
 查詢運算式 (如果有的話)，會指定一系列由 '&' 所分隔且未排序的名稱/值對。 查詢運算式的項目可以是一組常值 (x=2) 或是一組變數 (x={var})。 只有查詢運算式的右側才可以放置變數運算式。 不允許 ({someName} = {someValue}。 不允許使用未成對的值 (?x)。 空白的查詢運算式和查詢運算式包含只在單一之間沒有差異 '？ '（兩者都表示 「 任何查詢 」。）  
  
 片段運算式可能包含一個常值，不允許使用任何變數。  
  
 範本字串中所有的範本變數名稱必須是唯一的。 範本變數名稱不區分大小寫。  
  
 有效的範本字串範例包括：  
  
-   ""  
  
-   "/shoe"  
  
-   "/shoe/*"  
  
-   "{shoe}/boat"  
  
-   "{shoe} / {船 /bed/ {quilt}}"  
  
-   "shoe / {船}"  
  
-   "shoe / {船} / *"  
  
-   "shoe/船？ x = 2"  
  
-   "shoe / {船}？ x = {床}"  
  
-   "shoe/{boat}?x={bed}&y=band"  
  
-   "？ x = {shoe}"  
  
-   "shoe?x=3&y={var}  
  
 無效的範本字串範例包括：  
  
-   "{shoe} / {SHOE} / x = 2"-重複的變數名稱。  
  
-   "{shoe} /boat/？ 床 = {shoe}"– 變數名稱重複。  
  
-   "？ x = 2&x = 3"– 名稱/值組，查詢字串內必須是唯一的即使它們是常值。  
  
-   "？ x = 2 （& s) 」 – 查詢字串的格式不正確。  
  
-   "？ 2 2&x = {shoe}"– 查詢字串必須是名稱/值組。  
  
-   "？ y = 2 （& s) （& s) X = 3"– 查詢字串必須是名稱/值組，名稱開頭不能 '&'。  
  
### <a name="compound-path-segments"></a>複合路徑片段  
 複合路徑片段可以在單一 URI 路徑片段中包含多個變數以及與加入常值的變數。 以下範例列出有效的複合路徑片段：  
  
-   /filename.{ext}/  
  
-   /{filename}.jpg/  
  
-   /{filename}.{ext}/  
  
-   /{a}.{b}someLiteral{c}({d})/  
  
 以下範例列出無效的路徑片段：  
  
-   /{}：變數必須命名。  
  
-   /{shoe}{boat}：變數之間必須以常值分隔。  
  
### <a name="matching-and-compound-path-segments"></a>比對和複合路徑區段  
 複合路徑區段可讓您定義一個 UriTemplate，該 UriTemplate 在單一路徑區段中有多個變數。 例如，在以下的範本字串: 「 位址 / {state}。{city}"兩個變數 （state 和 city） 都在相同的區段中定義。 此範本將會比對的 URL，例如"http://example.com/Washington.Redmond"，但它也會比對像是"http://example.com/Washington.Redmond.Microsoft"的 URL。 在後者的情況下，state 變數將包含"Washington"，city 變數將包含"Redmond.Microsoft"。 在此情況下，任何文字 (除了 ‘/’ 之外) 都會比對 {city} 變數。 如果您想要的範本不比對 「 額外的 」 文字，請將變數放在另一個範本區段中，例如: 「 位址 / {state} / {city}。  
  
### <a name="named-wildcard-segments"></a>命名的萬用字元片段  
 命名的萬用字元片段可以是任一路徑變數片段，其變數名稱會以萬用字元 ‘*’ 開頭。 下列範本字串包含了命名的萬用字元片段，名為 "shoe"。  
  
```  
"literal/{*shoe}"  
```  
  
 萬用字元片段必須遵照下列規則：  
  
-   每一個範本字串最多只能使用一個萬用字元片段命名。  
  
-   命名的萬用字元片段必須置於路徑最右邊的片段中。  
  
-   在同一個範本字串中，不能同時使用命名的萬用字元片段以及匿名的萬用字元片段。  
  
-   命名的萬用字元片段名稱必須是獨一無二的。  
  
-   命名的萬用字元片段無法設定其預設值。  
  
-   命名的萬用字元片段結尾不可以"/"。  
  
### <a name="default-variable-values"></a>預設變數值  
 預設變數值可以讓指定要在範本內使用的變數預設值。 預設變數可以利用大括號指定，在其中宣告變數或是要傳遞給 UriTemplate 建構函式的集合。 以下範例示範兩種利用預設變數值指定 <xref:System.UriTemplate>的方法。  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 此範本宣告了預設值為 `a` 的具名變數 `1`，以及預設值為 `b`的具名變數 `5`。  
  
> [!NOTE]
>  只有路徑片段變數才能有預設值。 查詢字串變數、複合片段變數以及命名的萬用字元變數，都不能有預設值。  
  
 下列程式碼示範進行候選 URI 比對時，會如何處理預設變數。  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  如 http://localhost:8000/// 的 URI 並不符合上列程式碼中的範本，但若 URI 為 http://localhost:8000/ 便是符合的格式。  
  
 下列程式碼示範以範例建立 URI 比對時，會如何處理預設變數。  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
 如果某一個變數指定的預設值為 `null`，則會使用其他幾項條件約束。 如果變數置於範本字串最右邊的片段中，或是片段所有的右邊片段都有 `null` 做為預設值，變數的預設值才可以設為 `null`。 下列是預設值為 `null`的有效範本字串：  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 下列是預設值為 `null`的無效範本字串：  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a>預設值與進行比對  
 將候選 URI 與一個有預設值的範本進行比對時，如果候選 URI 內沒有指定值，預設值會置於 <xref:System.UriTemplateMatch.BoundVariables%2A> 集合中。  
  
### <a name="template-equivalence"></a>相等的範本  
 兩個範本都稱為*結構上相等*時所有範本的常值的比對，並在相同的片段中都擁有變數。 例如，下列範本在結構上是相等的：  
  
-   /a/{var1}/b b/{var2}?x=1&y=2  
  
-   a/{x}/b%20b/{var1}?y=2&x=1  
  
-   a/{y}/B%20B/{z}/?y=2&x=1  
  
 請注意下列幾點事項：  
  
-   如果範本包含好幾條前置斜線，則只會忽略第一條斜線。  
  
-   在您比較範本字串中的結構相等性時，可忽略變數名稱的大小寫，但須注意路徑片段與查詢字串的大小寫。  
  
-   查詢字串尚未排序。  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> 類別代表 <xref:System.UriTemplate> 物件的關聯表，而此物件則是繫結至開發人員所選擇之物件。 <xref:System.UriTemplateTable> 至少必須包含一個 <xref:System.UriTemplate>，才能呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>。 <xref:System.UriTemplateTable> 的內容會等到呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 之後才變更。 呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 時會執行驗證。 執行的驗證類型需視 `allowMultiple` 的 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 參數值而定。  
  
 當呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 並傳入 `false` 時，<xref:System.UriTemplateTable> 會進行檢查以確定表中沒有任何範本。 如果它找到任何結構上相等的範本，就會擲回例外狀況。 當您希望確定只有一個範本符合傳入的 URI 時，就可以使用這個方法來搭配 <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29>。  
  
 當呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 並傳入 `true` 時，<xref:System.UriTemplateTable> 允許多個結構上相等的範本包含在 <xref:System.UriTemplateTable> 中。  
  
 如果將一組 <xref:System.UriTemplate> 物件新增到 <xref:System.UriTemplateTable> 包含查詢字串中，則不得使用語意模糊的字串。 您可以使用相同的查詢字串。  
  
> [!NOTE]
>  雖然 <xref:System.UriTemplateTable> 允許使用 HTTP 以外的配置做為基底位址，但是在進行候選 URI 與範本比對時，仍然會忽略置及連接埠號碼。  
  
### <a name="query-string-ambiguity"></a>查詢字串模稜兩可  
 如果有一個 URI 同時符合多個範本，則共用相同路徑的範本會包含語意模糊的查詢字串。  
  
 下列查詢字串組本身語意都很明確：  
  
-   ?x=1  
  
-   ?x=2  
  
-   ?x=3  
  
-   ?x=1&y={var}  
  
-   ?x=2&z={var}  
  
-   ?x=3  
  
-   ?x=1  
  
-   ?  
  
-   ? x={var}  
  
-   ?  
  
-   ?m=get&c=rss  
  
-   ?m=put&c=rss  
  
-   ?m=get&c=atom  
  
-   ?m=put&c=atom  
  
 下列查詢字串範本組本身語意都很模糊：  
  
-   ?x=1  
  
-   ?x={var}  
  
 "x=1"：與兩個範本相符。  
  
-   ?x=1  
  
-   ?y=2  
  
 "x=1&y=2" 與兩個範本相符。 這是因為查詢字串所包含的查詢字串變數數量可能超出範本所符合的查詢字串變數數量。  
  
-   ?x=1  
  
-   ?x=1&y={var}  
  
 "x=1&y=3" 與兩個範本相符。  
  
-   ?x=3&y=4  
  
-   ?x=3&z=5  
  
> [!NOTE]
>  當字元 á 與 Á 出現在 URI 路徑或 <xref:System.UriTemplate> 路徑片段常值中時，兩者將被視為不同的字元 (但是字元 a 與 A 則被視為相同)。 當字元 á 與 Á 出現在 <xref:System.UriTemplate> {variableName} 或查詢字串中時，兩者將被視為相同的字元 (而且字元 a 與 A 亦將被視為相同)。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [WCF Web HTTP 程式設計物件模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [UriTemplate 表](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate 表發送器](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
