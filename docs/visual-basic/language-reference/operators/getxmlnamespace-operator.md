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
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592159"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 運算子 (Visual Basic)
取得對應至指定 XML 命名空間前置詞的 <xref:System.Xml.Linq.XNamespace> 物件。  
  
## <a name="syntax"></a>語法  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>組件  
 `xmlNamespacePrefix`  
 選擇性。 識別 XML 命名空間前置詞的字串。 如果提供，此字串必須是有效的 XML 識別碼。 如需詳細資訊，請參閱宣告[的 XML 元素和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。 如果沒有指定前置詞，則會傳回預設命名空間。 如果未指定預設命名空間，則會傳回空的命名空間。  
  
## <a name="return-value"></a>傳回值  
 對應至 XML 命名空間前置詞的 <xref:System.Xml.Linq.XNamespace> 物件。  
  
## <a name="remarks"></a>備註  
 @No__t-0 運算子會取得對應至 XML 命名空間前置詞 `xmlNamespacePrefix` 的 <xref:System.Xml.Linq.XNamespace> 物件。  
  
 您可以直接在 XML 常值和 XML 軸屬性中使用 XML 命名空間前置詞。 不過，您必須使用 `GetXmlNamespace` 運算子，將命名空間前置詞轉換成 @no__t 1 物件，然後才能在程式碼中使用它。 您可以將不合格的專案名稱附加至 @no__t 0 物件，以取得完整的 @no__t 1 物件，而這需要許多 @no__t 2 方法。  
  
## <a name="example"></a>範例  
 下列範例會將 `ns` 匯入為 XML 命名空間前置詞。 然後，它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱 `ns:phone` 的第一個子節點。 然後，它會將該子節點傳遞給 `ShowName` 副程式，這會使用 `GetXmlNamespace` 運算子來構造限定的名稱。 @No__t-0 副程式接著會將限定名稱傳遞給 <xref:System.Xml.Linq.XNode.Ancestors%2A> 方法，以取得父 `ns:contact` 節點。  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 當您呼叫 `TestGetXmlNamespace.RunSample()` 時，它會顯示訊息方塊，其中包含下列文字：  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [在 Visual Basic 中存取 XML](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
