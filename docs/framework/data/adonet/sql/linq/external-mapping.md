---
title: 外部對應
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 4b493279307f61847b72048c5bfa9dc14a38fe29
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218676"
---
# <a name="external-mapping"></a><span data-ttu-id="223a6-102">外部對應</span><span class="sxs-lookup"><span data-stu-id="223a6-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="223a6-103">支援*外部對應*，供您必須使用個別的 XML 檔案來指定資料庫的資料模型和物件模型之間對應的程序。</span><span class="sxs-lookup"><span data-stu-id="223a6-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="223a6-104">使用外部對應檔案的好處如下：</span><span class="sxs-lookup"><span data-stu-id="223a6-104">Advantages of using an external mapping file include the following:</span></span>  
  
-   <span data-ttu-id="223a6-105">您可以將對應程式碼與應用程式的程式碼分開來。</span><span class="sxs-lookup"><span data-stu-id="223a6-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="223a6-106">如此一來，就可以避免應用程式的程式碼變得雜亂。</span><span class="sxs-lookup"><span data-stu-id="223a6-106">This approach reduces clutter in your application code.</span></span>  
  
-   <span data-ttu-id="223a6-107">您可以將外部對應檔案視為組態檔。</span><span class="sxs-lookup"><span data-stu-id="223a6-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="223a6-108">例如，在交付二進位碼檔案之後，只要換掉外部對應檔案，就可以更新應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="223a6-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="223a6-109">需求</span><span class="sxs-lookup"><span data-stu-id="223a6-109">Requirements</span></span>  
 <span data-ttu-id="223a6-110">對應檔案必須是 XML 檔案，然後以該檔案必須驗證[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]結構描述定義 (.xsd) 檔案。</span><span class="sxs-lookup"><span data-stu-id="223a6-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="223a6-111">可套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="223a6-111">The following rules apply:</span></span>  
  
-   <span data-ttu-id="223a6-112">對應檔案必須是 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="223a6-112">The mapping file must be an XML file.</span></span>  
  
-   <span data-ttu-id="223a6-113">XML 對應檔案必須根據 XML 結構描述定義檔進行驗證。</span><span class="sxs-lookup"><span data-stu-id="223a6-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="223a6-114">如需詳細資訊，請參閱[如何：驗證 DBML 和外部對應檔](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="223a6-114">For more information, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
-   <span data-ttu-id="223a6-115">外部對應會覆寫以屬性 (Attribute) 為基礎的對應。</span><span class="sxs-lookup"><span data-stu-id="223a6-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="223a6-116">也就是說，當您使用外部對應來源建立 <xref:System.Data.Linq.DataContext> 時，<xref:System.Data.Linq.DataContext> 會忽略已在類別上建立的所有對應屬性。</span><span class="sxs-lookup"><span data-stu-id="223a6-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="223a6-117">不論類別是否包含在外部對應檔案中，結果都是一樣。</span><span class="sxs-lookup"><span data-stu-id="223a6-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="223a6-118">不支援混合使用兩種對應方式 （以屬性為基礎和外部）。</span><span class="sxs-lookup"><span data-stu-id="223a6-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="223a6-119">XML 結構描述定義檔</span><span class="sxs-lookup"><span data-stu-id="223a6-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="223a6-120">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的外部對應必須根據下列 XML 結構描述定義進行驗證。</span><span class="sxs-lookup"><span data-stu-id="223a6-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="223a6-121">這個結構描述定義檔與用來驗證 DBML 檔案的結構描述定義檔不同。</span><span class="sxs-lookup"><span data-stu-id="223a6-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="223a6-122">如需詳細資訊，請參閱 < [LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md))。</span><span class="sxs-lookup"><span data-stu-id="223a6-122">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="223a6-123">Visual Studio 使用者也可找到這個 XSD 檔在 XML 結構描述 對話方塊中為"LinqToSqlMapping.xsd"。</span><span class="sxs-lookup"><span data-stu-id="223a6-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="223a6-124">若要正確使用此檔案來驗證外部對應檔案，請參閱[How to:驗證 DBML 和外部對應檔](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="223a6-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```  
?<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="223a6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="223a6-125">See also</span></span>

- [<span data-ttu-id="223a6-126">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="223a6-126">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="223a6-127">參考資料</span><span class="sxs-lookup"><span data-stu-id="223a6-127">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="223a6-128">HOW TO：產生物件模型作為外部檔案</span><span class="sxs-lookup"><span data-stu-id="223a6-128">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
