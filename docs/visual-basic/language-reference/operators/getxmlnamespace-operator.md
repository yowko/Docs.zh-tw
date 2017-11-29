---
title: "GetXmlNamespace 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 運算子 (Visual Basic)
取得<xref:System.Xml.Linq.XNamespace>對應至指定的 XML 命名空間前置詞的物件。  
  
## <a name="syntax"></a>語法  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>組件  
 `xmlNamespacePrefix`  
 選擇項。 識別 XML 命名空間前置詞的字串。 如果提供，這個字串必須是有效的 XML 識別項。 如需詳細資訊，請參閱[名稱的宣告 XML 元素和屬性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。 如果指定前置詞，則會傳回預設命名空間。 如果未不指定任何預設命名空間，則會傳回空的命名空間。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XNamespace>對應的 XML 命名空間前置詞的物件。  
  
## <a name="remarks"></a>備註  
 `GetXmlNamespace`運算子取得<xref:System.Xml.Linq.XNamespace>對應的 XML 命名空間前置詞的物件`xmlNamespacePrefix`。  
  
 您可以使用直接在 XML 常值和 XML 軸屬性中的 XML 命名空間前置詞。 不過，您必須使用`GetXmlNamespace`運算子，將轉換的命名空間前置詞<xref:System.Xml.Linq.XNamespace>才能在程式碼中使用的物件。 您可以將附加到不合格的項目名稱<xref:System.Xml.Linq.XNamespace>要取得完整限定物件<xref:System.Xml.Linq.XName>物件、 哪些多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]方法都需要。  
  
## <a name="example"></a>範例  
 下列範例會匯入`ns`當做 XML 命名空間前置詞。 然後它會使用命名空間的前置詞來建立 XML 常值及存取具有限定的名稱的第一個子節點`ns:phone`。 接著，將該子節點`ShowName`建構使用限定的名稱的副程式`GetXmlNamespace`運算子。 `ShowName`副程式然後將傳遞的限定的名稱<xref:System.Xml.Linq.XNode.Ancestors%2A>方法來取得父`ns:contact`節點。  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 當您呼叫`TestGetXmlNamespace.RunSample()`，它會顯示訊息方塊包含下列文字：  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>另請參閱  
 [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [在 Visual Basic 中存取 XML](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
