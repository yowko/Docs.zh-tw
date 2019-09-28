---
title: XML Schema Definition Tool (Xsd.exe)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 7a27b05a12017a3c0de6b0d036f480b3e7fdeda7
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392736"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>XML Schema Definition Tool (Xsd.exe)

XML 結構描述定義工具 (Xsd.exe) 可以從 XDR、XML 和 XSD 檔案或從執行階段組件的類別中，產生 XML 結構描述或 Common Language Runtime 類別。

## <a name="syntax"></a>語法

```console
xsd file.xdr [/outputdir:directory][/parameters:file.xml]
xsd file.xml [/outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```

## <a name="argument"></a>引數

|引數|描述|
|--------------|-----------------|
|*file.extension*|指定要轉換的輸入檔。 您必須將此延伸模組指定為下列其中一項： xdr、.xml、.xsd、.dll 或 .exe。<br /><br /> 如果指定 XDR 結構描述檔 (副檔名為 .xdr )，Xsd.exe 會將 XDR 結構描述轉換成 XSD 結構描述。 輸出檔有和 XDR 結構描述一樣的名稱，但是具有 .xsd 副檔名。<br /><br /> 如果指定 XML 檔 (副檔名為 .xml )，Xsd.exe 會從檔案中的資料推斷結構描述，然後產生 XSD 結構描述。 輸出檔有和 XML 檔一樣的名稱，但是具有 .xsd 副檔名。<br /><br /> 如果指定 XML 結構描述檔 (.xsd 副檔名)，Xsd.exe 會產生對應到 XML 結構描述之 Runtime 物件的原始程式碼。<br /><br /> 如果指定執行階段組件檔 (.exe 或 .dll 副檔名)，Xsd.exe 會產生該組件中一個或多個型別的結構描述。 您可以使用 `/type` 選項來指定要產生結構描述的型別。 輸出結構描述被命名為 schema0.xsd、schema1.xsd 等等。 只有在指定的型別使用 `XMLRoot` 自訂屬性來指定命名空間 (Namespace) 時，Xsd.exe 才能產生多個結構描述。|

## <a name="general-options"></a>一般選項

