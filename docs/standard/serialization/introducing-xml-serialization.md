---
title: XML 序列化簡介
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
ms.openlocfilehash: 66412c620b8107312e5d58fef5cf1b5d9ee90107
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45615510"
---
# <a name="introducing-xml-serialization"></a>XML 序列化簡介

序列化是將物件轉換成可輕易傳輸之形式的程序。 例如，您可序列化物件並透過網際網路以 HTTP 在用戶端與伺服器之間傳輸。 另一方面，還原序列化從資料流重建物件。

 XML 序列化僅對物件的公用欄位及屬性值序列化至 XML 資料流。 XML 序列化不包含型別資訊。 例如，若您在 **Library** 命名空間中有 **Book** 物件，不保證它能還原序列化成為相同類型的物件。

> [!NOTE]
> XML 序列化不會轉換方法、索引子、私用欄位或唯讀屬性 (唯讀集合除外)。 若要序列化物件的所有欄位與屬性，無論是公用或私用，請使用 <xref:System.Runtime.Serialization.DataContractSerializer>，而非 XML 序列化。

 XML 序列化的核心類別為 <xref:System.Xml.Serialization.XmlSerializer> 類別，此類別中最重要的方法為**序列化**和**還原序列化**方法。 <xref:System.Xml.Serialization.XmlSerializer> 建立 C# 檔案並將它們編譯成為 .dll 檔案以執行此序列化。 在 .NET Framework 2.0 中，[XML 序列化程式產生器工具 (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) 的設計是用來預先產生要與您應用程式一起部署的這些序列化組件，並改善啟動效能。 產生的 XML 資料流**XmlSerializer** World Wide Web Consortium (W3C) 符合[XML 結構描述定義語言 (XSD) 1.0 建議](https://www.w3.org/TR/xslt)。 除此之外，產生的資料型別符合＜XML Schema Part 2: Datatypes＞文件的規範。

 您物件中的資料是用程式語言來描述的，該程式語言會建構如類別、欄位、屬性、基本類型、陣列，甚至是以 **XmlElement** 或 **XmlAttribute** 物件為格式的內嵌 XML。 您可以選擇以屬性註解建立自己的類別，或使用 XML 結構描述定義工具來依據現有 XML 結構描述產生類別。

 如果有 XML 結構描述，您可以執行 XML 結構描述定義工具來產生類別集，這些類別集是結構描述的強型別 (Strongly Typed)，而且以屬性註解。 當如此類別的執行個體序列化時，產生的 XML 符合 XML 結構描述。 隨著這種類別的提供，您可以根據操作簡易的物件模型進行程式設計，同時能確保產生的 XML 符合 XML 結構描述。 這是在 .NET Framework 使用其他類別的替代方法，就像是 **XmlReader** 和 **XmlWriter** 類別，用來剖析與撰寫 XML 資料流。 如需詳細資訊，請參閱 [XML 文件和資料](../../../docs/standard/data/xml/index.md)。 這些類別讓您能剖析所有 XML 資料流。 相反地，當預期 XML 資料流符合已知 XML 結構描述時，請使用 **XmlSerializer**。

 屬性會控制 **XmlSerializer** 類別產生的 XML 資料流，允許您設定 XML 資料流的 XML 命名空間、項目名稱、屬性名稱等等。 如需這些屬性的詳細資訊以及它們控制 XML 序列化的方式，請參閱[使用屬性控制 XML 序列化](controlling-xml-serialization-using-attributes.md)。 如需控制產生的 XML 所用的那些屬性資料表，請參閱[控制 XML 序列化的屬性](attributes-that-control-xml-serialization.md)。

 **XmlSerializer** 類別可更進一步序列化物件並且產生編碼的 SOAP XML 資料流。 產生的 XML 符合全球資訊網協會之＜Simple Object Access Protocol (SOAP) 1.1＞文件中的第 5 節。 如需此程序的詳細資訊，請參閱[如何：將物件序列化為 SOAP 編碼的 XML 資料流](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)。 如需控制產生之 XML 的屬性資料表，請參閱[控制編碼 SOAP 序列化的屬性](attributes-that-control-encoded-soap-serialization.md)。

 **XmlSerializer** 類別產生 XML Web 服務所建立以及傳遞的 SOAP 訊息。 若要控制 SOAP 訊息，可套用屬性至類別、傳回值、參數以及 XML Web 服務檔案 (.asmx) 中的欄位。 您可使用列在＜控制 XML 序列化的屬性＞和＜控制編碼 SOAP 序列化的屬性＞中的屬性，因為 XML Web 服務可使用常值或編碼的 SOAP 樣式。 如需使用屬性控制 XML Web 服務產生之 XML 的詳細資訊，請參閱[以 XML Web 服務進行 XML 序列化](xml-serialization-with-xml-web-services.md)。 如需 SOAP 與 XML Web 服務的詳細資訊，請參閱[自訂 SOAP 訊息](https://msdn.microsoft.com/en-us/subscriptions/index/dkwy2d72\(v=vs.71\).aspx)。

## <a name="security-considerations-for-xmlserializer-applications"></a>XmlSerializer 應用程式的安全性考量

建立使用 **XmlSerializer** 的應用程式時，您應留意下列項目及其含意：

- **XmlSerializer** 建立 C# (.cs) 檔案並在以 TEMP 環境變數命名的目錄中，將它們編譯成為 .dll 檔案；那些 DLL 會發生序列化。

  > [!NOTE]
  > 這些序列化組件可預先產生，並且使用 SGen.exe 工具簽署。 這並不是當做 Web 服務的伺服器。 換句話說，它只是供用戶端使用以及手動序列化。

  在建立與編譯時，程式碼與 DLL 容易受到惡意處理序的攻擊。 使用執行 Microsoft Windows NT 4.0 或以上版本的電腦時，有可能讓兩位以上的使用者共用 TEMP 目錄。 如果兩個帳戶擁有不同的安全性權限，而且權限較高的帳戶使用 **XmlSerializer** 執行應用程式，共用 TEMP 目錄會有危險性。 在此例中，一個使用者只要取代編譯的 .cs 或 .dll 檔案，就會破壞電腦的安全性。 若要去除此顧慮，請確定電腦上各帳戶皆有個別的設定檔。 根據預設，TEMP 環境變數是每個帳戶指向不同目錄。

- 若惡意使用者對網頁伺服器發送持續 XML 資料流 (阻絕服務攻擊)，那麼 **XmlSerializer** 會持續處理資料直到電腦資源消耗殆盡。

  若您使用執行 Internet Information Services (IIS) 的電腦，而且您的應用程式是在 IIS 裡執行，就可排除這類攻擊。 IIS 採用閘道，超過設定量 (預設為 4 KB) 的資料流就不處理。 若您建立不使用 IIS 的應用程式，而且以 **XmlSerializer** 還原序列化，那應實作類似閘道以防止阻絕服務攻擊。

- **XmlSerializer** 序列化資料並且以提供給它的任何類型來執行程式碼。

  惡意物件呈現威脅的方式有兩種。 它可執行惡意程式碼或將惡意程式碼插入 **XmlSerializer** 所建立的 C# 檔案。 在第一個情況下，若惡意物件試圖執行破壞性程序，程式碼存取安全性有助避免造成任何損壞。 在第二個情況下，理論上惡意物件有可能以某種方式將程式碼插入到 **XmlSerializer** 所建立的 C# 檔案。 雖然此問題已經徹底檢視，如此的攻擊也被認為非常不可能發生，但您應小心永遠不要以未知和未受信任的型別序列化資料。

- 序列化敏感資料可能會易受攻擊。

  在 **XmlSerializer** 擁有序列化資料之後，可儲存成 XML 檔案或其他資料存放區。 若您的資料存放區可由其他處理序存取，或是在內部網路或網際網路上看得到，那資料就可能遭竊取和惡意使用。 例如，若您建立了可序列化包含信用卡號碼之訂單的應用程式，這種資料就是高度敏感。 若想要防止它的發生，時時保護資料存放區並採取步驟保持它的私密性。

## <a name="serialization-of-a-simple-class"></a>簡單類別序列化

以下程式碼範例所示為具有公用欄位的基本類別。

```vb
Public Class OrderForm
    Public OrderDate As DateTime
End Class
```

```csharp
public class OrderForm
{
    public DateTime OrderDate;
}
```

此類別的執行個體序列化後，可能類似於下列項目。

```xml
<OrderForm>
    <OrderDate>12/12/01</OrderDate>
</OrderForm>
```

如需更多序列化範例，請參閱 [XML 序列化範例](examples-of-xml-serialization.md)。

## <a name="items-that-can-be-serialized"></a>可序列化的項目

下列項目可以使用 **XmLSerializer** 類別加以序列化：

- 共用讀/寫屬性與公用類別的欄位。

- 可實作 **ICollection** 或 **IEnumerable** 的類別。

  > [!NOTE]
  > 只序列化集合，公用屬性除外。

- **XmlElement** 物件。

- **XmlNode** 物件。

- **DataSet** 物件。

 如需序列化或還原序列化物件的詳細資訊，請參閱[如何：序列化物件](how-to-serialize-an-object.md)和[如何：還原序列化物件](how-to-deserialize-an-object.md)。

## <a name="advantages-of-using-xml-serialization"></a>使用 XML 序列化的優點

**XmlSerializer**類別可讓您完整而靈活地控制當您序列化物件為 XML。 若您建立 XML Web 服務，可套用控制序列化的屬性至類別與成員，以確保 XML 輸出符合特定結構描述。

例如， **XmlSerializer** 可讓您：

- 指定欄位或屬性 (Property) 是否要編碼為屬性 (Attribute) 或項目。

- 指定要使用的 XML 命名空間。

- 指定若欄位或屬性 (Property) 名稱不當時，項目或屬性 (Attribute) 的名稱。

XML 序列化的另一項優點是對於您開發的應用程式沒有限制，只要產生的 XML 資料流符合指定的結構描述即可。 試想用來描述書本的結構描述。 它有書名、作者、發行商和 ISBN 編號項目。 您可開發應用程式，以您想要的任何方式處理 XML 資料，例如書本訂單或書本庫存。 無論是哪一種情況，唯一的要求是 XML 資料流符合指定的 XML 結構描述定義語言 (XSD) 結構描述。

## <a name="xml-serialization-considerations"></a>XML 序列化考量

使用 **XmlSerializer** 類別時，應考量下列項目：

- Sgen.exe 工具是特別為了產生序列化組件以達到最佳效能而設計。

- 序列化資料僅包含資料本身以及您類別的結構。 不包括型別識別與組件資訊。

- 只可以序列化公用 (Public) 屬性和欄位。 屬性必須有公用存取子 (get 與 set 方法)。 若您必須對非公用資料序列化，請使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別，而非 XML 序列化。

- 類別必須有由 **XmlSerializer** 序列化的預設建構函式。

- 無法將方法序列化。

- **XmlSerializer** 可以處理的類別是，當 **IEnumerable** 或 **ICollection** 符合特定需求時，這些類別可以不同的方式實作它們，如下所示。

  實作 **IEnumerable** 的類別必須實作只採用單一參數的公用 **Add** 方法。 **Add** 方法的參數必須與 **IEnumerator.Current** 屬性傳回之類型一致 (多型)，此屬性是由 **GetEnumerator** 方法傳回。

  除了 **IEnumerable** 之外，實作 **ICollection** 的類別 (例如 **CollectionBase**) 也必須有採用整數的公用 **Item** 索引屬性 (C# 的索引子)，而且必須具有 **integer** 類型的公用 **Count** 屬性。 傳遞給 **Add** 方法的參數必須和 **Item** 屬性或其中一個類型基底所傳回的類型相同。

  針對實作 **ICollection** 的類別，要序列化的值擷取自索引的 **Item** 屬性，而不是呼叫 **GetEnumerator** 進行擷取。 同時，不序列化公用欄位與屬性，但傳回其他集合類別 (實作 **ICollection**) 的公用欄位除外。 如需範例，請參閱 [XML 序列化範例](examples-of-xml-serialization.md)。

## <a name="xsd-data-type-mapping"></a>XSD 資料型別對應

W3C 文件[XML 結構描述第 2 部分： 資料型別](https://www.w3.org/TR/xmlschema-2/)XML 結構描述定義語言 (XSD) 結構描述中指定允許的簡單資料類型。 許多這些資料類型 (例如，**int** 和 **decimal**)，在 .NET Framework 都有對應的資料類型。 然而，某些 XML 資料類型在 .NET Framework 中並無對應的資料類型 (例如 **NMTOKEN** 資料類型)。 在這種情況下，若您使用 XML 結構描述定義工具 ([XML 結構描述定義工具 (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) 從結構描述產生類別，將套用適當的屬性至類型字串的成員，且它的 **DataType** 屬性會設為 XML 資料類型名稱。 例如，若結構描述包括具有 XML 資料類型 **NMTOKEN** 之名為 "MyToken" 的項目，產生的類別可能包含下列範例所示的成員。

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

同樣地，若您建立必須符合特定 XML 結構描述 (XSD) 的類別，您應套用適當的屬性並將它的 **DataType** 屬性設為想要的 XML 資料類型名稱。

如需類型對應的完整清單，請參閱下列任一屬性 (attribute) 類別的 **DataType** 屬性 (property)：

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.IO.FileStream>
- [XML 和 SOAP 序列化](xml-and-soap-serialization.md)
- [二進位序列化](binary-serialization.md)
- [序列化](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [XML 序列化範例](examples-of-xml-serialization.md)
- [如何：序列化物件](how-to-serialize-an-object.md)
- [如何：還原序列化物件](how-to-deserialize-an-object.md)
