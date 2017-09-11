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
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 9a3c6f923bc9458997c388d4cf74ca113265a8cc
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017

---
# <a name="xml-intellisense-in-visual-basic"></a><span data-ttu-id="576ac-102">Visual Basic 中的 XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="576ac-102">XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="576ac-103">Visual Basic 程式碼編輯器包含提供 XML 結構描述中定義之元素的文字完成的 XML IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="576ac-103">The Visual Basic Code Editor includes IntelliSense features for XML that provide word completion for elements defined in an XML schema.</span></span> <span data-ttu-id="576ac-104">如果在您的專案中包含的 XML 結構描述定義 (XSD) 檔案和使用匯入結構描述的目標命名空間`Imports`陳述式，程式碼編輯器中會包含從 XSD 結構描述的項目清單中的 IntelliSense 的有效成員變數<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="576ac-104">If you include an XML Schema Definition (XSD) file in your project and import the target namespace of the schema by using the `Imports` statement, the Code Editor will include elements from the XSD schema in the IntelliSense list of valid member variables for <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="576ac-105">下圖顯示 IntelliSense 清單成員的<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="576ac-105">The following illustration shows the IntelliSense members list for an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="576ac-106">![在 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span><span class="sxs-lookup"><span data-stu-id="576ac-106">![XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")</span></span>  
<span data-ttu-id="576ac-107">XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="576ac-107">XML IntelliSense</span></span>  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a><span data-ttu-id="576ac-108">在 Visual Basic 中啟用 XML IntelliSense</span><span class="sxs-lookup"><span data-stu-id="576ac-108">Enabling XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="576ac-109">若要啟用 XML IntelliSense，Visual Basic 中，您必須包含 Visual Basic 專案中的 XSD 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="576ac-109">To enable XML IntelliSense in Visual Basic, you must include an XSD schema file in your Visual Basic project.</span></span> <span data-ttu-id="576ac-110">您也必須匯入程式碼檔案中的 XSD 結構描述的目標命名空間，使用`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="576ac-110">You must also import the target namespace for the XSD schema into your code file by using the `Imports` statement.</span></span> <span data-ttu-id="576ac-111">或者，新增的目標命名空間至專案層級命名空間清單使用**參考**Visual Basic 專案設計工具頁面。</span><span class="sxs-lookup"><span data-stu-id="576ac-111">Alternatively, you can add the target namespace to the project-level namespace list by using the **References** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="576ac-112">如需範例，請參閱[How to︰ 在 Visual Basic 中啟用 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="576ac-112">For examples, see [How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span> <span data-ttu-id="576ac-113">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)和[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="576ac-113">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) and [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="576ac-114">請注意，預設為您看不見 Visual Basic 專案中的 XSD 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="576ac-114">Note that by default you cannot see XSD schema files in Visual Basic projects.</span></span> <span data-ttu-id="576ac-115">您可能必須按一下**顯示所有檔案**按鈕來選取要包含在您的專案中的 XSD 檔案。</span><span class="sxs-lookup"><span data-stu-id="576ac-115">You may have to click the **Show All Files** button to select an XSD file to include in your project.</span></span>  
  
### <a name="generating-a-schema-file-schema-inference"></a><span data-ttu-id="576ac-116">產生結構描述檔案 （結構描述推斷）</span><span class="sxs-lookup"><span data-stu-id="576ac-116">Generating a Schema File (Schema Inference)</span></span>  
 <span data-ttu-id="576ac-117">您可以建立 XSD 結構描述現有的 XML 檔案推斷 XSD 結構描述使用 Visual Studio XML 工具。</span><span class="sxs-lookup"><span data-stu-id="576ac-117">You can create an XSD schema for an existing XML file by inferring the XSD schema by using Visual Studio XML tools.</span></span>  
  
-   <span data-ttu-id="576ac-118">從 SP1 開始，您可以使用 XML 結構描述精靈以建立從一個或多個 XML 文件推斷 XML 結構描述集，並將它包含您的專案。</span><span class="sxs-lookup"><span data-stu-id="576ac-118">Starting in SP1, you can use the XML to Schema Wizard to create an XML Schema set that is inferred from one or more XML documents and include it your project.</span></span> <span data-ttu-id="576ac-119">您可以使用文字檔、 XML 從 HTTP 網際網路位址或輸入或貼到 XML to Schema 精靈的 XML 格式的 XML 文任何的件組合。</span><span class="sxs-lookup"><span data-stu-id="576ac-119">You can use any combination of XML documents in the form of text files, XML from HTTP Internet addresses, or XML that is typed or pasted into the XML to Schema Wizard.</span></span> <span data-ttu-id="576ac-120">若要存取 XML to Schema 精靈，請按一下 **加入新項目**上**專案**功能表，並新增**XML 結構描述**範本從**資料**或**一般項目**範本群組。</span><span class="sxs-lookup"><span data-stu-id="576ac-120">To access the XML to Schema Wizard, click **Add New Item** on the **Project** menu and add an **XML to Schema** template from either the **Data** or **Common Items** template group.</span></span> <span data-ttu-id="576ac-121">在包含推斷 XML 結構描述集的所有 XML 文件來源之後，請按一下**確定**建立推斷的結構描述集。</span><span class="sxs-lookup"><span data-stu-id="576ac-121">After you have included all the XML document sources to infer the XML Schema set from, click **OK** to create the inferred schema set.</span></span> <span data-ttu-id="576ac-122">如需詳細資訊，請參閱[XML to Schema 精靈](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="576ac-122">For more information, see [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).</span></span>  
  
-   <span data-ttu-id="576ac-123">您也可以使用 Visual Studio XML 編輯器來推斷 XSD 結構描述設定從 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="576ac-123">You can also use the Visual Studio XML Editor to infer an XSD schema set from an XML file.</span></span> <span data-ttu-id="576ac-124">若要建立 XML 結構描述使用 XML 編輯器設定，在 Visual Studio XML 設計工具中開啟 XML 檔案，然後按一下  **Create Schema**上**XML**功能表。</span><span class="sxs-lookup"><span data-stu-id="576ac-124">To create an XML schema set by using the XML Editor, open an XML file in the Visual Studio XML Designer and then click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="576ac-125">建立 XSD 結構描述集之後，您可以將建立結構描述集儲存到一個或多個 XSD 檔案，並將它們包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="576ac-125">After you create the XSD schema set, you can save the created schema set to one or more XSD files and include them in your project.</span></span> <span data-ttu-id="576ac-126">如需詳細資訊，請參閱[How to︰ 在 Visual Basic 中啟用 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="576ac-126">For more information, see[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).</span></span>  
  
 <span data-ttu-id="576ac-127">請注意不同的 XSD 結構描述集可能會推斷出預期會有相同的結構描述的多個 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="576ac-127">Note that different XSD schema sets might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="576ac-128">這可能會發生在一個 XML 檔案，而不是在另一個，找到特定項目和屬性或元素，例如包含不同的順序。</span><span class="sxs-lookup"><span data-stu-id="576ac-128">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="576ac-129">當您使用 XSD 結構描述推斷時，您應該檢閱推斷的 XSD 結構描述集的完整性與正確性。</span><span class="sxs-lookup"><span data-stu-id="576ac-129">You should review inferred XSD schema sets for completeness and accuracy when you use XSD schema inference.</span></span>  
  
## <a name="member-list"></a><span data-ttu-id="576ac-130">成員清單</span><span class="sxs-lookup"><span data-stu-id="576ac-130">Member List</span></span>  
 <span data-ttu-id="576ac-131">輸入句號 （.） 來分隔的執行個體後<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件 (或執行個體`IEnumerable(Of XElement)`或`IEnumerable(Of XDocument)`)，Visual Basic IntelliSense 會顯示可能的物件成員的清單。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="576ac-131">After you type a period (.) to delimit an instance of an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object (or an instance of `IEnumerable(Of XElement)` or `IEnumerable(Of XDocument)`), Visual Basic IntelliSense displays a list of possible object members.</span></span> <span data-ttu-id="576ac-132">初始清單包含三個選項可表示 XML 軸屬性，如下列清單中所述。</span><span class="sxs-lookup"><span data-stu-id="576ac-132">The initial list includes three options that represent XML axis properties, as described in the following list.</span></span>  
  
|<span data-ttu-id="576ac-133">選項</span><span class="sxs-lookup"><span data-stu-id="576ac-133">Option</span></span>|<span data-ttu-id="576ac-134">說明</span><span class="sxs-lookup"><span data-stu-id="576ac-134">Description</span></span>|  
|---|---|  
|**\< >**|<span data-ttu-id="576ac-135">選取此選項可顯示一份可能的子項目。</span><span class="sxs-lookup"><span data-stu-id="576ac-135">Select this option to show a list of possible child elements.</span></span> <span data-ttu-id="576ac-136">如需詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和<xref:System.Xml.Linq.XContainer.Elements%2A>方法。</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="576ac-136">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
|**@**|<span data-ttu-id="576ac-137">選取此選項可顯示一份可能的屬性。</span><span class="sxs-lookup"><span data-stu-id="576ac-137">Select this option to show a list of possible attributes.</span></span> <span data-ttu-id="576ac-138">如需詳細資訊，請參閱[XML 軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)。此功能僅適用於物件的型別<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="576ac-138">For more information, see [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).This option is available only for objects of type <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="576ac-139">**…\< >**</span><span class="sxs-lookup"><span data-stu-id="576ac-139">**…\< >**</span></span>|<span data-ttu-id="576ac-140">選取此選項可顯示一份可能的子代項目。</span><span class="sxs-lookup"><span data-stu-id="576ac-140">Select this option to show a list of possible descendant elements.</span></span> <span data-ttu-id="576ac-141">如需詳細資訊，請參閱[How to︰ 存取 XML 子代項目](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)和<xref:System.Xml.Linq.XContainer.Elements%2A>方法。</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="576ac-141">For more information, see [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) and the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>|  
  
 <span data-ttu-id="576ac-142">選取或開始輸入的任何 XML 選項，從清單中。</span><span class="sxs-lookup"><span data-stu-id="576ac-142">Select or begin typing any of the XML options from the list.</span></span> <span data-ttu-id="576ac-143">成員的清單就會顯示從 XML 結構描述可能專屬於所選的選項的成員。</span><span class="sxs-lookup"><span data-stu-id="576ac-143">The member list will then display potential members from the XML schema that are specific to the selected option.</span></span> <span data-ttu-id="576ac-144">如果您擁有的 XML 命名空間匯入特定的 XML 命名空間前置詞相關聯，潛在的 XML 命名空間前置詞的清單包含在成員清單中。</span><span class="sxs-lookup"><span data-stu-id="576ac-144">If you have XML namespaces imported that are associated with a specific XML namespace prefix, a list of potential XML namespace prefixes is included in the member list.</span></span>  
  
 <span data-ttu-id="576ac-145">例如，請考慮下列 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="576ac-145">For example, consider the following XSD schema.</span></span>  
  
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
  
 <span data-ttu-id="576ac-146">有效的 XSD 結構描述的 XML 如下所示。</span><span class="sxs-lookup"><span data-stu-id="576ac-146">Valid XML for the XSD schema would resemble the following.</span></span>  
  
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
  
 <span data-ttu-id="576ac-147">如果您在專案中包含此 XSD 結構描述檔案，並從 XSD 結構描述的目標命名空間匯入到您的程式碼檔案或專案，Visual Basic IntelliSense 輸入 Visual Basic 程式碼時，就會顯示從結構描述的成員。</span><span class="sxs-lookup"><span data-stu-id="576ac-147">If you include this XSD schema file in a project and import the target namespace from the XSD schema into your code file or project, Visual Basic IntelliSense displays members from the schema as you type your Visual Basic code.</span></span> <span data-ttu-id="576ac-148">如果 XSD 結構描述的目標命名空間以預設的命名空間匯入，並輸入下列命令，IntelliSense 會顯示一份可能的子項目，如`PurchaseOrder`XML 項目。</span><span class="sxs-lookup"><span data-stu-id="576ac-148">If the target namespace for the XSD schema is imported as the default namespace and you type the following, IntelliSense displays a list of possible child elements for the `PurchaseOrder` XML element.</span></span>  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 <span data-ttu-id="576ac-149">清單是由位址、 註解，以及項目的項目所組成。</span><span class="sxs-lookup"><span data-stu-id="576ac-149">The list consists of the Address, Comment, and Items elements.</span></span>  
  
### <a name="certainty-levels-for-intellisense-list-items"></a><span data-ttu-id="576ac-150">IntelliSense 清單項目的確定性 」 層級</span><span class="sxs-lookup"><span data-stu-id="576ac-150">Certainty Levels for IntelliSense List Items</span></span>  
 <span data-ttu-id="576ac-151">決定用於 IntelliSense 的 XSD 型別不準確。</span><span class="sxs-lookup"><span data-stu-id="576ac-151">Determining the XSD type to use for IntelliSense is not exact.</span></span> <span data-ttu-id="576ac-152">如此一來，XML IntelliSense 通常會顯示可能的成員的展開的清單。</span><span class="sxs-lookup"><span data-stu-id="576ac-152">As a result, XML IntelliSense will often show an expanded list of possible members.</span></span> <span data-ttu-id="576ac-153">為協助您從 IntelliSense 成員清單中選取項目，項目會顯示的 XML IntelliSense 對於特定成員的確定性 」 層級的指示。</span><span class="sxs-lookup"><span data-stu-id="576ac-153">To aid you in selecting an item from the IntelliSense member list, items are displayed with an indication of the level of certainty that XML IntelliSense has for a particular member.</span></span>  
  
 <span data-ttu-id="576ac-154">有時 XML IntelliSense 可以識別特定的類型從 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="576ac-154">Sometimes XML IntelliSense can identify a specific type from the XSD schema.</span></span> <span data-ttu-id="576ac-155">在這些情況下，它會顯示可能的子項目、 屬性或該 XSD 型別的子系元素與較高程度的確定性 」。</span><span class="sxs-lookup"><span data-stu-id="576ac-155">In these cases, it will display possible child elements, attributes, or descendant elements for that XSD type with a high degree of certainty.</span></span> <span data-ttu-id="576ac-156">這些項目會識別的核取記號。</span><span class="sxs-lookup"><span data-stu-id="576ac-156">These items are identified with a check mark.</span></span>  
  
 <span data-ttu-id="576ac-157">不過，有時候 XML IntelliSense 不能識別特定的類型從 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="576ac-157">However, sometimes XML IntelliSense is not able to identify a specific type from the XSD schema.</span></span> <span data-ttu-id="576ac-158">在這些情況下，它會顯示可能的子項目、 屬性或子系的項目從專案的 XSD 結構描述的展開的清單與低度的確定性 」。</span><span class="sxs-lookup"><span data-stu-id="576ac-158">In these cases, it will display an expanded list of possible child elements, attributes, or descendant elements from the XSD schema for the project with a low degree of certainty.</span></span> <span data-ttu-id="576ac-159">這些項目會識別加上問號。</span><span class="sxs-lookup"><span data-stu-id="576ac-159">These items are identified with a question mark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576ac-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="576ac-160">See Also</span></span>  
 <span data-ttu-id="576ac-161">[如何︰ 啟用 Visual Basic 中的 XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span><span class="sxs-lookup"><span data-stu-id="576ac-161">[How to: Enable XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md) </span></span>  
<span data-ttu-id="576ac-162"> [XML to Schema 精靈](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="576ac-162"> [XML to Schema Wizard](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md) </span></span>  
<span data-ttu-id="576ac-163"> [Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="576ac-163"> [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="576ac-164"> [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="576ac-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="576ac-165"> [XML 屬性軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="576ac-165"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="576ac-166"> [XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="576ac-166"> [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span></span>  
<span data-ttu-id="576ac-167"> [專案設計工具、參考頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="576ac-167"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
