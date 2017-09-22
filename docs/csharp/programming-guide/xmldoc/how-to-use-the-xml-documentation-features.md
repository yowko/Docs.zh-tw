---
title: "如何：使用 XML 文件功能 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eeee77db523bc0ad97f425d4ba8076ae5740dfe8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>如何：使用 XML 文件功能 (C# 程式設計手冊)
下列範例提供已記載之類型的基本概觀。  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **// 此 .xml 檔案是透過上述程式碼範例所產生。**  
**\<?xml version="1.0"?>**  
**\<doc>**  
 **\<assembly>**  
 **\<name>xmlsample\</name>**  
 **\</assembly>**  
 **\<members>**  
 **\<member name="T:SomeClass">**  
 **\<summary>**  
 **類別層級摘要文件在此處出現。\</summary>**  
 **\<remarks>**  
 **可以將較長的註解經由備註標記**   
 **和類型或成員產生關聯\</remarks>**  
 **\</member>**  
 **\<member name="F:SomeClass.m_Name">**  
 **\<summary>**  
 **Name 屬性的存放區\</summary>**  
 **\</member>**  
 **\<member name="M:SomeClass.#ctor">**  
 **\<summary>類別建構函式。\</summary>**   
 **\</member>**  
 **\<member name="M:SomeClass.SomeMethod(System.String)">**  
 **\<summary>**  
 **SomeMethod 的描述。\</summary>**  
 **\<param name="s"> s 的參數描述在此處出現\</param>**  
 **\<seealso cref="T:System.String">**  
 **您可以使用任何標記上的 cref 屬性來參考類型或成員**   
 **而編譯器會檢查這個參考是否存在。\</seealso>**  
 **\</member>**  
 **\<member name="M:SomeClass.SomeOtherMethod">**  
 **\<summary>**  
 **一些其他方法。\</summary>**  
 **\<returns>**  
 **傳回結果是透過傳回標記描述。\</returns>**  
 **\<seealso cref="M:SomeClass.SomeMethod(System.String)">**  
 **請注意使用 cref 屬性來參考特定的方法 \</seealso>**  
 **\</member>**  
 **\<member name="M:SomeClass.Main(System.String[])">**  
 **\<summary>**  
 **應用程式的進入點。**  
 **\</summary>**  
 **\<param name="args"> 命令列引數清單\</param>**  
 **\</member>**  
 **\<member name="P:SomeClass.Name">**  
 **\<summary>**  
 **Name 屬性 \</summary>**  
 **\<value>**  
 **值的標記被用來描述這個屬性值\</value>**  
 **\</member>**  
 **\</members>**  
**\</doc>**   
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯範例，請輸入下列命令列：  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 這會建立 XML 檔案 XMLsample.xml，您可以在瀏覽器中或使用 TYPE 命令進行檢視。  
  
## <a name="robust-programming"></a>穩固程式設計  
 XML 文件是以 /// 開頭。 當您建立新的專案時，精靈會為您在開頭放入幾行 ///。 這些註解在處理時有一些限制：  
  
-   文件必須是語式正確的 XML。 如果 XML 的語式不正確，則會產生警告，而且文件檔案會包含註解，指出發生錯誤。  
  
-   開發人員可以自由建立自己的標記集合。 有建議的標記集合 (請參閱＜進一步閱讀＞一節)。 其中一些建議的標記具有特殊意義：  
  
    -   \<param> 標記是用來描述參數。 如果使用，編譯器會驗證參數存在，而且所有參數在文件中都有描述。 如果驗證失敗，編譯器會發出警告。  
  
    -   `cref` 屬性可以附加至任何標記，以提供程式碼項目的參考。 編譯器會驗證此程式碼項目存在。 如果驗證失敗，編譯器會發出警告。 編譯器在尋找 `cref` 屬性中所述的類型時，會遵守任何 `using` 陳述式。  
  
    -   Visual Studio 中的 IntelliSense 使用 \<summary> 標記來顯示類型或成員的其他資訊。  
  
        > [!NOTE]
        >  XML 檔案不會提供類型和成員的完整資訊 (例如，它不會包含任何類型資訊)。 若要取得類型或成員的完整資訊，文件檔案在使用時必須能夠反映實際類型或成員。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [/doc (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

