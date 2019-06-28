---
title: 資料合約結構描述參考
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: e736b963fe081832995cdc8d9c2ab41ac34cf980
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425388"
---
# <a name="data-contract-schema-reference"></a>資料合約結構描述參考

本主題說明 <xref:System.Runtime.Serialization.DataContractSerializer> 用來描述 XML 序列化之 Common Language Runtime (CLR) 型別的 XML 結構描述 (XSD) 子集。

## <a name="datacontractserializer-mappings"></a>DataContractSerializer 對應

`DataContractSerializer`從 Windows Communication Foundation (WCF) 服務使用中繼資料端點匯出中繼資料時，將 CLR 型別對應至 XSD 或[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 如需詳細資訊，請參閱 <<c0> [ 資料合約序列化程式](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)。

當您使用 Svcutil.exe 來存取 Web 服務描述語言 (WSDL) 或 XSD 文件並產生服務或用戶端的資料合約時， `DataContractSerializer` 也會將 XSD 對應至 CLR 型別。

只有符合本文件所述之需求的 XML 結構描述執行個體可以使用 `DataContractSerializer`對應至 CLR 型別。

### <a name="support-levels"></a>支援層級

`DataContractSerializer` 針對特定 XML 結構描述功能提供下列支援層級：

- **支援**： 使用 `DataContractSerializer`從這項功能明確對應至 CLR 型別或屬性 (或兩者)。

- **忽略**： 此功能可用在 `DataContractSerializer`所匯入的結構描述中，但是不會對產生程式碼有任何影響。

- **禁止**： `DataContractSerializer` 不支援使用此功能來支援匯入結構描述。 例如，當使用結構描述 (運用此類功能) 來存取 WSDL 時，Svcutil.exe 就會改回使用 <xref:System.Xml.Serialization.XmlSerializer> 。 這是預設的結果。

## <a name="general-information"></a>一般資訊

- [XML 結構描述](https://go.microsoft.com/fwlink/?LinkId=95475)(英文) 將說明結構描述命名空間。 本文使用 "xs" 前置詞。

- 任何包含非結構描述命名空間的屬性都會被忽略。

- 任何附註 (除了本文中所述的以外) 都會被忽略。

### <a name="xsschema-attributes"></a>\<schema> >： 屬性

|屬性|DataContract|
|---------------|------------------|
|`attributeFormDefault`|忽略。|
|`blockDefault`|忽略。|
|`elementFormDefault`|必須限定。 所有項目必須限定，以便由 `DataContractSerializer`支援結構描述。 這可藉由設定任一xs:schema/@elementFormDefault為"qualified"或藉由設定xs:element/@form為"qualified"上每個個別的項目宣告。|
|`finalDefault`|忽略。|
|`Id`|忽略。|
|`targetNamespace`|支援且對應至資料合約命名空間。 如果沒有指定此屬性，便會使用空白的命名空間。 不能保留的命名空間 `http://schemas.microsoft.com/2003/10/Serialization/` 。|
|`version`|忽略。|

### <a name="xsschema-contents"></a>\<schema> >： 內容

|內容|結構描述|
|--------------|------------|
|`include`|支援。 `DataContractSerializer` 支援 xs:include 和 xs:import。 但是，當您從本機檔案載入中繼資料時，Svcutil.exe 會限制下列 `xs:include/@schemaLocation` 和 `xs:import/@location` 參考。 在此情況下，結構描述檔案清單必須透過超出範圍之外的機制，而不是 `include` 來傳遞； `include`的結構描述文件會被忽略。|
|`redefine`|禁止。 基於安全性的理由，禁止透過 `xs:redefine` 使用 `DataContractSerializer` ： `x:redefine` 要求必須遵循 `schemaLocation` 。 在特定情況下，使用 DataContract 的 Svcutil.exe 會限制使用 `schemaLocation`。|
|`import`|支援。 `DataContractSerializer` 支援 `xs:include` 和 `xs:import`。 但是，當您從本機檔案載入中繼資料時，Svcutil.exe 會限制下列 `xs:include/@schemaLocation` 和 `xs:import/@location` 參考。 在此情況下，結構描述檔案清單必須透過超出範圍之外的機制，而不是 `include` 來傳遞； `include`的結構描述文件會被忽略。|
|`simpleType`|支援。 請參閱 `xs:simpleType` 一節。|
|`complexType`|支援，且對應至資料合約。 請參閱 `xs:complexType` 一節。|
|`group`|忽略。 `DataContractSerializer` 不支援使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。 已忽略這些宣告並將其視為 `xs:schema`的子項，但是無法從 `complexType` 或其他支援的建構內部參考這些宣告。|
|`attributeGroup`|忽略。 `DataContractSerializer` 不支援使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。 已忽略這些宣告並將其視為 `xs:schema`的子項，但是無法從 `complexType` 或其他支援的建構內部參考這些宣告。|
|`element`|支援。 請參閱全域項目宣告 (GED)。|
|`attribute`|忽略。 `DataContractSerializer` 不支援使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。 已忽略這些宣告並將其視為 `xs:schema`的子項，但是無法從 `complexType` 或其他支援的建構內部參考這些宣告。|
|`notation`|忽略。|

## <a name="complex-types--xscomplextype"></a>複雜型別 – \<complextype> >

### <a name="general-information"></a>一般資訊

每個複雜型別\<complextype> > 對應至資料合約。

### <a name="xscomplextype-attributes"></a>\<complextype> >： 屬性

|屬性|結構描述|
|---------------|------------|
|`abstract`|必須為 false (預設)。|
|`block`|禁止。|
|`final`|忽略。|
|`id`|忽略。|
|`mixed`|必須為 false (預設)。|
|`name`|支援且對應至資料合約名稱。 如果名稱之間包含句點，就會嘗試將型別對應至內部型別。 例如，名為 `A.B` 的複雜型別會對應至資料合約型別 (即包含資料合約名稱 `A`的內部型別)，但前提是必須存在此類資料合約型別。 有可能存在一個以上的巢狀層級：例如， `A.B.C` 可以是內部型別，但前提是 `A` 和 `A.B` 必須同時存在。|

### <a name="xscomplextype-contents"></a>\<complextype> >： 內容

|內容|結構描述|
|--------------|------------|
|`simpleContent`|禁止使用副檔名。<br /><br /> 只允許來自 `anySimpleType`的限制。|
|`complexContent`|支援。 請參閱「繼承」。|
|`group`|禁止。|
|`all`|禁止。|
|`choice`|禁止|
|`sequence`|支援，且對應至資料合約的資料成員。|
|`attribute`|已禁止，即使 use="prohibited" (有一個例外狀況) 亦然。 僅支援來自標準序列化結構描述命名空間的選用屬性。 它們無法對應至資料合約程式設計模型中的資料成員。 目前，只有此類屬性具有意義，而且會在「ISerializable」一節中討論。 其他所有項目都會被忽略。|
|`attributeGroup`|禁止。 在 WCF v1 版本中，`DataContractSerializer`會忽略出現與否`attributeGroup`內`xs:complexType`。|
|`anyAttribute`|禁止。|
|(空白)|對應至不包含資料成員的資料合約。|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<sequence > 複雜類型中： 屬性

|屬性|結構描述|
|---------------|------------|
|`id`|忽略。|
|`maxOccurs`|必須為 1 (預設)。|
|`minOccurs`|必須為 1 (預設)。|

### <a name="xssequence-in-a-complex-type-contents"></a>\<sequence > 複雜類型中： 內容

|內容|結構描述|
|--------------|------------|
|`element`|每個執行個體都會對應至資料成員。|
|`group`|禁止。|
|`choice`|禁止。|
|`sequence`|禁止。|
|`any`|禁止。|
|(空白)|對應至不包含資料成員的資料合約。|

## <a name="elements--xselement"></a>項目 – \<xs: element >

### <a name="general-information"></a>一般資訊

`<xs:element>` 可能在下列情況發生：

- 它會發生在用來描述一般 (非集合) 資料合約之資料成員的 `<xs:sequence>`中。 在此情況下， `maxOccurs` 屬性必須為 1 (不允許 0 這個值)。

- 它會發生在用來描述集合資料合約之資料成員的 `<xs:sequence>`中。 在此情況下， `maxOccurs` 屬性必須為大於 1 或 "unbounded"。

- 它會發生在 `<xs:schema>` 中，做為全域項目宣告 (GED)。

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs: element > maxOccurs = 1 內\<xs > （資料成員）

|屬性|結構描述|
|---------------|------------|
|`ref`|禁止。|
|`name`|支援，且對應至資料成員名稱。|
|`type`|支援，且對應至資料成員型別。 如需詳細資訊，請參閱「型別/基本對應」。 如果未指定 (而且項目不包含匿名型別)，則會假定為 `xs:anyType` 。|
|`block`|忽略。|
|`default`|禁止。|
|`fixed`|禁止。|
|`form`|必須限定。 此屬性可以透過 `elementFormDefault` 上的 `xs:schema`來設定。|
|`id`|忽略。|
|`maxOccurs`|1|
|`minOccurs`|對應至資料成員的 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性 (當`IsRequired` 為 1 時， `minOccurs` 為 true)。|
|`nillable`|影響型別對應。 請參閱「型別/基本對應」。|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs: element > maxoccurs > 1 內\<xs > （集合）

- 對應至 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>。

- 在集合型別中，xs:sequence 只允許使用一個 xs:element。

 集合可以是下列任何型別：

- 一般集合 (例如，陣列)。

- 字典集合 (將某值對應至另一個值；例如， <xref:System.Collections.Hashtable>)。

- 字典與金鑰/值組型別的陣列之間的唯一差異，就在於產生的程式設計模型。 您可採用一種結構描述附註機制，將特定型別指定為字典集合。

`ref`、 `block`、 `default`、 `fixed`、 `form`和 `id` 屬性的規則與非集合案例的規則是一樣的。 下表包含其他各項屬性。

|屬性|結構描述|
|---------------|------------|
|`name`|支援，且對應至 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> 屬性 (Attribute) 中的 `CollectionDataContractAttribute` 屬性 (Property)。|
|`type`|支援，且對應至存放在集合中的型別。|
|`maxOccurs`|大於 1 或 "unbounded"。 DC 結構描述應該使用 "unbounded"。|
|`minOccurs`|忽略。|
|`nillable`|影響型別對應。 字典集合會忽略此屬性。|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs: element > 內\<schema> > 元素的全域宣告

- 與結構描述中的型別具有相同名稱與命名空間的全域項目宣告 (GED)，或是可在本身內部定義匿名型別的項目，稱為與型別關聯。

- 結構描述匯出：每個產生的型別，不管是簡單還是複雜型別，都會產生關聯的 GED。

- 還原序列化/序列化：關聯的 GED 可做為型別的根項目來使用。

- 結構描述匯入：如果關聯的 GED 遵循下列規則 (除非它們定義了型別)，則這些 GED 為非必要而且會被忽略。

|屬性|結構描述|
|---------------|------------|
|`abstract`|關聯的 GED 必須是 false。|
|`block`|禁止在關聯的 GED 中使用。|
|`default`|禁止在關聯的 GED 中使用。|
|`final`|關聯的 GED 必須是 false。|
|`fixed`|禁止在關聯的 GED 中使用。|
|`id`|忽略。|
|`name`|支援。 請參閱關聯的 GED 定義。|
|`nillable`|關聯的 GED 必須是 true。|
|`substitutionGroup`|禁止在關聯的 GED 中使用。|
|`type`|支援，且必須符合關聯 GED 的關聯型別 (除非項目包含匿名型別)。|

### <a name="xselement-contents"></a>\<xs: element >： 內容

|內容|結構描述|
|--------------|------------|
|`simpleType`|支援。*|
|`complexType`|支援。*|
|`unique`|忽略。|
|`key`|忽略。|
|`keyref`|忽略。|
|(空白)|支援。|

\* 使用時`simpleType`和`complexType,`匿名型別對應是與非匿名型別相同，只不過沒有任何的匿名資料合約，因此建立具名的資料合約時，產生的名稱衍生自項目名稱。 下表為匿名型別的規則：

- WCF 實作詳細資料：如果`xs:element`名稱不包含句號，則匿名型別會對應至外部資料合約型別的內部型別。 如果名稱包含句點，則結果的資料合約型別是獨立的 (不是內部型別)。

- 產生之內部型別的資料合約名稱為外部型別的資料合約名稱，後面並跟著句點、項目名稱，以及字串 "Type"。

- 如果此名稱的資料合約已經存在，則名稱後面會加上 "1"、"2"、"3" 等，直到將其建立為唯一的名稱。

## <a name="simple-types---xssimpletype"></a>簡單型別- \<simpletype> >

### <a name="xssimpletype-attributes"></a>\<simpletype> >： 屬性

|屬性|結構描述|
|---------------|------------|
|`final`|忽略。|
|`id`|忽略。|
|`name`|支援，且對應至資料合約名稱。|

### <a name="xssimpletype-contents"></a>\<simpletype> >： 內容

|內容|結構描述|
|--------------|------------|
|`restriction`|支援。 對應至列舉資料合約。 如果此屬性與列舉模式不符，就會被忽略。 請參閱「 `xs:simpleType` 限制」一節。|
|`list`|支援。 對應至旗標列舉資料合約。 請參閱「 `xs:simpleType` 清單」一節。|
|`union`|禁止。|

### <a name="xsrestriction"></a>\<xs:restriction>

- base="`xs:anyType`" 僅支援複雜型別限制。

- 只包含 `xs:string` 限制 Facet 的 `xs:enumeration` 簡單型別限制會對應至列舉資料合約。

- 其他所有簡單型別限制則會對應至所限制的型別上。 例如， `xs:int` 的限制會對應至整數，就像 `xs:int` 本身一樣。 如需有關基本類型對應的詳細資訊，請參閱型別/基本對應。

### <a name="xsrestriction-attributes"></a>\<xs: restriction >： 屬性

|屬性|結構描述|
|---------------|------------|
|`base`|必須是支援的簡單型別或 `xs:anyType`。|
|`id`|忽略。|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs: restriction > 所有其他案例： 內容

|內容|結構描述|
|--------------|------------|
|`simpleType`|如果存在，必須衍生自支援的基本類型。|
|`minExclusive`|忽略。|
|`minInclusive`|忽略。|
|`maxExclusive`|忽略。|
|`maxInclusive`|忽略。|
|`totalDigits`|忽略。|
|`fractionDigits`|忽略。|
|`length`|忽略。|
|`minLength`|忽略。|
|`maxLength`|忽略。|
|`enumeration`|忽略。|
|`whiteSpace`|忽略。|
|`pattern`|忽略。|
|(空白)|支援。|

## <a name="enumeration"></a>列舉

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs: restriction > 列舉型別： 屬性

|屬性|結構描述|
|---------------|------------|
|`base`|如果存在的話，必須是 `xs:string`。|
|`id`|忽略。|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs: restriction > 列舉： 內容

|內容|結構描述|
|--------------|------------|
|`simpleType`|如果存在，必須是資料合約所支援的列舉限制 (本節)。|
|`minExclusive`|忽略。|
|`minInclusive`|忽略。|
|`maxExclusive`|忽略。|
|`maxInclusive`|忽略。|
|`totalDigits`|忽略。|
|`fractionDigits`|忽略。|
|`length`|禁止。|
|`minLength`|禁止。|
|`maxLength`|禁止。|
|`enumeration`|支援。 會忽略列舉 "id"，並將 "value" 對應至列舉資料合約中的值名稱。|
|`whiteSpace`|禁止。|
|`pattern`|禁止。|
|(空白)|支援，且對應至空的列舉型別。|

 下列程式碼將示範 C# 列舉類別。

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

此類別會透過 `DataContractSerializer`對應至下列結構描述。 如果列舉值從 1 開始，則不會產生 `xs:annotation` 區塊。

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a>\<xs:list>

`DataContractSerializer` 會將標示為 `System.FlagsAttribute` 的列舉型別對應至衍生自 `xs:list` 的 `xs:string`。 不支援其他任何 `xs:list` 變化。

### <a name="xslist-attributes"></a>\<x: list> >： 屬性

|屬性|結構描述|
|---------------|------------|
|`itemType`|禁止。|
|`id`|忽略。|

### <a name="xslist-contents"></a>\<x: list> >： 內容

|內容|結構描述|
|--------------|------------|
|`simpleType`|必須使用 `xs:string` Facet 從 `xs:enumeration` 限制。|

如果列舉值並未遵循 2 次方的級數 (旗標的預設值)，則會將值儲存在 `xs:annotation/xs:appInfo/ser:EnumerationValue` 項目中。

例如，下列程式碼會為列舉型別加上旗標。

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

此型別會對應至下列結構描述。

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a>繼承

### <a name="general-rules"></a>一般規則

資料合約可以繼承自其他資料合約。 此類資料合約會對應至基底型別，而且會使用 `<xs:extension>` XML 結構描述建構並由延伸型別衍生。

資料合約無法繼承自集合資料合約。

例如，下列程式碼為資料合約。

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

此資料合約會對應至下列 XML 結構描述型別宣告。

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a>\<complexcontent> >： 屬性

|屬性|結構描述|
|---------------|------------|
|`id`|忽略。|
|`mixed`|必須為 false。|

### <a name="xscomplexcontent-contents"></a>\<complexcontent> >： 內容

|內容|結構描述|
|--------------|------------|
|`restriction`|禁止，除了當 base="`xs:anyType`" 以外。 後者等同於將 `xs:restriction` 的內容直接放在 `xs:complexContent`容器底下。|
|`extension`|支援。 對應至資料合約繼承。|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs: extension > 在\<complexcontent> >： 屬性

|屬性|結構描述|
|---------------|------------|
|`id`|忽略。|
|`base`|支援。 對應至此型別所繼承的基底資料合約型別。|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs: extension > 在\<complexcontent> >： 內容

其規則與 `<xs:complexType>` 內容的規則一樣。

如果提供了 `<xs:sequence>` ，則其成員項目會對應至額外資料成員 (存在衍生的資料合約中)。

如果衍生型別內含的項目與基底型別中的項目擁有相同的名稱，則重複的項目宣告會對應至已產生唯一名稱的資料成員。 正整數會新增至資料成員名稱 ("member1"、"member2" 等等)，直到找到唯一名稱為止。 相反地：

- 如果衍生資料合約的資料成員與基底資料合約中的資料成員具有相同的名稱與型別，則 `DataContractSerializer` 會在衍生型別中產生這個對應的項目。

- 如果衍生資料合約的資料成員與基底資料合約中的資料成員具有相同的名稱 (但型別不同)，則 `DataContractSerializer` 會將包含型別 `xs:anyType` 之項目的結構描述匯入基底型別與衍生型別宣告中。 原始型別名稱會保留在 `xs:annotations/xs:appInfo/ser:ActualType/@Name`中。

兩種變化視各自的資料成員的順序而定，都可能會導致結構描述內含模糊的內容模型。

## <a name="typeprimitive-mapping"></a>型別/基本對應

`DataContractSerializer` 針對 XML 結構描述基本型別使用下列對應。

|XSD 類型|.NET 型別|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|用於位移的<xref:System.DateTime> 和 <xref:System.TimeSpan> 。 請參閱下面的＜DateTimeOffset 序列化＞。|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<xref:System.Byte> 陣列。|
|`hexBinary`|<xref:System.String>.|
|`float`|<xref:System.Single>.|
|`double`|<xref:System.Double>.|
|`anyURI`|<xref:System.Uri>.|
|`QName`|<xref:System.Xml.XmlQualifiedName>.|
|`string`|<xref:System.String>.|
|`normalizedString`|<xref:System.String>.|
|`token`|<xref:System.String>.|
|`language`|<xref:System.String>.|
|`Name`|<xref:System.String>.|
|`NCName`|<xref:System.String>.|
|`ID`|<xref:System.String>.|
|`IDREF`|<xref:System.String>.|
|`IDREFS`|<xref:System.String>.|
|`ENTITY`|<xref:System.String>.|
|`ENTITIES`|<xref:System.String>.|
|`NMTOKEN`|<xref:System.String>.|
|`NMTOKENS`|<xref:System.String>.|
|`decimal`|<xref:System.Decimal>.|
|`integer`|<xref:System.Int64>.|
|`nonPositiveInteger`|<xref:System.Int64>.|
|`negativeInteger`|<xref:System.Int64>.|
|`long`|<xref:System.Int64>.|
|`int`|<xref:System.Int32>.|
|`short`|<xref:System.Int16>.|
|`Byte`|<xref:System.SByte>.|
|`nonNegativeInteger`|<xref:System.Int64>.|
|`unsignedLong`|<xref:System.UInt64>.|
|`unsignedInt`|<xref:System.UInt32>.|
|`unsignedShort`|<xref:System.UInt16>.|
|`unsignedByte`|<xref:System.Byte>.|
|`positiveInteger`|<xref:System.Int64>.|

## <a name="iserializable-types-mapping"></a>ISerializable 型別對應

在.NET Framework 1.0 版，<xref:System.Runtime.Serialization.ISerializable>導入做為一般的機制來序列化物件的持續性服務或資料傳輸。 有許多實作的.NET Framework 類型`ISerializable`而且可以在應用程式之間傳遞。 <xref:System.Runtime.Serialization.DataContractSerializer> 自然會為 `ISerializable` 類別提供支援。 `DataContractSerializer` 會對應至 `ISerializable` 實作結構描述型別 (其中只有型別的 QName 限定名稱不同)，而且是有效的屬性集合。 例如， `DataContractSerializer` 對應 <xref:System.Exception> 至下列 XSD 型別中 `http://schemas.datacontract.org/2004/07/System` 命名空間。

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

在資料合約序列化結構描述中宣告的選用屬性 `ser:FactoryType` 會參考可以還原序列化型別的處理站類別。 處理站類別必須是正在使用之 `DataContractSerializer` 執行個體的已知型別集合的一部分。 如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。

## <a name="datacontract-serialization-schema"></a>DataContract 序列化結構描述

由 `DataContractSerializer` 匯出的一些結構描述使用來自特殊資料合約序列化命名空間的型別、項目和屬性：

`http://schemas.microsoft.com/2003/10/Serialization`

下列為完整的資料合約序列化結構描述宣告。

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

請注意下列各項：

- `ser:char` 已引入來代表型別 <xref:System.Char>的 Unicode 字元。

- `valuespace` 的 `xs:duration` 已縮減為排序的組合，以對應至 <xref:System.TimeSpan>。

- `FactoryType` 會用在衍生自 <xref:System.Runtime.Serialization.ISerializable>之型別所匯出的結構描述中。

## <a name="importing-non-datacontract-schemas"></a>匯入非 DataContract 結構描述

`DataContractSerializer` 具有 `ImportXmlTypes` 選項，可允許匯入不符合 `DataContractSerializer` XSD 設定檔的結構描述 (請參閱 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> 屬性)。 將此選項設為 `true` 可允許接受不符的結構描述型別，並將之對應至下列實作： <xref:System.Xml.Serialization.IXmlSerializable> 包裝 <xref:System.Xml.XmlNode> 的陣列 (只有類別名稱不同)。

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a>DateTimeOffset 序列化

<xref:System.DateTimeOffset> 不會被視為基本型別。 反之，它會被序列化為包含兩個部分的複雜項目。 第一個部分代表日期時間，而第二個部分則代表日期時間的位移。 下列程式碼提供序列化的 DateTimeOffset 值範例。

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

結構描述如下列所示。

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
