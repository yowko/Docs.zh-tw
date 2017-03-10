---
title: "XML IntelliSense in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, XML"
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# XML IntelliSense in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 程式碼編輯器含有 XML 專用的 IntelliSense 功能，可根據 XML 結構描述中已定義的項目提供文字自動完成的功能。  如果您在專案中併入 XML 結構描述定義 \(XSD\) 檔案，並使用 `Imports` 陳述式匯入結構描述的目標命名空間 \(Namespace\)，則程式碼編輯器會以 IntelliSense 清單的形式將 XSD 結構描述中的項目列為 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 物件的有效成員變數。  下圖顯示 <xref:System.Xml.Linq.XElement> 物件的 IntelliSense 成員清單。  
  
 ![Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/media/xml-intellisense.png "XML\_Intellisense")  
XML IntelliSense  
  
## 啟用 Visual Basic 中的 XML IntelliSense  
 若要啟用 Visual Basic 中的 XML IntelliSense，您必須在 Visual Basic 專案中併入 XSD 結構描述檔案。  您也必須使用 `Imports` 陳述式，將 XSD 結構描述的目標命名空間匯入至程式碼檔案。  或者，您也可以使用 Visual Basic 專案設計工具的 \[**參考**\] 頁，將目標命名空間加入至專案層級的命名空間清單。  如需範例，請參閱 [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)。  如需詳細資訊，請參閱 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) 和[專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)。  
  
 請注意，根據預設您在 Visual Basic 專案中看不到 XSD 結構描述檔案。  您可能需要按一下 \[**顯示所有檔案**\] 按鈕，才能選取要併入專案的 XSD 檔案。  
  
### 產生結構描述檔案 \(結構描述推斷\)  
 您可以使用 Visual Studio XML 工具推斷 XSD 結構描述，藉以為現有的 XML 檔案建立 XSD 結構描述。  
  
-   從 SP1 開始，您可以使用 \[XML To Schema 精靈\] 建立從一個或多個 XML 文件推斷而來的 XML 結構描述集，並將它包含於專案中。  您可以使用任何以文字檔、來自 HTTP 網際網路位址亦或輸入或貼至 \[XML To Schema 精靈\] 之 XML 的形式組合而成的 XML 文件。  若要存取 \[XML To Schema 精靈\]，請按一下 \[**專案**\] 功能表上的 \[**加入新項目**\]，然後從 \[**資料**\] 或 \[**一般項目**\] 樣板群組加入 \[**XML To Schema**\] 樣板。  在您已經加入要從中推斷 XML 結構描述集的所有 XML 文件來源之後，請按一下 \[**確定**\] 建立推斷的結構描述集。  如需詳細資訊，請參閱 [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)。  
  
-   您也可以使用 Visual Studio 的 \[XML 編輯器\]，從 XML 檔案推斷 XSD 結構描述集。  若要使用 \[XML 編輯器\] 建立 XML 結構描述，請在 Visual Studio 的 \[XML 設計工具\] 中開啟 XML 檔案，然後按一下 \[**XML**\] 功能表上的 \[**建立結構描述**\]。  在建立 XSD 結構描述集之後，您就可以將建立的結構描述集儲存至一個或多個 XSD 檔案，然後將它們加入專案中。  如需詳細資訊，請參閱[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)。  
  
 請注意，從多份預期會有相同結構描述的 XML 文件中，可能會推斷出不同的 XSD 結構描述集。  例如，當某個 XML 檔案中有特定項目與屬性 \(Attribute\)，但在另一個檔案中卻沒有時，或是併入的項目順序不同時，便有可能發生這種情形。  因此，使用 XSD 結構描述推斷時，應檢查所推斷之 XSD 結構描述集的完整性與正確性。  
  
## 成員清單  
 當您輸入句號 \(.\) 來分隔 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件的執行個體 \(或是 `IEnumerable(Of XElement)` 或 `IEnumerable(Of XDocument)` 的執行個體\) 時，Visual Basic IntelliSense 會顯示可能物件成員的清單。  初始清單包含三個代表 XML 軸屬性 \(Property\) 的選項，如下列清單所述。  
  
|||  
|-|-|  
|選項|描述|  
|**\< \>**|選取這個選項會顯示可能子項目的清單。  如需詳細資訊，請參閱 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。|  
|**@**|選取這個選項會顯示可能屬性 \(Attribute\) 的清單。  如需詳細資訊，請參閱 [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。這個選項只適用於 <xref:System.Xml.Linq.XElement> 型別的物件。|  
|**…\< \>**|選取這個選項會顯示可能子代 \(Descendant\) 項目的清單。  如需詳細資訊，請參閱 [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) 和 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。|  
  
 請選取或開始輸入上列任一個 XML 選項。  接著，成員清單就會顯示 XML 結構描述中符合所選選項的可能成員。  如果您已匯入與特定 XML 命名空間前置字元相關聯的 XML 命名空間，則成員清單中會包含可能 XML 命名空間前置字元的清單。  
  
 例如，假設有下列 XSD 結構描述。  
  
```  
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
  
 XSD 結構描述的有效 XML 將與底下類似。  
  
```  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 如果您將這個 XSD 結構描述檔併入專案中，並將 XSD 結構描述的目標命名空間匯入至您的程式碼檔案或專案，則 Visual Basic IntelliSense 會根據您輸入的 Visual Basic 程式碼，顯示結構描述中的成員。  如果 XSD 結構描述的目標命名空間已匯入做為預設命名空間，而且您輸入下列字元，則 IntelliSense 會顯示 `PurchaseOrder` XML 項目的可能子項目清單。  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 這份清單由 Address、Comment 及 Items 項目組成。  
  
### IntelliSense 清單項目的確定性層級  
 IntelliSense 對於 XSD 型別的判斷並不精確。  因此，XML IntelliSense 經常會顯示一長串可能的成員。  為了協助您從 IntelliSense 成員清單中選取項目，項目旁會標註 XML IntelliSense 對於特定成員的確定性層級。  
  
 有時候 XML IntelliSense 可以識別 XSD 結構描述中的特定型別。  在這種情況下，XML IntelliSense 會顯示該 XSD 型別中確定性較高的可能子項目、屬性 \(Attribute\) 或子代項目。  會以核取記號識別這些項目。  
  
 不過，有時候 XML IntelliSense 無法識別 XSD 結構描述中的特定型別。  在這種情況下，XML IntelliSense 會針對專案顯示一長串 XSD 結構描述中確定性較低的可能子項目、屬性 \(Attribute\) 或子代項目。  會以問號識別這些項目。  
  
## 請參閱  
 [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [專案設計工具，參考頁 \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)