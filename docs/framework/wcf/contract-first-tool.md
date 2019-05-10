---
title: Contract-First 工具
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 95aef67eb43176ab062b38979e714f232898f221
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652066"
---
# <a name="contract-first-tool"></a>Contract-First 工具
服務合約通常必須從現有的服務來建立。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，可以使用合約優先 (Contract-First) 工具自動從現有的服務建立資料合約類別。 若要使用合約優先工具，必須將 XML 結構描述定義 (XSD) 檔案下載至本機，這個工具無法透過 HTTP 匯入遠端資料合約。

 合約優先工具已整合到 Visual Studio 2012 中，做為建置工作。 每當建置專案時就會建立建置工作所產生的程式碼檔案，讓專案可以輕鬆採用基礎服務合約中的變更。

 合約優先工具可以匯入的結構描述型別包括下列各項：

```xml
<xsd:complexType>
<xsd:simpleType>
```

 如果這些型別是基本型別 (例如 `Int16` 或 `String`) 則不產生簡單型別，如果是 `Collection` 型別則不產生複雜類型。 如果這些型別是其他 `xsd:complexType` 的一部分，也不會產生型別。 在所有這些情況下，型別會改為參考專案中的現有型別。

## <a name="adding-a-data-contract-to-a-project"></a>將資料合約加入至專案
 在使用合約優先工具之前，必須先將服務合約 (XSD) 加入至專案。 為了便於說明本概觀，將會使用下列合約來解釋合約優先功能。 這項服務定義是 Bing 的搜尋應用程式開發介面所使用之服務合約的一個小型子集合。

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema id="ServiceSchema"
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"
    elementFormDefault="qualified"
    xmlns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
>
  <xs:complexType name="SearchRequest">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="WebSearchOption">
    <xs:restriction base="xs:string">
      <xs:enumeration value="DisableHostCollapsing" />
      <xs:enumeration value="DisableQueryAlterations" />
    </xs:restriction>
  </xs:simpleType>
</xs:schema>
```

 將上述服務合約加入至專案，以滑鼠右鍵按一下專案，然後選取**加入新...**. 從 [範本] 對話方塊的 [WCF] 窗格中選取 [結構描述定義]，並命名新的檔案 SampleContract.xsd。 複製上面的程式碼，將其貼入新檔案的程式碼檢視中。

## <a name="configuring-contract-first-options"></a>設定合約優先選項
 合約優先選項可以設定的內容功能表中的 WCF 專案。 若要啟用合約優先開發，請選取**將 XSD 啟用為型別定義語言**專案的 [屬性] 視窗的 [WCF] 頁面中核取方塊。

 ![啟用合約優先開發 WCF 選項的螢幕擷取畫面。](./media/contract-first-tool/contract-first-options.png)

 若要設定進階屬性，請按一下 [進階] 按鈕。

 ![進階的合約程式碼產生設定對話方塊。](./media/contract-first-tool/advanced-contract-settings.png)

 您可以設定下列適用於從合約產生程式碼的進階設定。 這些設定只能針對專案中的所有檔案進行，目前尚無法對個別檔案進行設定。

- **序列化程式模式**:此設定會決定哪種序列化程式用來讀取服務合約檔案。 當**XML 序列化程式**選取時，**集合型別**並**重複使用型別**選項已停用。 這些選項僅適用於**資料合約序列化程式**。

- **重複使用型別**:此設定指定哪些程式庫會用於型別重複使用。 此設定僅適用於**序列化程式模式**設為**資料合約序列化程式**。

- **集合型別**:此設定會指定要使用集合資料型別的完整限定或組件限定的類型。 此設定僅適用於**序列化程式模式**設為**資料合約序列化程式**。

- **字典型別**:此設定會指定完整限定或組件限定型別，用於字典資料型別。

- **EnableDataBinding**:此設定指定是否要實作<xref:System.ComponentModel.INotifyPropertyChanged>實作資料繫結的所有資料型別上的介面。

- **ExcludedTypes**： 此設定會指定要排除參考的組件的完整限定或組件限定類型的清單。 此設定僅適用於**序列化程式模式**設為**資料合約序列化程式**。

- **GenerateInternalTypes**:此設定指定是否要產生標示為內部的類別。 此設定僅適用於**序列化程式模式**設為**資料合約序列化程式**。

- **GenerateSerializableTypes**:此設定指定是否要產生類別<xref:System.SerializableAttribute>屬性。 此設定僅適用於**序列化程式模式**設為**資料合約序列化程式**。

- **/Importxmltypes**:此設定指定是否要將設定資料合約序列化程式，套用<xref:System.SerializableAttribute>屬性設定為不具類別<xref:System.Runtime.Serialization.DataContractAttribute>屬性。  此設定僅適用於**序列化程式模式**設為**資料合約序列化程式**。

- **SupportFx35TypedDataSets**:此設定指定是否要建立適用於.NET Framework 3.5 的具類型資料集提供額外的功能。 當**序列化程式模式**設為**XML 序列化程式**，則<xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35>延伸模組會新增至 XML 結構描述匯入工具，當此值設定為 True。 當**序列化程式模式**設為**資料合約序列化程式**，型別<xref:System.DateTimeOffset>時這個值設為 False，會從參考排除以便<xref:System.DateTimeOffset>一定會產生對於較舊 framework 版本。

- **InputXsdFiles**:此設定指定輸入檔清單。 每個檔案都必須包含有效的 XML 結構描述。

- **語言**:此設定會指定產生的合約程式碼語言。 這個設定必須可以由 <xref:System.CodeDom.Compiler.CodeDomProvider> 辨識。

- **NamespaceMappings**:此設定會指定從 XSD 目標命名空間到 CLR 命名空間的對應。 每個對應都要使用下列格式：

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     XML 序列化程式只接受一個使用下列格式的對應：

    ```xml
    "*, <CLR Namespace>"
    ```

- **OutputDirectory**:此設定會指定將產生的程式碼檔案的目錄。

 建置專案時，將會使用這些設定從服務合約檔案產生服務合約型別。

## <a name="using-contract-first-development"></a>使用合約優先開發
 將服務合約加入至專案，並確認組建設定中，則在按下建置專案後**F6**。 服務合約中定義的型別接著就可以在專案中使用。

 若要使用服務合約中定義的型別，請在目前命名空間之下加入 `ContractTypes` 的參考：

```csharp
using MyProjectNamespace.ContractTypes;
```

 如下所示，如此便可解析在專案中，服務合約中定義的類型：

 ![顯示在 IntelliSense 中，輸入前幾個字母之後 SearchRequest 類別。](./media/contract-first-tool/service-contract-types.png)

 工具所產生的型別會建立在 GeneratedXSDTypes.cs 檔案中。 在 建立檔案\<專案目錄 > j\<組建組態 > /XSDGeneratedCode/ 目錄預設。 本主題開頭的範例結構描述轉換如下：

```csharp
//------------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by a tool.
//     Runtime Version:4.0.30319.17330
//
//     Changes to this file may cause incorrect behavior and will be lost if
//     the code is regenerated.
// </auto-generated>
//------------------------------------------------------------------------------

