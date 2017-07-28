---
title: "Imports 陳述式 （XML 命名空間） |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImportsXmlns
dev_langs:
- VB
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 546168994973d19336f86f4b4e9ec566f0b9dd91
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="imports-statement-xml-namespace"></a>Imports 陳述式 (XML 命名空間)
匯入 XML 命名空間前置詞，以用於 XML 常值和 XML 軸屬性。  
  
## <a name="syntax"></a>語法  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>組件  
 `xmlNamespacePrefix`  
 選擇項。 字串的 xml 項目和屬性可以參考`xmlNamespaceName`。 如果沒有`xmlNamespacePrefix`是提供，匯入的 XML 命名空間是預設 XML 命名空間。 必須是有效的 XML 識別碼。 如需詳細資訊，請參閱[名稱的宣告 XML 元素和屬性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。  
  
 `xmlNamespaceName`  
 必要項。 識別要匯入的 XML 命名空間的字串。  
  
## <a name="remarks"></a>備註  
 您可以使用`Imports`陳述式來定義通用的 XML 命名空間，您可以使用 XML 常值和 XML 軸屬性，或是做為參數傳遞至`GetXmlNamespace`運算子。 (如需使用`Imports`陳述式來匯入別名可用，您的程式碼中使用的型別名稱，請參閱[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。)宣告 XML 命名空間使用的語法`Imports`陳述式是用於 XML 的語法相同。 因此，您可以從 XML 檔案複製命名空間宣告，並且將它用於`Imports`陳述式。  
  
 當您想要重複地建立會從相同的命名空間的 XML 項目時，適合使用 XML 命名空間前置詞。 宣告 XML 命名空間前置詞`Imports`陳述式是全域的會提供給所有的程式碼檔案中。 當您建立 XML 項目常值和 XML 軸屬性的存取時，您可以使用它。 如需詳細資訊，請參閱[XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和[XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。  
  
 如果您定義不含命名空間前置詞的全域 XML 命名空間 (例如， `Imports <xmlns="http://SomeNameSpace>"`)，該命名空間會被視為預設 XML 命名空間。 預設 XML 命名空間用於任何 XML 項目常值或未明確指定命名空間的 XML 屬性軸屬性。 如果指定的命名空間是空白的命名空間，也會使用預設命名空間 (也就是`xmlns=""`)。 XML 常值中的 XML 屬性或沒有命名空間的 XML 屬性軸屬性不會套用預設 XML 命名空間。  
  
 XML 命名空間定義在 XML 常值，稱為*本機 XML 命名空間*，XML 命名空間所定義的優先順序高於`Imports`為全域的陳述式。 XML 命名空間所定義的`Imports`陳述式的優先順序高於 Visual Basic 專案匯入的 XML 命名空間。 如果 XML 常值定義的 XML 命名空間，該區域的命名空間不適用於內嵌的運算式。  
  
 全域 XML 命名空間遵循.NET Framework 命名空間相同的限制範圍與定義規則。 如此一來，您可以包含`Imports`陳述式來定義通用的 XML 命名空間任何位置匯入的.NET Framework 命名空間。 這包括程式碼檔案和專案層級匯入的命名空間。 專案層級匯入的命名空間的相關資訊，請參閱[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)。  
  
 每個原始程式檔可以包含任意數目的`Imports`陳述式。 這些必須遵循選項的宣告，例如`Option Strict`陳述式，而且前面必須加上程式設計項目宣告，例如`Module`或`Class`陳述式。  
  
## <a name="example"></a>範例  
 下列範例會匯入預設 XML 命名空間和 XML 命名空間前置詞用來識別`ns`。 然後，它會建立使用這兩個命名空間的 XML 常值。  
  
 [!code-vb[VbXMLSamples #&45;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>範例  
 下列範例會匯入 XML 命名空間前置詞`ns`。 然後，它會建立 XML 常值，會使用命名空間前置詞，並顯示項目的最終格式。  
  
 [!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 請注意，編譯器轉換 XML 命名空間前置詞從通用的前置詞為本機的前置詞定義。  
  
## <a name="example"></a>範例  
 下列範例會匯入 XML 命名空間前置詞`ns`。 然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。  
  
 [!code-vb[VbXMLSamples #&19;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>另請參閱  
 [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [GetXmlNamespace 運算子](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
