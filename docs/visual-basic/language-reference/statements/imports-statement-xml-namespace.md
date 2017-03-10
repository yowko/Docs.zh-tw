---
title: "Imports Statement (XML Namespace) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ImportsXmlns"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML namespace [Visual Basic], importing"
  - "imports [Visual Basic]"
  - "Imports statement [Visual Basic]"
  - "namespaces [Visual Basic], importing"
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Imports Statement (XML Namespace)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

匯入 XML 命名空間前置字元以用於 XML 常值 \(Literal\) 和 XML 軸屬性。  
  
## 語法  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## 組件  
 `xmlNamespacePrefix`  
 選擇項。  XML 項目和屬性 \(Attribute\) 可藉以參考 `xmlNamespaceName` 的字串。  如果未提供 `xmlNamespacePrefix`，匯入的 XML 命名空間 \(Namespace\) 即是預設的 XML 命名空間。  必須是有效的 XML 識別項。  如需詳細資訊，請參閱 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。  
  
 `xmlNamespaceName`  
 必要項。  用於識別要匯入之 XML 命名空間的字串。  
  
## 備註  
 您可以使用 `Imports` 陳述式 \(Statement\) 定義全域 XML 命名空間，您可以將該命名空間與 XML 常值和 XML 軸屬性搭配使用，或做為參數傳遞至 `GetXmlNamespace` 運算子   \(如需使用 `Imports` 陳述式匯入可以在程式碼中使用型別名稱之位置使用的別名 \(Alias\) 的詳細資訊，請參閱[Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)\)。 使用 `Imports` 陳述式宣告 XML 命名空間的語法與 XML 中使用的語法相同。  因此，您可以從 XML 檔案複製命名空間宣告並且用在 `Imports` 陳述式中。  
  
 您要從相同的命名空間重複建立 XML 項目時，XML 命名空間前置字元相當有用。  與 `Imports` 陳述式一起宣告的 XML 命名空間前置字元是全域的，因為它可供檔案中的所有程式碼使用。  您可以在建立 XML 項目常值以及存取 XML 軸屬性時使用。  如需詳細資訊，請參閱 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。  
  
 如果您定義的全域 XML 命名空間不具有命名空間前置字元 \(例如 `Imports <xmlns="http://SomeNameSpace>"`\)，該命名空間會被視為預設 XML 命名空間。  預設 XML 命名空間是用於未明確指定命名空間的任何 XML 項目常值或 XML 屬性 \(Attribute\) 軸屬性 \(Property\)。  如果指定的命名空間是空的命名空間 \(也就是 `xmlns=""`\)，此時也會使用預設命名空間。  預設 XML 命名空間不會套用至 XML 常值中的 XML 屬性 \(Attribute\)，或沒有命名空間的 XML 屬性 \(Attribute\) 軸屬性 \(Property\)。  
  
 XML 常值中定義的 XML 命名空間，稱為「*本機 XML 命名空間*」\(Local XML Namespace\)，其優先順序高於 `Imports` 陳述式定義為全域的 XML 命名空間。  `Imports` 陳述式定義的 XML 命名空間，其優先順序高於 Visual Basic 專案所匯入的 XML 命名空間。  如果 XML 常值定義某個 XML 命名空間，該本機命名空間不會套用至內嵌運算式。  
  
 全域 XML 命名空間會遵照與 .NET Framework 命名空間相同的範圍和定義規則。  因此，您可以包含 `Imports` 陳述式，在可以匯入 .NET Framework 命名空間的任何位置定義全域 XML 命名空間。  這同時包含程式碼檔案和專案層級匯入命名空間。  如需專案層級匯入命名空間的詳細資訊，請參閱[專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)。  
  
 每個原始程式檔 \(Source File\) 都能包含任何數目的 `Imports` 陳述式。  這些陳述式必須在選項宣告之後 \(例如 `Option Strict` 陳述式\)，而且它們必須在程式設計項目宣告之前 \(例如 `Module` 或 `Class` 陳述式\)。  
  
## 範例  
 下列範例會匯入預設 XML 命名空間和以前置字元 `ns` 識別的 XML 命名空間。  然後建立同時使用這兩個命名空間的 XML 常值。  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/imports-statement-xml-na_1.vb)]  
  
 這個程式碼會顯示下列文字：  
  
```  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## 範例  
 下列範例會匯入 XML 命名空間前置字元 `ns`。  然後建立使用命名空間前置字元的 XML 常值，並且顯示項目的最終格式。  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/imports-statement-xml-na_2.vb)]  
  
 這個程式碼會顯示下列文字：  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 請注意，編譯器 \(Compiler\) 會將 XML 命名空間前置字元從全域前置字元轉換為本機前置字元定義。  
  
## 範例  
 下列範例會匯入 XML 命名空間前置字元 `ns`。  然後使用這個命名空間前置字元建立 XML 常值，並以限定名稱 `ns:name` 存取第一個子節點。  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/imports-statement-xml-na_3.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Patrick Hines`  
  
## 請參閱  
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [GetXmlNamespace Operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)