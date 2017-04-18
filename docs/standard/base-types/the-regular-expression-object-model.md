---
title: "規則運算式物件模型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 規則運算式, 反向參考"
  - ".NET Framework 規則運算式, 類別"
  - "反向參考"
  - "Capture 類別"
  - "CaptureCollection 類別"
  - "字元 [.NET Framework], 反向參考"
  - "字元 [.NET Framework], 中繼字元"
  - "字元 [.NET Framework], 規則運算式"
  - "類別 [.NET Framework], 規則運算式"
  - "Group 類別"
  - "GroupCollection 類別"
  - "Match 類別"
  - "MatchCollection 類別"
  - "中繼字元, 反向參考"
  - "中繼字元, 規則運算式類別"
  - "使用規則運算式剖析文字, 反向參考"
  - "使用規則運算式剖析文字, 類別"
  - "使用規則運算式的模式比對, 反向參考"
  - "使用規則運算式的模式比對, 類別"
  - "Regex 類別"
  - "規則運算式 [.NET Framework]"
  - "規則運算式 [.NET Framework], 反向參考"
  - "規則運算式 [.NET Framework], 類別"
  - "重複字元的群組"
  - "使用規則運算式搜尋, 反向參考"
  - "使用規則運算式搜尋, 類別"
  - "字串 [.NET Framework], 規則運算式"
  - "子字串"
ms.assetid: 49a21470-64ca-4b5a-a889-8e24e3c0af7e
caps.latest.revision: 26
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 26
---
# 規則運算式物件模型
<a name="introduction"></a> 本主題說明用來處理 .NET Framework 規則運算式的物件模型。 它包含以下各節：  
  