|選項|描述|
|------------|-----------------|
|**/h @ no__t-1elp @ no__t-2**|顯示工具的命令語法和選項。|
|**/o @ no__t-1utputdir @ no__t-2：** _directory_|指定輸出檔的目錄。 這個引數只可以使用一次。 預設為目前的目錄。|
|**/?**|顯示工具的命令語法和選項。|
|**/p\[arameters\]:** _file.xml_|從指定的 .xml 檔案，讀取各種作業模式的選項。 簡短形式為 `/p:`。 如需詳細資訊，請參閱[備註](#remarks)一節。|

## <a name="xsd-file-options"></a>XSD 檔案選項
 您只能為 .xsd 檔指定下列其中一個選項：

|選項|描述|
|------------|-----------------|
|**/c\[lasses\]**|產生對應到指定的結構描述的類別。 若要將 XML 資料讀入物件，請使用 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。|
|**/d\[ataset\]**|產生衍生自 <xref:System.Data.DataSet> 的類別，對應到指定的結構描述。 若要將 XML 資料讀入衍生類別，請使用 <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> 方法。|

 您也可以為 .xsd 檔指定下列任何選項：

|選項|描述|
|------------|-----------------|
|**/e @ no__t-1lement @ no__t-2：** _element_|指定所要產生程式碼的結構描述中的項目。 根據預設，會輸入所有項目。 您可以多次指定這個引數。|
|**/enableDataBinding**|在所有產生的型別上實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，以啟用資料繫結 (Data Binding)。 簡短形式為 `/edb`。|
|**/enableLinqDataSet**|(簡短形式：`/eld`)。指定產生的 DataSet 可使用 LINQ to DataSet 查詢。 如果也指定了 /dataset 選項，就會使用這個選項。 如需詳細資訊，請參閱 [LINQ to DataSet 概觀](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)和[查詢具類型資料集](../../../docs/framework/data/adonet/querying-typed-datasets.md)。 如需使用 LINQ 的一般資訊，請參閱[語言整合式查詢（linq C# ）-](../../csharp/programming-guide/concepts/linq/index.md)或[語言整合式查詢（linq）-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)。|
|**/f\[ields\]**|產生欄位，而不是產生屬性。 根據預設，會產生屬性。|
|**/l @ no__t-1anguage @ no__t-2：** _language_|指定要使用的程式語言。 可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。 您也可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 的類別指定完整名稱。|
|**/n\[amespace\]:** _namespace_|指定產生的型別的執行階段命名空間。 預設命名空間是 `Schemas`。|
|**/nologo**|隱藏產品啟始畫面。|
|**/order**|在所有物件成員上產生明確順序識別項。|
|**/o @ no__t-1ut @ no__t-2：** _directoryName_|指定要在其中放置檔案的輸出目錄。 預設為目前的目錄。|
|**/u @ no__t-1ri @ no__t-2：** _uri_|指定所要產生程式碼的結構描述中項目的 URI。 這個 URI 如果存在，會套用到所有以 `/element` 選項指定的項目。|

## <a name="dll-and-exe-file-options"></a>DLL 和 EXE 檔案選項

|選項|描述|
|------------|-----------------|
|**/t\[ype\]:** _typename_|指定所要建立結構描述的型別名稱。 您可以指定多個型別引數。 如果 *typename* 沒有指定命名空間，Xsd.exe 會以指定的類型比對組件中的所有類型。 如果 *typename* 指定命名空間，只有該類型會被比對。 如果 *typename* 結尾為星號字元 (\*)，則工具會比對 \* 之前以這個字串為開頭的所有類型。 如果省略 `/type` 選項，Xsd.exe 會產生組件中所有型別的結構描述。|

## <a name="remarks"></a>備註

下表列出 Xsd.exe 執行的作業。

| | |
|------------|-----------------|
|XDR 轉換成 XSD|從 XML-Data-Reduced 結構描述檔中產生 XML 結構描述。 XDR 是早期 XML 架構的結構描述。|
|XML 轉換成 XSD|從 XML 檔案中產生 XML 結構描述。|
|XSD 轉換成 DataSet|從 XSD 結構描述檔中產生 Common Language Runtime <xref:System.Data.DataSet> 類別。 產生的類別為一般 XML 資料提供了豐富的物件模型。|
|XSD 轉換成類別|從 XSD 結構描述檔中產生執行階段類別。 產生的類別可以配合 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 使用，以讀取和寫入遵循結構描述的 XML 程式碼。|
|類別轉換成 XSD| 從型別或執行階段組件檔中的型別中產生 XML 結構描述。 產生的架構會定義 <xref:System.Xml.Serialization.XmlSerializer> 所使用的 XML 格式。|

 Xsd.exe 只允許您操作遵循 XML 結構描述定義 (XSD) 語言的 XML 結構描述，而這個 XSD 語言是由全球資訊網協會 (W3C) 所提出的。 如需 XML 架構定義提案或 XML 標準的詳細資訊，請參閱 <https://w3.org>。

## <a name="setting-options-with-an-xml-file"></a>設定 XML 檔案的選項

使用 `/parameters` 參數時，您可以指定會設定各種選項的單一 XML 檔案。 您可以設定的選項會視使用 XSD.exe 工具的方式而定。 這些選擇包括產生結構描述、產生程式碼檔或產生內含 `DataSet` 功能的程式碼檔。 例如，您可以在產生結構描述時 (但不是在產生程式碼檔案時)，將 `<assembly>` 項目設為可執行檔 (.exe) 或型別程式庫 (.dll) 檔案的名稱。 下列 XML 會顯示如何使用 `<generateSchemas>` 項目搭配指定的可執行檔：

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

如果前一個 XML 內含在名為 GenerateSchemas.xml 的檔案中，則在命令提示字元中鍵入下列命令，並按 ENTER 鍵，就可以使用 `/parameters` 參數：

```console
 xsd /p:GenerateSchemas.xml
```

換句話說，如果針對在組件中找到的單一型別產生結構描述，就可以使用下列 XML：

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

但是若要使用之前的程式碼，您也必須在命令提示字元中提供組件的名稱。 在命令提示字元中輸入下列命令 (假設 XML 檔案的名稱為 GenerateSchemaFromType.xml)：

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

您只能為 `<generateSchemas>` 項目指定下列其中一個選項。

|元素|描述|
|-------------|-----------------|
|\<assembly>|指定要產生結構描述的組件。|
|\<type>|指定在組件中找到的型別，以用於產生結構描述。|
|\<xml>|指定用於產生結構描述的 XML 檔案。|
|\<xdr >|指定用於產生結構描述的 XDR 檔案。|

若要產生程式碼檔，請使用 `<generateClasses>` 項目。 下列範例會產生程式碼檔。 請注意，也會顯示兩個屬性，可讓您設定所產生檔案的程式設計語言和命名空間。

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 您可以對 `<generateClasses>` 項目設定的選項包括下列各項。

|元素|描述|
|-------------|-----------------|
|\<element>|指定要產生程式碼之 .xsd 檔案中的項目。|
|\<schemaImporterExtensions>|指定衍生自 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 類別的型別。|
|\<schema>|指定用於產生程式碼的 XML 結構描述檔案。 多個 XML 結構描述檔案可以使用多個 \<schema> 元素指定。|

下表顯示也可以和 `<generateClasses>` 項目搭配使用的屬性。

|屬性|描述|
|---------------|-----------------|
|language|指定要使用的程式語言。 可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。 您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。|
|namespace|指定產生之程式碼的命名空間。 命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。|
|options|下列其中一個值：`none`、`properties` (產生屬性而非公用欄位)、`order` 或 `enableDataBinding` (請參閱先前＜XSD 檔案選項＞一節中的 `/order` 和 `/enableDataBinding` 參數)。|

 您也可以使用 `DataSet` 項目，控制產生 `<generateDataSet>` 程式碼的方法。 下列 XML 會指定產生的程式碼會使用 `DataSet` 結構（例如 <xref:System.Data.DataTable> 類別）來建立所指定專案 Visual Basic 程式碼。 所產生的 DataSet 結構將會支援 LINQ 查詢。

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

您可以對 `<generateDataSet>` 項目設定的選項包括下列各項。

|元素|描述|
|-------------|-----------------|
|\<schema>|指定用於產生程式碼的 XML 結構描述檔案。 多個 XML 結構描述檔案可以使用多個 \<schema> 元素指定。|

 下表顯示可以和 `<generateDataSet>` 項目搭配使用的屬性。

|屬性|描述|
|---------------|-----------------|
|enableLinqDataSet|指定產生的 DataSet 可使用 LINQ to DataSet 查詢。 預設值為 false。|
|language|指定要使用的程式語言。 可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。 您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。|
|namespace|指定產生之程式碼的命名空間。 命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。|

 在最上層 `<xsd>` 項目中有一些您可以設定的屬性。 這些選項可以和任何子項目搭配使用 (`<generateSchemas>`、`<generateClasses>` 或 `<generateDataSet>`)。 下列 XML 程式碼會對名為 "IDItems" 的項目，在名為 "MyOutputDirectory" 的輸出目錄中產生程式碼。

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

下表顯示也可以和 `<xsd>` 項目搭配使用的屬性。

|屬性|描述|
|---------------|-----------------|
|output|將放置產生的結構描述或程式碼檔的目錄名稱。|
|nologo|隱藏產品啟始畫面。 設為 `true` 或 `false`。|
|help|顯示工具的命令語法和選項。 設為 `true` 或 `false`。|

## <a name="examples"></a>範例
 下列命令會從 `myFile.xdr` 產生 XML 結構描述，並將它儲存到目前的目錄。

```console
xsd myFile.xdr
```

下列命令會從 `myFile.xml` 產生 XML 結構描述，並將它儲存到指定的目錄。

```console
xsd myFile.xml /outputdir:myOutputDir
```

下列命令會產生對應到以 C# 語言指定之結構描述的資料集，並在目前的目錄中將它儲存為 `XSDSchemaFile.cs`。

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

下列命令會對 `myAssembly.dll` 組件中的所有型別產生 XML 結構描述，並在目前的目錄中將它們儲存為 `schema0.xsd`。

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [工具](../../../docs/framework/tools/index.md)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [LINQ to DataSet 概觀](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [查詢具類型資料集](../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [LINQ （語言整合式查詢）（C#）](../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ （語言整合式查詢）（Visual Basic）](../../visual-basic/programming-guide/concepts/linq/index.md)