namespace TestXSD3.ContractTypes
{
    using System.Xml.Serialization;

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Diagnostics.DebuggerStepThroughAttribute()]
    [System.ComponentModel.DesignerCategoryAttribute("code")]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]
    public partial class SearchRequest
    {

        private string versionField;

        private string marketField;

        private string uILanguageField;

        private string queryField;

        private string appIdField;

        private double latitudeField;

        private bool latitudeFieldSpecified;

        private double longitudeField;

        private bool longitudeFieldSpecified;

        private double radiusField;

        private bool radiusFieldSpecified;

        public SearchRequest()
        {
            this.versionField = "2.2";
        }

        /// <remarks/>
        [System.ComponentModel.DefaultValueAttribute("2.2")]
        public string Version
        {
            get
            {
                return this.versionField;
            }
            set
            {
                this.versionField = value;
            }
        }

        /// <remarks/>
        public string Market
        {
            get
            {
                return this.marketField;
            }
            set
            {
                this.marketField = value;
            }
        }

        /// <remarks/>
        public string UILanguage
        {
            get
            {
                return this.uILanguageField;
            }
            set
            {
                this.uILanguageField = value;
            }
        }

        /// <remarks/>
        public string Query
        {
            get
            {
                return this.queryField;
            }
            set
            {
                this.queryField = value;
            }
        }

        /// <remarks/>
        public string AppId
        {
            get
            {
                return this.appIdField;
            }
            set
            {
                this.appIdField = value;
            }
        }

        /// <remarks/>
        public double Latitude
        {
            get
            {
                return this.latitudeField;
            }
            set
            {
                this.latitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LatitudeSpecified
        {
            get
            {
                return this.latitudeFieldSpecified;
            }
            set
            {
                this.latitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Longitude
        {
            get
            {
                return this.longitudeField;
            }
            set
            {
                this.longitudeField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool LongitudeSpecified
        {
            get
            {
                return this.longitudeFieldSpecified;
            }
            set
            {
                this.longitudeFieldSpecified = value;
            }
        }

        /// <remarks/>
        public double Radius
        {
            get
            {
                return this.radiusField;
            }
            set
            {
                this.radiusField = value;
            }
        }

        /// <remarks/>
        [System.Xml.Serialization.XmlIgnoreAttribute()]
        public bool RadiusSpecified
        {
            get
            {
                return this.radiusFieldSpecified;
            }
            set
            {
                this.radiusFieldSpecified = value;
            }
        }
    }

    /// <remarks/>
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]
    [System.SerializableAttribute()]
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]
    public enum WebSearchOption
    {

        /// <remarks/>
        DisableHostCollapsing,

        /// <remarks/>
        DisableQueryAlterations,
    }
}
```

## <a name="errors-and-warnings"></a>錯誤和警告
 剖析 XSD 結構描述時發生的錯誤和警告將會顯示為建置錯誤和警告。

## <a name="interface-inheritance"></a>介面繼承
 不能同時使用介面繼承與合約優先開發；這與介面在其他作業中的運作方式一致。 若要使用繼承基底介面的介面，請使用兩個單獨的端點。 第一個端點使用繼承的合約，第二個端點實作基底介面。
