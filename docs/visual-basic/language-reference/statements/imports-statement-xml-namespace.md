---
title: Imports 陳述式-XML 命名空間 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 97d08113a37477add9d770b0a680c303fe7e3040
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841403"
---
# <a name="imports-statement-xml-namespace"></a>Imports 陳述式 (XML 命名空間)
匯入適用於 XML 常值和 XML 軸屬性的 XML 命名空間前置詞。  
  
## <a name="syntax"></a>語法  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>組件  
 `xmlNamespacePrefix`  
 選擇性。 字串的 xml 項目和屬性可以參考`xmlNamespaceName`。 如果沒有`xmlNamespacePrefix`是提供，匯入的 XML 命名空間是預設 XML 命名空間。 必須是有效的 XML 識別項。 如需詳細資訊，請參閱 <<c0> [ 名稱的宣告 XML 元素和屬性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。  
  
 `xmlNamespaceName`  
 必要項。 識別要匯入的 XML 命名空間的字串。  
  
## <a name="remarks"></a>備註  
 您可以使用`Imports`陳述式來定義通用的 XML 命名空間，您可以使用 XML 常值和 XML 軸屬性，或做為參數傳遞至`GetXmlNamespace`運算子。 (如需有關使用資訊`Imports`陳述式匯入別名可用型別名稱，用於您的程式碼，請參閱[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。)宣告 XML 命名空間所使用的語法`Imports`陳述式是用於 XML 的語法相同。 因此，您可以從 XML 檔案複製命名空間宣告，並將它用於`Imports`陳述式。  
  
 當您想要重複建立來自相同的命名空間的 XML 項目，則 XML 命名空間前置詞會很有用。 使用 XML 命名空間前置詞宣告`Imports`陳述式是全域的因為它可供在檔案中的所有程式碼。 當您建立 XML 元素常值和 XML 軸屬性的存取時，您可以使用它。 如需詳細資訊，請參閱 < [XML 元素常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)並[XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。  
  
 如果您定義不含命名空間前置詞的全域 XML 命名空間 (例如`Imports <xmlns="http://SomeNameSpace>"`)，該命名空間會被視為預設 XML 命名空間。 預設 XML 命名空間用於任何 XML 元素常值或未明確指定命名空間的 XML 屬性軸屬性。 如果指定的命名空間是空的命名空間，也會使用預設命名空間 (也就是`xmlns=""`)。 預設 XML 命名空間不適用於 XML 常值中的 XML 屬性或沒有命名空間的 XML 屬性軸屬性。  
  
 XML 命名空間定義在 XML 常值，稱為*本機的 XML 命名空間*，所定義的 XML 命名空間中的優先順序高於`Imports`為全域的陳述式。 所定義的 XML 命名空間`Imports`陳述式的優先順序高於針對 Visual Basic 專案匯入的 XML 命名空間。 如果 XML 常值定義 XML 命名空間，該區域的命名空間不適用於內嵌的運算式。  
  
 通用的 XML 命名空間會遵循.NET Framework 命名空間相同的限制範圍與定義規則。 如此一來，您可以在其中包含`Imports`陳述式來定義的全域 XML 命名空間任何位置匯入的.NET Framework 命名空間。 這包括程式碼檔案和專案層級匯入的命名空間。 專案層級匯入的命名空間的相關資訊，請參閱[專案設計工具 (Visual Basic)、 參考頁](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。  
  
 每個來源檔案可以包含任意數目的`Imports`陳述式。 這些必須遵循選項的宣告，例如`Option Strict`陳述式，而且它們必須在前面程式設計項目宣告，例如`Module`或`Class`陳述式。  
  
## <a name="example"></a>範例  
 下列範例會匯入預設 XML 命名空間和 XML 命名空間前置詞識別`ns`。 然後，它會建立使用兩個命名空間的 XML 常值。  
  
 [!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]  
  
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
 下列範例會匯入的 XML 命名空間前置詞`ns`。 然後，它會建立 XML 常值，會使用命名空間前置詞，並顯示項目的最終格式。  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 請注意，編譯器轉換 XML 命名空間前置詞從全域首碼做為本機的前置詞定義。  
  
## <a name="example"></a>範例  
 下列範例會匯入的 XML 命名空間前置詞`ns`。 然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 此程式碼顯示下列文字：  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>另請參閱

- [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace 運算子](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
