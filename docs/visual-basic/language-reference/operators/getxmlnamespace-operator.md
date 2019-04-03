---
title: GetXmlNamespace 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 757ca54e5ba370bf2cc48bc70499e7b43ec96ef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834747"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 運算子 (Visual Basic)
取得<xref:System.Xml.Linq.XNamespace>對應至指定的 XML 命名空間前置詞的物件。  
  
## <a name="syntax"></a>語法  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>組件  
 `xmlNamespacePrefix`  
 選擇性。 識別 XML 命名空間前置詞的字串。 如果提供，這個字串必須是有效的 XML 識別項。 如需詳細資訊，請參閱 <<c0> [ 名稱的宣告 XML 元素和屬性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。 如果未不指定任何前置詞，則會傳回預設的命名空間。 如果未不指定任何預設命名空間，則會傳回空的命名空間。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XNamespace> XML 命名空間前置詞對應的物件。  
  
## <a name="remarks"></a>備註  
 `GetXmlNamespace`運算子取得<xref:System.Xml.Linq.XNamespace>物件，對應至 XML 命名空間前置詞`xmlNamespacePrefix`。  
  
 您可以使用 XML 命名空間前置詞，直接在 XML 常值和 XML 軸屬性。 不過，您必須使用`GetXmlNamespace`運算子，將轉換的命名空間前置詞<xref:System.Xml.Linq.XNamespace>物件，才能用於您的程式碼。 您可以將附加至未限定的項目名稱<xref:System.Xml.Linq.XNamespace>以取得完整限定的物件<xref:System.Xml.Linq.XName>物件，哪一個多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]方法都需要。  
  
## <a name="example"></a>範例  
 下列範例會匯入`ns`作為 XML 命名空間前置詞。 然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定的名稱的第一個子節點`ns:phone`。 接著，將該子節點`ShowName`藉由建構限定的名稱的副程式`GetXmlNamespace`運算子。 `ShowName`副程式接著會將傳遞的限定的名稱<xref:System.Xml.Linq.XNode.Ancestors%2A>方法來取得父代`ns:contact`節點。  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 當您呼叫`TestGetXmlNamespace.RunSample()`，它會顯示訊息方塊包含下列文字：  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [在 Visual Basic 中存取 XML](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
