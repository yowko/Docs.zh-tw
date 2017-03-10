---
title: "如何：使用 XML 文件功能 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML 文件 [C#]"
  - "C# 語言，XML 文件功能"
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 如何：使用 XML 文件功能 (C# 程式設計手冊)
下列範例提供的型別，已記錄的基本概觀。  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/how-to-use-the-xml-docum_1.cs)]  
  
 **上述程式碼範例產生這個.xml 檔案。**  
**\<？ xml 版本 ="1.0"？>**  
**\< 文件>**  
 **\< 組件>**  
 **\< 名稱>xmlsample \< / 名稱>**  
 **\< / 組件>**  
 **\< 成員>**  
 **\< 成員名稱 ="T:SomeClass">**  
 **\< 摘要>**  
 **在類別層級摘要文件。 \< / 摘要>**  
 **\< 註解>**  
 **較長的註解可與型別或成員相關聯**   
 **註解標記 \< / 註解>**  
 **\< / 成員>**  
 **\< 成員 name="F:SomeClass.m_Name 」>**  
 **\< 摘要>**  
 **Name 屬性存放區 \< / 摘要>**  
 **\< / 成員>**  
 **\< 成員名稱 ="M:SomeClass.#ctor 」>**  
 **\< 摘要>類別建構函式。 \< / 摘要>**   
 **\< / 成員>**  
 **\< 成員 name="M:SomeClass.SomeMethod(System.String) 」>**  
 **\< 摘要>**  
 **描述 SomeMethod。 \< / 摘要>**  
 **\< 參數名稱 ="s"> 此處參數描述 s \< / 參數>**  
 **\< seealso cref="T:System.String 」>**  
 **您可以任何標記上使用 cref 屬性來參考型別或成員**   
 **然後編譯器會檢查這個參考存在。\< / seealso>**  
 **\< / 成員>**  
 **\< 成員 name="M:SomeClass.SomeOtherMethod 」>**  
 **\< 摘要>**  
 **其他方法。\< / 摘要>**  
 **\< 傳回>**  
 **傳回說明結果透過傳回標記。 \< />**  
 **\< seealso cref="M:SomeClass.SomeMethod(System.String) 」>**  
 **請注意，cref 屬性來參考特定的方法使用 \< / seealso>**  
 **\< / 成員>**  
 **\< 成員 name="M:SomeClass.Main(System.String[]) 」>**  
 **\< 摘要>**  
 **應用程式的進入點。**  
 **\< / 摘要>**  
 **\< 參數名稱 ="args"> 命令列引數清單 \< / 參數>**  
 **\< / 成員>**  
 **\< 成員 name="P:SomeClass.Name 」>**  
 **\< 摘要>**  
 **Name 屬性 \< / 摘要>**  
 **\< 值>**  
 **值的標記用來描述屬性的值 \< / v>**  
 **\< / 成員>**  
 **\< / 成員>**  
**\< / 文件>**   
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯範例，請輸入下列命令列︰  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 這會建立 XML 檔案 XMLsample.xml，您可以檢視您的瀏覽器中或使用 TYPE 命令。  
  
## <a name="robust-programming"></a>穩固程式設計  
 / / 開始 XML 文件。 當您建立新的專案時，精靈放入一些入門的 / / 行中。 處理這些註解有一些限制︰  
  
-   文件必須格式正確 XML。 如果 XML 格式不正確，則會產生警告，且文件檔案會包含註解，指出發生錯誤。  
  
-   開發人員可以自由建立自己的標記集合。 沒有一組建議的標記 （請參閱進一步閱讀 > 章節）。 有些建議的標記有特殊意義︰  
  
    -   \< Param> 標記用來描述參數。 如果使用，則編譯器會驗證參數存在，並且所有的參數會在文件中描述。 如果驗證失敗，編譯器會發出警告。  
  
    -    `cref` 屬性可以附加至任何標記以提供程式碼項目的參考。 編譯器會驗證此程式碼項目存在。 如果驗證失敗，編譯器會發出警告。 編譯器會遵守任何 `using` 陳述式中所述的型別尋找時 `cref` 屬性。  
  
    -   \< 摘要> 標籤用 Visual Studio 中的 IntelliSense 來顯示型別或成員的其他資訊。  
  
        > [!NOTE]
        >  XML 檔案並不提供型別和成員的完整資訊 （例如，不含任何型別資訊）。 若要取得型別或成員的完整資訊，文件檔案必須搭配反映實際型別或成員。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [/doc （C# 編譯器選項）](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)