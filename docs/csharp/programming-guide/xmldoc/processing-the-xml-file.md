---
title: "處理 XML 檔案 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML [C#], 處理"
  - "XML 處理 [C#]"
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 處理 XML 檔案 (C# 程式設計手冊)
編譯器會為每一個加上標記的程式碼的建構產生一個 ID 字串，用來產生文件   \(如需將程式碼加上標記的詳細資訊，請參閱[建議的文件註解標記](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)\)。 ID 字串會將建構獨一無二地識別出來。  處理 XML 檔案的程式可以使用 ID 字串來識別文件也適用之 .NET Framework 中對應的中繼資料\/反映項目。  
  
 XML 檔案並不是程式碼的階層架構表示，它是一個平面圖式的清單，其中每個項目都有一個 ID。  
  
 在產生 ID 字串時，編譯器會遵守下列的規則：  
  
-   字串中不能有空白。  
  
-   ID 字串的第一個部分 \(單一字元後接著一個分號\) 識別了成員的種類。  下面是使用的成員型別：  
  
    |字元|描述|  
    |--------|--------|  
    |N|namespace<br /><br /> 您不能將文件註解加入命名空間裡，但是可以讓 cref 參考這些文件註解 \(如果有支援這項功能\)|  
    |T|型別：類別、介面、結構、列舉、委派|  
    |F|欄位|  
    |P|屬性 \(包括索引工具或其他索引屬性\)|  
    |M|方法 \(包括如建構函式、運算子等特別的方法\)|  
    |E|event|  
    |\!|錯誤字串<br /><br /> 字串的其餘部分會提供該錯誤的相關資訊。  C\# 編譯器對於無法解析的連結會產生錯誤資訊|  
  
-   字串的第二個部分是該項目的完整名稱 \(開始於命名空間的根\)。  該項目的名稱、它的封入型別以及命名空間由句號分開。  若該項目的名稱本身含有句號，則句號會被井字號 \(\#\) 所替換。  一般假設在項目名稱中不會直接出現井字號 \(\#\)。  例如，字串建構函式的完整名稱為 "System.String.\#ctor"。  
  
-   對於屬性和方法，若方法有引數，則後面會接著由括號括起來的引數清單。  如果沒有引數，就不會有括弧出現。  引數間是以逗號來分隔。  每個引數的編碼直接遵照 .NET Framework 簽章中的編碼方式：  
  
    -   基底型別。  標準型別 \(ELEMENT\_TYPE\_CLASS 或 ELEMENT\_TYPE\_VALUETYPE\) 以該型別的完整名稱表示。  
  
    -   內建型別 \(例如，ELEMENT\_TYPE\_I4、ELEMENT\_TYPE\_OBJECT、ELEMENT\_TYPE\_STRING、ELEMENT\_TYPE\_TYPEDBYREF。  和 ELEMENT\_TYPE\_VOID\) 表示為對應之完整型別的完整名稱。  例如，System.Int32 或 System.TypedReference。  
  
    -   ELEMENT\_TYPE\_PTR 於修改的型別後以 '\*' 表示。  
  
    -   ELEMENT\_TYPE\_BYREF 於修改的型別後以 '@' 表示。  
  
    -   ELEMENT\_TYPE\_PINNED 於修改的型別後以 '^' 表示。  C\# 編譯器永遠不會產生這個。  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ 於修改的型別後以 '&#124;' 和修飾詞類別的完整名稱表示。  C\# 編譯器永遠不會產生這個。  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT 於修改的型別後以 '\!' 和修飾詞類別的完整名稱表示。  
  
    -   ELEMENT\_TYPE\_SZARRAY 在陣列的項目型別後以 "\[\]" 表示。  
  
    -   ELEMENT\_TYPE\_GENERICARRAY 在陣列的項目型別後以 "\[?\]" 表示。  C\# 編譯器永遠不會產生這個。  
  
    -   ELEMENT\_TYPE\_ARRAY 以 \[*lowerbound*:`size`，*lowerbound*:`size`\] 表示，其中逗號的數目為陣序規範 \-1，若已知每個維度的下限與大小，則以十進位表示。  若沒有指定下限或大小，則會被忽略。  若省略了特定維度的下限及大小，則 ":" 也會被省略。  例如，一個沒有指定大小的二維陣列的下限是 1，則會以 \[1:,1:\] 表示。  
  
    -   ELEMENT\_TYPE\_FNPTR 以「\=FUNC:`type`\(*signature*\)」表示，其中 `type` 為傳回型別，而 *signature* 為方法的引數。  如果沒有引數的話，就會省略括弧。  C\# 編譯器永遠不會產生這個。  
  
     將不顯示下列的簽章元件，因為它們從不用來區分多載的方法。  
  
    -   呼叫慣例  
  
    -   傳回型別  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   方法的傳回值僅會對轉換運算子 \(op\_Implicit 和 op\_Explicit\) 編碼成 '~' 後面接傳回型別，如同上述的編碼一樣。  
  
-   泛型型別的名稱後面會有一個反勾號，然後是表示泛型型別參數數目的數字。  例如：  
  
     `<member name="T:SampleClass`2">` 是定義為 `public class SampleClass\<T, U>` 之型別的標記。  
  
     若為使用泛型型別做為參數的方法，會將泛型型別參數指定為前面加上反勾號的數字 \(例如 \`0、\`1\)。  每個數字都代表型別泛型參數以零起始的陣列。  
  
## 範例  
 下面的範例說明了類別與其成員的 ID 字串如何產生：  
  
 [!code-cs[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/processing-the-xml-file_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)