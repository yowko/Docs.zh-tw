---
title: "在 Visual Basic 中的 XML IntelliSense |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, XML
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
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
ms.openlocfilehash: 8c43db3d2010e4fa92eebeec8a973c50052b1340
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="xml-intellisense-in-visual-basic"></a>Visual Basic 中的 XML IntelliSense
Visual Basic 程式碼編輯器包含提供 XML 結構描述中定義之元素的文字完成的 XML IntelliSense 功能。 如果在您的專案中包含的 XML 結構描述定義 (XSD) 檔案和使用匯入結構描述的目標命名空間`Imports`陳述式，程式碼編輯器中會包含從 XSD 結構描述的項目清單中的 IntelliSense 的有效成員變數<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 下圖顯示 IntelliSense 清單成員的<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
 ![在 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")  
XML IntelliSense  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a>在 Visual Basic 中啟用 XML IntelliSense  
 若要啟用 XML IntelliSense，Visual Basic 中，您必須包含 Visual Basic 專案中的 XSD 結構描述檔案。 您也必須匯入程式碼檔案中的 XSD 結構描述的目標命名空間，使用`Imports`陳述式。 或者，新增的目標命名空間至專案層級命名空間清單使用**參考**Visual Basic 專案設計工具頁面。 如需範例，請參閱[How to︰ 在 Visual Basic 中啟用 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)。 如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)和[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)。  
  
 請注意，預設為您看不見 Visual Basic 專案中的 XSD 結構描述檔案。 您可能必須按一下**顯示所有檔案**按鈕來選取要包含在您的專案中的 XSD 檔案。  
  
### <a name="generating-a-schema-file-schema-inference"></a>產生結構描述檔案 （結構描述推斷）  
 您可以建立 XSD 結構描述現有的 XML 檔案推斷 XSD 結構描述使用 Visual Studio XML 工具。  
  
-   從 SP1 開始，您可以使用 XML 結構描述精靈以建立從一個或多個 XML 文件推斷 XML 結構描述集，並將它包含您的專案。 您可以使用文字檔、 XML 從 HTTP 網際網路位址或輸入或貼到 XML to Schema 精靈的 XML 格式的 XML 文任何的件組合。 若要存取 XML to Schema 精靈，請按一下 **加入新項目**上**專案**功能表，並新增**XML 結構描述**範本從**資料**或**一般項目**範本群組。 在包含推斷 XML 結構描述集的所有 XML 文件來源之後，請按一下**確定**建立推斷的結構描述集。 如需詳細資訊，請參閱[XML to Schema 精靈](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)。  
  
-   您也可以使用 Visual Studio XML 編輯器來推斷 XSD 結構描述設定從 XML 檔案。 若要建立 XML 結構描述使用 XML 編輯器設定，在 Visual Studio XML 設計工具中開啟 XML 檔案，然後按一下  **Create Schema**上**XML**功能表。 建立 XSD 結構描述集之後，您可以將建立結構描述集儲存到一個或多個 XSD 檔案，並將它們包含在專案中。 如需詳細資訊，請參閱[How to︰ 在 Visual Basic 中啟用 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)。  
  
 請注意不同的 XSD 結構描述集可能會推斷出預期會有相同的結構描述的多個 XML 文件。 這可能會發生在一個 XML 檔案，而不是在另一個，找到特定項目和屬性或元素，例如包含不同的順序。 當您使用 XSD 結構描述推斷時，您應該檢閱推斷的 XSD 結構描述集的完整性與正確性。  
  
## <a name="member-list"></a>成員清單  
 輸入句號 （.） 來分隔的執行個體後<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件 (或執行個體`IEnumerable(Of XElement)`或`IEnumerable(Of XDocument)`)，Visual Basic IntelliSense 會顯示可能的物件成員的清單。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 初始清單包含三個選項可表示 XML 軸屬性，如下列清單中所述。  
  
|選項|說明|  
|---|---|  
|**\< >**|選取此選項可顯示一份可能的子項目。 如需詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和<xref:System.Xml.Linq.XContainer.Elements%2A>方法。</xref:System.Xml.Linq.XContainer.Elements%2A>|  
|**@**|選取此選項可顯示一份可能的屬性。 如需詳細資訊，請參閱[XML 軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。此功能僅適用於物件的型別<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>|  
|**…\< >**|選取此選項可顯示一份可能的子代項目。 如需詳細資訊，請參閱[How to︰ 存取 XML 子代項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)和<xref:System.Xml.Linq.XContainer.Elements%2A>方法。</xref:System.Xml.Linq.XContainer.Elements%2A>|  
  
 選取或開始輸入的任何 XML 選項，從清單中。 成員的清單就會顯示從 XML 結構描述可能專屬於所選的選項的成員。 如果您擁有的 XML 命名空間匯入特定的 XML 命名空間前置詞相關聯，潛在的 XML 命名空間前置詞的清單包含在成員清單中。  
  
 例如，請考慮下列 XSD 結構描述。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"   
           elementFormDefault="qualified"   
           targetNamespace="http://SamplePurchaseOrder"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="PurchaseOrders">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="PurchaseOrder">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Address" />  
              <xs:element name="Items" />  
              <xs:element name="Comment" />  
            </xs:sequence>  
            <xs:attribute name="PurchaseOrderNumber" type="xs:unsignedShort" use="required" />  
            <xs:attribute name="OrderDate" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 有效的 XSD 結構描述的 XML 如下所示。  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 如果您在專案中包含此 XSD 結構描述檔案，並從 XSD 結構描述的目標命名空間匯入到您的程式碼檔案或專案，Visual Basic IntelliSense 輸入 Visual Basic 程式碼時，就會顯示從結構描述的成員。 如果 XSD 結構描述的目標命名空間以預設的命名空間匯入，並輸入下列命令，IntelliSense 會顯示一份可能的子項目，如`PurchaseOrder`XML 項目。  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 清單是由位址、 註解，以及項目的項目所組成。  
  
### <a name="certainty-levels-for-intellisense-list-items"></a>IntelliSense 清單項目的確定性 」 層級  
 決定用於 IntelliSense 的 XSD 型別不準確。 如此一來，XML IntelliSense 通常會顯示可能的成員的展開的清單。 為協助您從 IntelliSense 成員清單中選取項目，項目會顯示的 XML IntelliSense 對於特定成員的確定性 」 層級的指示。  
  
 有時 XML IntelliSense 可以識別特定的類型從 XSD 結構描述。 在這些情況下，它會顯示可能的子項目、 屬性或該 XSD 型別的子系元素與較高程度的確定性 」。 這些項目會識別的核取記號。  
  
 不過，有時候 XML IntelliSense 不能識別特定的類型從 XSD 結構描述。 在這些情況下，它會顯示可能的子項目、 屬性或子系的項目從專案的 XSD 結構描述的展開的清單與低度的確定性 」。 這些項目會識別加上問號。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 啟用 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [XML to Schema 精靈](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 屬性軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [專案設計工具、參考頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)