-   [規則運算式引擎](#Engine)  
  
-   [MatchCollection 和 Match 物件](#Match_and_MCollection)  
  
-   [群組集合](#GroupCollection)  
  
-   [擷取群組](#the_captured_group)  
  
-   [擷取集合](#CaptureCollection)  
  
-   [個別擷取](#the_individual_capture)  
  
<a name="Engine"></a>   
## 規則運算式引擎  
 .NET Framework 中的規則運算式引擎以 <xref:System.Text.RegularExpressions.Regex> 類別表示。 規則運算式引擎負責剖析和編譯規則運算式，以及執行規則運算式模式與輸入字串的比對作業。 引擎是 .NET Framework 規則運算式物件模型的中心元件。  
  
 規則運算式引擎有兩種使用方式：  
  
-   呼叫 <xref:System.Text.RegularExpressions.Regex> 類別的靜態方法。 方法參數包括輸入字串和規則運算式模式。 規則運算式引擎會快取靜態方法呼叫中所使用的規則運算式，因此重複呼叫使用相同規則運算式的靜態規則運算式方法，可提供相對較佳的效能。  
  
-   傳遞規則運算式到類別建構函式，以具現化 <xref:System.Text.RegularExpressions.Regex> 物件。 在此案例中，<xref:System.Text.RegularExpressions.Regex> 物件不可變 \(唯讀\)，並代表與單一規則運算式緊密結合的規則運算式引擎。 由於未快取 <xref:System.Text.RegularExpressions.Regex> 執行個體所使用的規則運算式，因此您不應該以相同的規則運算式將 <xref:System.Text.RegularExpressions.Regex> 物件具現化多次。  
  
 您可以呼叫 <xref:System.Text.RegularExpressions.Regex> 類別的方法來執行下列作業：  
  
-   判定字串是否符合規則運算式模式。  
  
-   擷取單一相符項目或第一個相符項目。  
  
-   擷取所有相符項目。  
  
-   取代相符的子字串。  
  
-   將單一字串分割成字串陣列。  
  
 下面各節將會說明這些作業。  
  
### 比對規則運算式模式  
 如果字串符合模式，<xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> 方法會傳回 `true`，如果不符合，則傳回 `false`。<xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法常用來驗證字串輸入。 例如，下列程式碼可確保字串符合美國境內有效的社會安全號碼。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 規則運算式模式 `^\d{3}-\d{2}-\d{4}$` 的解譯方式如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`^`|比對輸入字串的開頭。|  
|`\d{3}`|比對三個十進位數字。|  
|`-`|比對連字號。|  
|`\d{2}`|比對兩個十進位數字。|  
|`-`|比對連字號。|  
|`\d{4}`|比對四個十進位數字。|  
|`$`|比對輸入字串的結尾。|  
  
### 擷取單一相符項目或第一個相符項目  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=fullName> 方法會傳回 <xref:System.Text.RegularExpressions.Match> 物件，其中包含符合規則運算式模式之第一個子字串的相關資訊。 如果 `Match.Success` 屬性傳回 `true`，指出已找到相符項目，您就可以呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法來擷取後續相符項目的相關資訊。 這些方法呼叫可以一直持續到 `Match.Success` 屬性傳回 `false`。 例如，下列程式碼會使用 <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=fullName> 方法來尋找字串中第一次出現的重複文字。 然後會呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法來尋找所出現的任何其他重複文字。 此範例會在每次方法呼叫之後檢查 `Match.Success` 屬性，以判定目前比對是否成功，以及後面是否應該接著呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 規則運算式模式 `\b(\w+)\W+(\1)\b` 的解譯方式如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`\b`|開始字邊界比對。|  
|`(\w+)`|比對一個或多個文字字元。 這是第一個擷取群組。|  
|`\W+`|比對一或多個非文字字元。|  
|`(\1)`|比對第一個擷取的字串。 這是第二個擷取群組。|  
|`\b`|結束字邊界比對。|  
  
### 擷取所有相符項目  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName> 方法會傳回 <xref:System.Text.RegularExpressions.MatchCollection> 物件，其中包含規則運算式引擎在輸入字串中找到之所有相符項目的相關資訊。 例如，您可以將上一個範例重寫為呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 方法，而不是 <xref:System.Text.RegularExpressions.Regex.Match%2A> 和 <xref:System.Text.RegularExpressions.Match.NextMatch%2A> 方法。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### 取代相符的子字串  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> 方法會將符合規則運算式模式的每個子字串，取代為指定的字串或規則運算式模式，並傳回含有取代項目的整個輸入字串。 例如，下列程式碼會在字串中的十進位數字前面加上美國貨幣符號。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 規則運算式模式 `\b\d+\.\d{2}\b` 的解譯方式如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`\b`|開始字緣比對。|  
|`\d+`|比對一個或多個十進位數字。|  
|`\.`|比對句點。|  
|`\d{2}`|比對兩個十進位數字。|  
|`\b`|結束字緣比對。|  
  
 取代模式 `$$$&` 的解譯方式如下表所示。  
  
|模式|取代字串|  
|--------|----------|  
|`$$`|貨幣符號 \($\) 字元。|  
|`$&`|整個相符子字串。|  
  
### 將單一字串分割成字串陣列  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=fullName> 方法會在規則運算式比對所定義的位置分割輸入字串。 例如，下列程式碼會將編號清單中的項目放在字串陣列中。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 規則運算式模式 `\b\d{1,2}\.\s` 的解譯方式如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`\b`|開始字緣比對。|  
|`\d{1,2}`|比對一個或兩個十進位數字。|  
|`\.`|比對句點。|  
|`\s`|比對空白字元。|  
  
<a name="Match_and_MCollection"></a>   
## MatchCollection 和 Match 物件  
 Regex 方法會傳回兩個屬於規則運算式物件模型的物件：<xref:System.Text.RegularExpressions.MatchCollection> 物件和 <xref:System.Text.RegularExpressions.Match> 物件。  
  
<a name="the_match_collection"></a>   
### 比對集合  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName> 方法會傳回 <xref:System.Text.RegularExpressions.MatchCollection> 物件，其中包含 <xref:System.Text.RegularExpressions.Match> 物件，這些物件代表規則運算式引擎找到的所有相符項目，並按照其於輸入字串中出現的順序排列。 如果沒有相符項目，該方法會傳回 <xref:System.Text.RegularExpressions.MatchCollection> 物件，但不含成員。<xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=fullName> 屬性可讓您依索引存取集合的個別成員，從零到 <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=fullName> 屬性的值減一。<xref:System.Text.RegularExpressions.MatchCollection.Item%2A> 是集合的索引子 \(在 C\# 中\) 和預設屬性 \(在 Visual Basic 中\)。  
  
 依預設，呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName> 方法時會使用延遲評估來填入 <xref:System.Text.RegularExpressions.MatchCollection> 物件。 若要存取需要完整填入集合的屬性，例如 <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=fullName> 和 <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=fullName> 屬性，可能會導致效能傷害。 因此，建議您使用 <xref:System.Collections.IEnumerator> 方法傳回的 <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=fullName> 物件來存取集合。 個別語言會提供包裝集合之 `For` 介面的建構 \(例如 Visual Basic 中的 `Each``foreach`，以及 C\# 中的 <xref:System.Collections.IEnumerator>\)。  
  
 下列範例使用 <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=fullName> 方法，以在輸入字串中找到的所有相符項目來填入 <xref:System.Text.RegularExpressions.MatchCollection> 物件。 此範例會列舉集合、將相符項目複製到字串陣列，並記錄整數陣列中的字元位置。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### 比對  
 <xref:System.Text.RegularExpressions.Match> 類別代表單一規則運算式比對的結果。 您可以用兩個方式來存取 <xref:System.Text.RegularExpressions.Match> 物件：  
  
-   從 <xref:System.Text.RegularExpressions.MatchCollection> 方法傳回的 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName> 物件中擷取。 若要擷取個別 <xref:System.Text.RegularExpressions.Match> 物件，請使用 `foreach` \(在 C\# 中\) 或 `For Each`...`Next` \(在 Visual Basic 中\) 的建構來逐一查看集合，或是使用 <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=fullName> 屬性來依據索引或名稱擷取特定的 <xref:System.Text.RegularExpressions.Match> 物件。 您也可以依索引 \(從零到集合中的物件數減一\) 從集合擷取個別 <xref:System.Text.RegularExpressions.Match> 物件。 不過，此方法不會利用延遲評估，因為它會存取 <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=fullName> 屬性。  
  
     下列範例會使用 <xref:System.Text.RegularExpressions.Match> 或 <xref:System.Text.RegularExpressions.MatchCollection>...`foreach` 建構逐一查看集合，以從 `For Each` 物件擷取個別 `Next` 物件。 規則運算式會單純比對輸入字串中的字串 "abc"。  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   呼叫 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=fullName> 方法，它會傳回代表字串中第一個相符項目或字串一部分的 <xref:System.Text.RegularExpressions.Match> 物件。 您可以擷取 `Match.Success` 屬性的值，以判斷是否找到相符項目。 若要擷取代表後續相符項目的 <xref:System.Text.RegularExpressions.Match> 物件，請重複呼叫 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法，直到傳回之 `Success` 物件的 <xref:System.Text.RegularExpressions.Match> 屬性為 `false`。  
  
     下列範例使用 <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=fullName> 和 <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法來比對輸入字串中的字串 "abc"。  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 <xref:System.Text.RegularExpressions.Match> 類別的兩個屬性會傳回集合物件：  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName> 屬性會傳回 <xref:System.Text.RegularExpressions.GroupCollection> 物件，其中包含符合規則運算式模式中之擷取群組的子字串相關資訊。  
  
-   `Match.Captures` 屬性會傳回用法受限的 <xref:System.Text.RegularExpressions.CaptureCollection> 物件。 針對 <xref:System.Text.RegularExpressions.Match> 屬性為 `Success` 的 `false` 物件，不會填入集合。 否則，就會包含具有與 <xref:System.Text.RegularExpressions.Capture> 物件相同資訊的單一 <xref:System.Text.RegularExpressions.Match> 物件。  
  
 如需這些物件的詳細資訊，請參閱本主題稍後的[群組集合](#GroupCollection)和[擷取集合](#CaptureCollection)一節。  
  
 <xref:System.Text.RegularExpressions.Match> 類別的兩個其他屬性會提供比對的相關資訊。`Match.Value` 屬性會傳回輸入字串中，符合規則運算式模式的子字串。`Match.Index` 屬性會傳回輸入字串中相符字串以零起始的開始位置。  
  
 <xref:System.Text.RegularExpressions.Match> 類別也有兩個模式比對方法：  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> 方法會尋找目前 <xref:System.Text.RegularExpressions.Match> 物件代表之相符項目後面的相符項目，並傳回代表該相符項目的 <xref:System.Text.RegularExpressions.Match> 物件。  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> 方法會在相符字串上執行指定的取代作業，並傳回結果。  
  
 下列範例會使用 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> 方法，在包含兩個小數位數的每個數字前面，加上 $ 符號和空格。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 規則運算式模式 `\b\d+(,\d{3})*\.\d{2}\b` 的定義如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`\b`|開始字緣比對。|  
|`\d+`|比對一個或多個十進位數字。|  
|`(,\d{3})*`|比對後面接三個十進位數字的零或多個逗號。|  
|`\.`|比對小數點字元。|  
|`\d{2}`|比對兩個十進位數字。|  
|`\b`|結束字緣比對。|  
  
 取代模式 `$$ $&` 指出相符的子字串應取代為貨幣符號 \($\) \(`$$` 模式\)、空格和相符項的值 \(`$&` 模式\)。  
  
 [回到頁首](#introduction)  
  
<a name="GroupCollection"></a>   
## 群組集合  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName> 屬性會傳回 <xref:System.Text.RegularExpressions.GroupCollection> 物件，其中包含單一比對中代表擷取群組的 <xref:System.Text.RegularExpressions.Group> 物件。 集合中的第一個 <xref:System.Text.RegularExpressions.Group> 物件 \(索引位置為 0\) 代表整個比對。 後面接續的每個物件各代表單一擷取群組的結果。  
  
 您可以使用 <xref:System.Text.RegularExpressions.Group> 屬性，擷取集合中的個別 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=fullName> 物件。 您可以依集合中的序數位置來擷取未具名群組，以及依名稱或依序數位置來擷取具名群組。 未具名擷取會先出現在集合中，並依其出現在規則運算式模式中的順序，由左至右編排索引。 具名擷取的索引會依其出現在規則運算式模式中的順序，由左至右編排在未具名擷取之後。 若要判定特定規則運算式比對方法傳回的集合中，有哪些編號群組可用，您可以呼叫執行個體 <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=fullName> 方法。 若要判定集合中有哪些具名群組可用，您可以呼叫執行個體 <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=fullName> 方法。 在用來分析任何規則運算式找到之相符項目的一般用途常式中，這兩種方法都特別好用。  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=fullName> 屬性在 C\# 是集合的索引子，在 Visual Basic 中是集合物件的預設屬性。 這表示，可以依索引 \(若為具名群組，可依名稱\) 來存取個別 <xref:System.Text.RegularExpressions.Group> 物件，如下所示：  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 下列範例定義的規則運算式會使用群組建構來擷取日期的月、日和年。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 規則運算式模式 `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` 的定義如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`\b`|開始字緣比對。|  
|`(\w+)`|比對一個或多個文字字元。 這是第一個擷取群組。|  
|`\s`|比對空白字元。|  
|`(\d{1,2})`|比對一個或兩個十進位數字。 這是第二個擷取群組。|  
|`,`|比對逗號。|  
|`\s`|比對空白字元。|  
|`(\d{4})`|比對四個十進位數字。 這是第三個擷取群組。|  
|`\b`|結束字邊界比對。|  
  
 [回到頁首](#introduction)  
  
<a name="the_captured_group"></a>   
## 擷取群組  
 <xref:System.Text.RegularExpressions.Group> 類別代表單一擷取群組的結果。<xref:System.Text.RegularExpressions.GroupCollection.Item%2A> 屬性傳回之 <xref:System.Text.RegularExpressions.GroupCollection> 物件的 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName> 屬性，會傳回代表規則運算式中定義之擷取群組的群組物件。<xref:System.Text.RegularExpressions.GroupCollection.Item%2A> 屬性是 <xref:System.Text.RegularExpressions.Group> 類別的索引子 \(在 C\# 中\) 及預設屬性 \(在 Visual Basic 中\)。 您也可以使用 `foreach` 或 `For``Each` 建構，逐一查看集合來擷取個別成員。 如需範例，請參閱上一節。  
  
 下列範例會使用巢狀群組建構，將子字串擷取至群組中。 規則運算式模式 `(a(b))c` 會相符字串 "abc"。 它會將子字串 "ab" 指派給第一個擷取群組，並將子字串 "b" 指派給第二個擷取群組。  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 下列範例會使用具名群組建構，從包含 "DATANAME:VALUE" 格式 \(規則運算式會在冒號 \(:\) 處分割\) 資料的字串擷取子字串。  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 規則運算式模式 `^(?<name>\w+):(?<value>\w+)` 的定義如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`^`|在輸入字串的開頭開始比對。|  
|`(?<name>\w+)`|比對一個或多個文字字元。 此擷取群組的名稱為 `name`。|  
|`:`|比對冒號。|  
|`(?<value>\w+)`|比對一個或多個文字字元。 此擷取群組的名稱為 `value`。|  
  
 <xref:System.Text.RegularExpressions.Group> 類別的屬性會提供擷取群組的相關資訊：`Group.Value` 屬性包含擷取的子字串，`Group.Index` 屬性會指出擷取群組在輸入文字中的開始位置，`Group.Length` 屬性包含擷取文字的長度，而 `Group.Success` 屬性會指出子字串是否符合擷取群組所定義的模式。  
  
 將數量詞套用至群組 \(如需詳細資訊，請參閱 [數量詞](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)\) 修改每個擷取群組各一個擷取的關聯性，有兩種方式：  
  
-   如果將 `*` 或 `*?` 數量詞 \(可指定零或多個相符項目\) 套用至群組，擷取群組在輸入字串中可會沒有相符項目。 沒有擷取文字時，<xref:System.Text.RegularExpressions.Group> 物件的屬性會設定如下表所示。  
  
    |群組屬性|值|  
    |----------|-------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=fullName>|  
    |`Length`|0|  
  
     下列範例提供一個實例。 在規則運算式模式 `aaa(bbb)*ccc` 中，第一個擷取群組 \(子字串 "bbb"\) 可比對零或多次。 因為輸入字串 "aaaccc" 符合模式，所以擷取群組沒有相符項目。  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   數量詞可以比對多次出現的擷取群組定義的模式。 在此情況下，`Value` 物件的 `Length` 和 <xref:System.Text.RegularExpressions.Group> 屬性只包含最後擷取之子字串的相關資訊。 例如，下列規則運算式會比對以句點結尾的單一句子。 其使用兩個群組建構：第一個群組建構會擷取個別文字和空格字元，第二個群組建構會擷取個別文字。 如範例輸出所示，雖然規則運算式成功擷取了整個句子，但是第二個擷取群組只擷取了最後一個字。  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [回到頁首](#introduction)  
  
<a name="CaptureCollection"></a>   
## 擷取集合  
 <xref:System.Text.RegularExpressions.Group> 物件只包含最後一個擷取的相關資訊。 不過，您仍可從 <xref:System.Text.RegularExpressions.CaptureCollection> 屬性傳回的 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=fullName> 物件，取得擷取群組所建立的一整組擷取。 集合的每個成員都是 <xref:System.Text.RegularExpressions.Capture> 物件，代表擷取群組所建立的擷取，並依照擷取的順序排列 \(因此，順序為在輸入字串中比對擷取群組的順序，由左至右排列\)。 您可以從集合擷取個別 <xref:System.Text.RegularExpressions.Capture> 物件，有兩種方式：  
  
-   使用 `foreach` \(在 C\# 中\) 或 `For``Each` \(在 Visual Basic 中\) 之類的建構逐一查看集合。  
  
-   使用 <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=fullName> 屬性，依索引擷取特定物件。<xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> 屬性是 <xref:System.Text.RegularExpressions.CaptureCollection> 物件的預設屬性 \(在 Visual Basic 中\) 或索引子 \(在 C\# 中\)。  
  
 如果沒有將數量詞套用至擷取群組，則 <xref:System.Text.RegularExpressions.CaptureCollection> 物件會包含單一較無用處的 <xref:System.Text.RegularExpressions.Capture> 物件，因為其提供與其 <xref:System.Text.RegularExpressions.Group> 物件相同之相符項目的相關資訊。 如果將數量詞套用至擷取群組，則 <xref:System.Text.RegularExpressions.CaptureCollection> 物件包含擷取群組建立的所有擷取，而集合的最後一個成員代表與 <xref:System.Text.RegularExpressions.Group> 物件相同的擷取。  
  
 例如，如果您使用規則運算式模式 `((a(b))c)+` \(其中 \+ 數量詞指定一或多個比對\)，以從字串 "abcabcabc" 擷取相符項目，則每個 <xref:System.Text.RegularExpressions.CaptureCollection> 物件的 <xref:System.Text.RegularExpressions.Group> 物件各包含三個成員。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 下列範例使用規則運算式 `(Abc)+`，在字串 "XYZAbcAbcAbcXYZAbcAb" 中尋找一或多次連續執行的字串 "Abc"。 此範例說明如何使用 <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=fullName> 屬性來傳回多個擷取子字串群組。  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [回到頁首](#introduction)  
  
<a name="the_individual_capture"></a>   
## 個別擷取  
 <xref:System.Text.RegularExpressions.Capture> 類別包含單一子運算式擷取的結果。<xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=fullName> 屬性包含相符的文字，而 <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=fullName> 屬性指出輸入字串中以零起始的位置，也就是相符的子字串開始的位置。  
  
 下列範例會針對所選城市的氣溫剖析輸入字串。 逗號 \(","\) 用來分隔城市及其氣溫，而分號 \(";"\) 用來分隔每個城市的資料。 整個輸入字串代表單一比對。 在規則運算式模式 `((\w+(\s\w+)*),(\d+);)+` \(用來剖析字串\) 中，城市名稱指派給第二個擷取群組，而氣溫指派給第四個擷取群組。  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 規則運算式的定義如下表所示。  
  
|模式|描述|  
|--------|--------|  
|`\w+`|比對一個或多個文字字元。|  
|`(\s\w+)*`|比對出現零或多次、後接一或多個文字字元的空格字元。 此模式會比對多字的城市名稱。 這是第三個擷取群組。|  
|`(\w+(\s\w+)*)`|比對一或多個文字字元，其後面接出現零或多次的空格字元，以及一或多個文字字元。 這是第二個擷取群組。|  
|`,`|比對逗號。|  
|`(\d+)`|比對一或多個數字。 這是第四個擷取群組。|  
|`;`|比對分號。|  
|`((\w+(\s\w+)*),(\d+);)+`|一或多次比對文字的模式，該文字後面接任何其他文字，後面再接逗號、一或多個數字和分號。 這是第一個擷取群組。|  
  
## 請參閱  
 <xref:System.Text.RegularExpressions>   
 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)   
 [規則運算式語言 \- 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)