---
title: 資料集和 DataTable 安全性指引
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: c6b32afeadccc3fd22d6611d282840233280440f
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86382453"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="e63c0-102">資料集和 DataTable 安全性指引</span><span class="sxs-lookup"><span data-stu-id="e63c0-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="e63c0-103">本文適用于：</span><span class="sxs-lookup"><span data-stu-id="e63c0-103">This article applies to:</span></span>

* <span data-ttu-id="e63c0-104">.NET Framework （所有版本）</span><span class="sxs-lookup"><span data-stu-id="e63c0-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="e63c0-105">.NET Core 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e63c0-105">.NET Core and later</span></span>
* <span data-ttu-id="e63c0-106">.NET 5.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e63c0-106">.NET 5.0 and later</span></span>

<span data-ttu-id="e63c0-107">[DataSet](/dotnet/api/system.data.dataset)和[DataTable](/dotnet/api/system.data.datatable)類型是舊版的 .net 元件，可將資料集表示為 managed 物件。</span><span class="sxs-lookup"><span data-stu-id="e63c0-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="e63c0-108">這些元件是在 .NET 1.0 中引進，做為原始[ADO.NET 基礎結構](/dotnet/framework/data/adonet/dataset-datatable-dataview/)的一部分。</span><span class="sxs-lookup"><span data-stu-id="e63c0-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span></span> <span data-ttu-id="e63c0-109">其目標是要提供關聯式資料集的受控視圖，並將資料的基礎來源抽象化為 XML、SQL 或其他技術。</span><span class="sxs-lookup"><span data-stu-id="e63c0-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="e63c0-110">如需 ADO.NET 的詳細資訊，包括更多現代化的資料檢視範例，請參閱[ADO.NET 檔](/dotnet/framework/data/adonet/)。</span><span class="sxs-lookup"><span data-stu-id="e63c0-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](/dotnet/framework/data/adonet/).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="e63c0-111">從 XML 還原序列化 DataSet 或 DataTable 時的預設限制</span><span class="sxs-lookup"><span data-stu-id="e63c0-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="e63c0-112">在所有支援的 .NET Framework、.NET Core 和 .NET 版本上，針對還原序列化 `DataSet` `DataTable` 資料中可能出現的物件類型，施加下列限制。</span><span class="sxs-lookup"><span data-stu-id="e63c0-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="e63c0-113">根據預設，此清單僅限於：</span><span class="sxs-lookup"><span data-stu-id="e63c0-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="e63c0-114">基本和基本對等專案： `bool` 、 `char` 、 `sbyte` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `byte` `short` `ushort` `int` `uint` `long` `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` 和 `SqlString` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="e63c0-115">常用的非基本類型： `Type` 、 `Uri` 和 `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="e63c0-116">常用的_系統。繪圖_類型： `Color` 、 `Point` 、 `PointF` 、 `Rectangle` 、 `RectangleF` 、 `Size` 和 `SizeF` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="e63c0-117">`Enum`各種.</span><span class="sxs-lookup"><span data-stu-id="e63c0-117">`Enum` types.</span></span>
* <span data-ttu-id="e63c0-118">上述類型的陣列和清單。</span><span class="sxs-lookup"><span data-stu-id="e63c0-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="e63c0-119">如果傳入的 XML 資料包含的物件的類型不在此清單中：</span><span class="sxs-lookup"><span data-stu-id="e63c0-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="e63c0-120">隨即擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e63c0-120">An exception is thrown.</span></span>
* <span data-ttu-id="e63c0-121">還原序列化操作失敗。</span><span class="sxs-lookup"><span data-stu-id="e63c0-121">The deserialization operation fails.</span></span>

<span data-ttu-id="e63c0-122">將 XML 載入到現有的 `DataSet` 或 `DataTable` 實例時，也會將現有的資料行定義納入考慮。</span><span class="sxs-lookup"><span data-stu-id="e63c0-122">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="e63c0-123">如果資料表已經包含自訂類型的資料行定義，則該類型會暫時加入至 XML 還原序列化作業期間的允許清單。</span><span class="sxs-lookup"><span data-stu-id="e63c0-123">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

<span data-ttu-id="e63c0-124">當您使用來還原序列化或的實例時，也適用物件類型限制 `XmlSerializer` `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-124">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="e63c0-125">不過，使用來還原序列化或的實例時，可能不適用這些限制 `BinaryFormatter` `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-125">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="e63c0-126">使用時，不適用物件類型限制 `DataAdapter.Fill` ，例如 `DataTable` 直接從資料庫填入實例時，不使用 XML 還原序列化 api。</span><span class="sxs-lookup"><span data-stu-id="e63c0-126">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="e63c0-127">擴充允許類型的清單</span><span class="sxs-lookup"><span data-stu-id="e63c0-127">Extend the list of allowed types</span></span>

<span data-ttu-id="e63c0-128">除了以上所列的內建類型之外，應用程式可以擴充允許的類型清單來包含自訂類型。</span><span class="sxs-lookup"><span data-stu-id="e63c0-128">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="e63c0-129">如果擴充允許的類型清單，變更會影響_all_ `DataSet` `DataTable` 應用程式內的所有和實例。</span><span class="sxs-lookup"><span data-stu-id="e63c0-129">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="e63c0-130">無法從內建的允許類型清單中移除類型。</span><span class="sxs-lookup"><span data-stu-id="e63c0-130">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="e63c0-131">透過設定擴充（.NET Framework 4.0-4.8）</span><span class="sxs-lookup"><span data-stu-id="e63c0-131">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="e63c0-132">_App.config_可以用來擴充允許的類型清單。</span><span class="sxs-lookup"><span data-stu-id="e63c0-132">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="e63c0-133">若要擴充允許的類型清單：</span><span class="sxs-lookup"><span data-stu-id="e63c0-133">To extend the allowed types list:</span></span>

* <span data-ttu-id="e63c0-134">使用專案 `<configSections>` ，將參考加入至_system.object_設定區段。</span><span class="sxs-lookup"><span data-stu-id="e63c0-134">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="e63c0-135">使用 `<system.data.dataset.serialization>` / `<allowedTypes>` 來指定其他類型。</span><span class="sxs-lookup"><span data-stu-id="e63c0-135">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="e63c0-136">每個 `<add>` 元素都只能使用其元件限定類型名稱來指定一個類型。</span><span class="sxs-lookup"><span data-stu-id="e63c0-136">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="e63c0-137">若要將其他類型新增至允許的類型清單，請使用多個 `<add>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e63c0-137">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="e63c0-138">下列範例顯示如何藉由新增自訂類型來擴充允許的類型清單 `Fabrikam.CustomType` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-138">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="e63c0-139">若要取得類型的元件限定名稱，請使用[AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname)屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e63c0-139">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="e63c0-140">透過設定擴充（.NET Framework 2.0-3.5）</span><span class="sxs-lookup"><span data-stu-id="e63c0-140">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="e63c0-141">如果您的應用程式以 .NET Framework 2.0 或3.5 為目標，您仍然可以使用上述_App.config_機制來擴充允許的類型清單。</span><span class="sxs-lookup"><span data-stu-id="e63c0-141">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="e63c0-142">不過，您 `<configSections>` 的元素看起來會稍有不同，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-142">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="e63c0-143">以程式設計方式擴充（.NET Framework、.NET Core、.NET 5.0 +）</span><span class="sxs-lookup"><span data-stu-id="e63c0-143">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="e63c0-144">您也可以使用_DataSetDefaultAllowedTypes_ [，以程式](/dotnet/api/system.appdomain.setdata)設計方式擴充允許的類型清單，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e63c0-144">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="e63c0-145">如果使用延伸模組機制，則與金鑰_DataSetDefaultAllowedTypes_相關聯的值必須是類型 `Type[]` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-145">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="e63c0-146">在 .NET Framework 上，允許的類型清單可使用_App.config_和進行擴充 `AppDomain.SetData` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-146">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="e63c0-147">在此情況下， `DataSet` 和 `DataTable` 會允許將物件還原序列化為數據的一部分（如果其中一個清單中有其類型的話）。</span><span class="sxs-lookup"><span data-stu-id="e63c0-147">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="e63c0-148">以 audit 模式執行應用程式（.NET Framework）</span><span class="sxs-lookup"><span data-stu-id="e63c0-148">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="e63c0-149">在 .NET Framework 中， `DataSet` 並 `DataTable` 提供「稽核模式」功能。</span><span class="sxs-lookup"><span data-stu-id="e63c0-149">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="e63c0-150">啟用 audit 模式時，會 `DataSet` 將 `DataTable` 傳入物件的類型與允許的類型清單進行比較。</span><span class="sxs-lookup"><span data-stu-id="e63c0-150">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="e63c0-151">不過，如果看到不允許其類型的物件，則**不**會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e63c0-151">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="e63c0-152">相反 `DataSet` 地，和 `DataTable` 會通知任何附加的 `TraceListener` 實例有可疑的類型存在，讓 `TraceListener` 能夠記錄此資訊。</span><span class="sxs-lookup"><span data-stu-id="e63c0-152">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="e63c0-153">不會擲回任何例外狀況，而且還原序列化作業會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e63c0-153">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="e63c0-154">以「audit mode」執行應用程式應該只是用於測試的暫時量值。</span><span class="sxs-lookup"><span data-stu-id="e63c0-154">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="e63c0-155">啟用 audit 模式時， `DataSet` 並 `DataTable` 不會強制執行類型限制，這可能會在您的應用程式內引進安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="e63c0-155">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="e63c0-156">如需詳細資訊，請參閱標題為[不受信任的輸入](#swr)[移除所有類型限制](#ratr)和安全性的章節。</span><span class="sxs-lookup"><span data-stu-id="e63c0-156">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="e63c0-157">您可以透過_App.config_來啟用 Audit 模式：</span><span class="sxs-lookup"><span data-stu-id="e63c0-157">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="e63c0-158">請參閱本檔中的[擴充到](#etc)設定一節，以取得要為元素放置之適當值的相關資訊 `<configSections>` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-158">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="e63c0-159">使用 `<allowedTypes auditOnly="true">` 來啟用 audit 模式，如下列標記所示。</span><span class="sxs-lookup"><span data-stu-id="e63c0-159">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="e63c0-160">啟用 audit 模式之後，您就可以使用_App.config_ ，將慣用的 `TraceListener` 內建 `DataSet` `TraceSource.` 追蹤來源名稱連接到_system.web. Data. DataSet_。</span><span class="sxs-lookup"><span data-stu-id="e63c0-160">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="e63c0-161">下列範例示範如何將追蹤事件寫入主控台_和_磁片上的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e63c0-161">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

<span data-ttu-id="e63c0-162">如需和的詳細資訊 `TraceSource` `TraceListener` ，請參閱檔 how [To：搭配追蹤接聽項使用 TraceSource 和篩選](/dotnet/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners)。</span><span class="sxs-lookup"><span data-stu-id="e63c0-162">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](/dotnet/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners).</span></span>

<span data-ttu-id="e63c0-163">**注意**：在「audit 模式」中執行應用程式無法在 .net Core 中使用，或在 .net 5.0 和更新版本中提供。</span><span class="sxs-lookup"><span data-stu-id="e63c0-163">**Note**: Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="e63c0-164">移除所有類型限制</span><span class="sxs-lookup"><span data-stu-id="e63c0-164">Remove all type restrictions</span></span>

<span data-ttu-id="e63c0-165">如果應用程式必須從和移除所有類型限制 `DataSet` 限制 `DataTable` ：</span><span class="sxs-lookup"><span data-stu-id="e63c0-165">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="e63c0-166">有數個選項可隱藏類型限制限制。</span><span class="sxs-lookup"><span data-stu-id="e63c0-166">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="e63c0-167">可用的選項取決於應用程式的目標架構。</span><span class="sxs-lookup"><span data-stu-id="e63c0-167">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="e63c0-168">移除所有類型的限制可能會在應用程式內引進安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="e63c0-168">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="e63c0-169">使用這種機制時，請確定應用**程式不會使用** `DataSet` 或 `DataTable` 來讀取不受信任的輸入。</span><span class="sxs-lookup"><span data-stu-id="e63c0-169">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="e63c0-170">如需詳細資訊，請參閱[CVE-2020-1147](https://portal.msrc.microsoft.com/security-guidance/advisory/CVE-2020-1147) ，以及[與不受信任的輸入有關](#swr)的下一節標題為安全。</span><span class="sxs-lookup"><span data-stu-id="e63c0-170">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="e63c0-171">透過 AppCoNtext 設定（.NET Framework 4.6-4.8、.NET Core 2.1 和更新版本、.NET 5.0 和更新版本）</span><span class="sxs-lookup"><span data-stu-id="e63c0-171">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="e63c0-172">`AppContext` `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` 當設定為時，會 `true` 從和移除所有類型限制限制的參數 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-172">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="e63c0-173">在 .NET Framework 中，可以透過_App.config_啟用此交換器，如下列設定所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-173">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="e63c0-174">在 ASP.NET 中， `<AppContextSwitchOverrides>` 無法使用元素。</span><span class="sxs-lookup"><span data-stu-id="e63c0-174">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="e63c0-175">相反地，您可以透過_Web.config_來啟用參數，如下列設定所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-175">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="e63c0-176">如需詳細資訊，請參閱 [\<AppContextSwitchOverrides>](/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) 元素。</span><span class="sxs-lookup"><span data-stu-id="e63c0-176">For more information, see the [\<AppContextSwitchOverrides>](/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) element.</span></span>

<span data-ttu-id="e63c0-177">在 .NET Core、.NET 5 和 ASP.NET Core 中，這項設定是由_上的runtimeconfig.js_所控制，如下列 JSON 所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-177">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="e63c0-178">如需詳細資訊，請參閱[.Net Core 執行時間設定](/dotnet/core/run-time-config/)值。</span><span class="sxs-lookup"><span data-stu-id="e63c0-178">For more information, see [".NET Core run-time configuration settings"](/dotnet/core/run-time-config/).</span></span>

<span data-ttu-id="e63c0-179">`AllowArbitraryDataSetTypeInstantiation`也可以透過[AppCoNtext](/dotnet/api/system.appcontext.setswitch)以程式設計方式設定，而不是使用設定檔，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-179">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="e63c0-180">如果您選擇上述的程式設計方法，對的呼叫 `AppContext.SetSwitch` 應該會在應用程式啟動時提早發生。</span><span class="sxs-lookup"><span data-stu-id="e63c0-180">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="e63c0-181">透過整部電腦的登錄（.NET Framework 2.0-4.8）</span><span class="sxs-lookup"><span data-stu-id="e63c0-181">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="e63c0-182">如果 `AppContext` 無法使用，可以使用 Windows 登錄來停用類型限制檢查：</span><span class="sxs-lookup"><span data-stu-id="e63c0-182">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="e63c0-183">系統管理員必須設定登錄。</span><span class="sxs-lookup"><span data-stu-id="e63c0-183">An administrator must configure the registry.</span></span>
* <span data-ttu-id="e63c0-184">使用登錄是全電腦的變更，將會影響在機器上執行的_所有_應用程式。</span><span class="sxs-lookup"><span data-stu-id="e63c0-184">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="e63c0-185">類型</span><span class="sxs-lookup"><span data-stu-id="e63c0-185">Type</span></span>  |  <span data-ttu-id="e63c0-186">值</span><span class="sxs-lookup"><span data-stu-id="e63c0-186">Value</span></span> |
|---|---|
| <span data-ttu-id="e63c0-187">**登錄機碼**</span><span class="sxs-lookup"><span data-stu-id="e63c0-187">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="e63c0-188">**值名稱**</span><span class="sxs-lookup"><span data-stu-id="e63c0-188">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="e63c0-189">**值類型**</span><span class="sxs-lookup"><span data-stu-id="e63c0-189">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="e63c0-190">**值資料**</span><span class="sxs-lookup"><span data-stu-id="e63c0-190">**Value data**</span></span> | `true` |

<span data-ttu-id="e63c0-191">在64位的作業系統上，我需要為64位金鑰（如上所示）和32位金鑰新增這兩個值。</span><span class="sxs-lookup"><span data-stu-id="e63c0-191">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="e63c0-192">32位金鑰位於 `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-192">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="e63c0-193">如需使用登錄進行設定的詳細資訊 `AppContext` ，請參閱「連結[庫取用者的 AppCoNtext](/dotnet/api/system.appcontext#appcontext-for-library-consumers)」。</span><span class="sxs-lookup"><span data-stu-id="e63c0-193">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="e63c0-194">與不受信任的輸入有關的安全性</span><span class="sxs-lookup"><span data-stu-id="e63c0-194">Safety with regard to untrusted input</span></span>

<span data-ttu-id="e63c0-195">雖然和會對在還原 `DataSet` `DataTable` 序列化 XML 裝載時允許出現的類型強加預設限制，但__ `DataSet` `DataTable` 在填入不受信任的輸入時，一般不安全。__</span><span class="sxs-lookup"><span data-stu-id="e63c0-195">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="e63c0-196">以下是 `DataSet` 或 `DataTable` 實例可能會讀取不受信任的輸入之方式的不完整清單。</span><span class="sxs-lookup"><span data-stu-id="e63c0-196">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="e63c0-197">`DataAdapter`會參考資料庫，而 `DataAdapter.Fill` 方法則是用來在中填入 `DataSet` 資料庫查詢的內容。</span><span class="sxs-lookup"><span data-stu-id="e63c0-197">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="e63c0-198">`DataSet.ReadXml`或 `DataTable.ReadXml` 方法是用來讀取包含資料行和資料列資訊的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="e63c0-198">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="e63c0-199">`DataSet`或 `DataTable` 實例會序列化為 ASP.NET （SOAP） web 服務或 WCF 端點的一部分。</span><span class="sxs-lookup"><span data-stu-id="e63c0-199">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="e63c0-200">序列化程式（例如） `XmlSerializer` 是用來 `DataSet` `DataTable` 從 XML 資料流程還原序列化或實例。</span><span class="sxs-lookup"><span data-stu-id="e63c0-200">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="e63c0-201">序列化程式（例如） `JsonConvert` 是用來 `DataSet` `DataTable` 從 JSON 資料流程還原序列化或實例。</span><span class="sxs-lookup"><span data-stu-id="e63c0-201">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="e63c0-202">`JsonConvert`是常用的協力廠商[Newtonsoft.Js](https://www.newtonsoft.com/json)程式庫中的方法。</span><span class="sxs-lookup"><span data-stu-id="e63c0-202">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="e63c0-203">序列化程式（例如） `BinaryFormatter` 是用來 `DataSet` `DataTable` 從原始位元組資料流程還原序列化或實例。</span><span class="sxs-lookup"><span data-stu-id="e63c0-203">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="e63c0-204">本檔討論先前案例的安全性考慮。</span><span class="sxs-lookup"><span data-stu-id="e63c0-204">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="e63c0-205">用 `DataAdapter.Fill` 來 `DataSet` 從不受信任的資料來源填入</span><span class="sxs-lookup"><span data-stu-id="e63c0-205">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="e63c0-206">您 `DataSet` 可以 `DataAdapter` 使用[ `DataAdapter.Fill` 方法](/dotnet/api/system.data.common.dataadapter.fill)，從填入實例，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e63c0-206">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="e63c0-207">（上述程式碼範例是在[從 DataAdapter 填入資料集中](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter)找到之較大範例的一部分）。</span><span class="sxs-lookup"><span data-stu-id="e63c0-207">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).)</span></span>

> <span data-ttu-id="e63c0-208">大部分的應用程式都可以簡化並假設其資料庫層是受信任的。</span><span class="sxs-lookup"><span data-stu-id="e63c0-208">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="e63c0-209">不過，如果您的應用程式是[威脅](https://www.microsoft.com/securityengineering/sdl/threatmodeling)模型化的習慣，您的威脅模型可能會考慮到應用程式（用戶端）和資料庫層（伺服器）之間的信任界限。</span><span class="sxs-lookup"><span data-stu-id="e63c0-209">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="e63c0-210">使用[相互驗證](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections)或用戶端與伺服器之間的[AAD 驗證](/azure/azure-sql/database/authentication-aad-overview)，是協助解決與此相關聯之風險的一種方式。</span><span class="sxs-lookup"><span data-stu-id="e63c0-210">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="e63c0-211">本節的其餘部分將討論用戶端連接到不受信任的伺服器時可能產生的結果。</span><span class="sxs-lookup"><span data-stu-id="e63c0-211">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="e63c0-212">將指向 `DataAdapter` 不受信任資料來源的結果取決於本身的執行 `DataAdapter` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-212">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="e63c0-213">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="e63c0-213">SqlDataAdapter</span></span>

<span data-ttu-id="e63c0-214">針對內建類型[SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)，參考不受信任的資料來源可能會導致拒絕服務（DoS）攻擊。</span><span class="sxs-lookup"><span data-stu-id="e63c0-214">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="e63c0-215">DoS 攻擊可能會導致應用程式變得沒有回應或損毀。</span><span class="sxs-lookup"><span data-stu-id="e63c0-215">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="e63c0-216">如果攻擊者可以將 DLL 與應用程式一起植入，他們也可以達到本機程式碼執行的能力。</span><span class="sxs-lookup"><span data-stu-id="e63c0-216">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="e63c0-217">其他 DataAdapter 類型</span><span class="sxs-lookup"><span data-stu-id="e63c0-217">Other DataAdapter types</span></span>

<span data-ttu-id="e63c0-218">協力廠商的 `DataAdapter` 執行必須自行評估其在臉部不受信任的輸入時，所提供的安全性保證。</span><span class="sxs-lookup"><span data-stu-id="e63c0-218">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="e63c0-219">.NET 無法針對這些執行提供任何安全保證。</span><span class="sxs-lookup"><span data-stu-id="e63c0-219">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="e63c0-220">ReadXml 和 DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="e63c0-220">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="e63c0-221">`DataSet.ReadXml`與不 `DataTable.ReadXml` 受信任的輸入搭配使用時，和方法不安全。</span><span class="sxs-lookup"><span data-stu-id="e63c0-221">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="e63c0-222">我們強烈建議取用者改為考慮使用本檔稍後所述的其中一種替代方案。</span><span class="sxs-lookup"><span data-stu-id="e63c0-222">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="e63c0-223">`DataSet.ReadXml`和的 `DataTable.ReadXml` 執行原本是在序列化弱點被視為很容易瞭解的威脅類別目錄之前建立的。</span><span class="sxs-lookup"><span data-stu-id="e63c0-223">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="e63c0-224">因此，此程式碼不會遵循目前的安全性最佳作法。</span><span class="sxs-lookup"><span data-stu-id="e63c0-224">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="e63c0-225">這些 Api 可用來做為攻擊者的向量，以對 web 應用程式執行 DoS 攻擊。</span><span class="sxs-lookup"><span data-stu-id="e63c0-225">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="e63c0-226">這些攻擊可能會使 web 服務無回應，或導致非預期的進程終止。</span><span class="sxs-lookup"><span data-stu-id="e63c0-226">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="e63c0-227">此架構不會提供這些攻擊類別的緩和措施，而 .NET 會將此行為視為「依設計」。</span><span class="sxs-lookup"><span data-stu-id="e63c0-227">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="e63c0-228">.NET 已發行安全性更新，以降低某些問題，例如和中的資訊洩漏或遠端程式碼執行 `DataSet.ReadXml` `DataTable.ReadXml` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-228">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="e63c0-229">.NET 安全性更新可能不會針對這些威脅類別提供完整的保護。</span><span class="sxs-lookup"><span data-stu-id="e63c0-229">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="e63c0-230">取用者應該評估其個別案例，並考慮其對這些風險的潛在風險。</span><span class="sxs-lookup"><span data-stu-id="e63c0-230">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="e63c0-231">取用者應該注意到，這些 Api 的安全性更新可能會影響應用程式在某些情況下的相容性。</span><span class="sxs-lookup"><span data-stu-id="e63c0-231">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="e63c0-232">此外，也有可能會發現這些 Api 中的 novel 弱點，而 .NET 無法實際發佈安全性更新。</span><span class="sxs-lookup"><span data-stu-id="e63c0-232">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="e63c0-233">我們建議這些 Api 的取用者為：</span><span class="sxs-lookup"><span data-stu-id="e63c0-233">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="e63c0-234">請考慮使用本檔稍後所述的其中一種替代方案。</span><span class="sxs-lookup"><span data-stu-id="e63c0-234">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="e63c0-235">對其應用程式執行個別風險評量。</span><span class="sxs-lookup"><span data-stu-id="e63c0-235">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="e63c0-236">取用者會自行負責判斷是否要使用這些 Api。</span><span class="sxs-lookup"><span data-stu-id="e63c0-236">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="e63c0-237">取用者應評估任何安全性、技術和法律風險，包括可能使用這些 Api 的法規需求。</span><span class="sxs-lookup"><span data-stu-id="e63c0-237">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="e63c0-238">透過 ASP.NET web 服務或 WCF 的資料集和 DataTable</span><span class="sxs-lookup"><span data-stu-id="e63c0-238">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="e63c0-239">您可以 `DataSet` `DataTable` 在 ASP.NET （SOAP） web 服務中接受或實例，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-239">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

<span data-ttu-id="e63c0-240">這種方式的變化不是接受 `DataSet` 或 `DataTable` 直接作為參數，而是改為接受它做為整體 SOAP 序列化物件圖形的一部分，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-240">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e63c0-241">或者，使用 WCF，而不是 ASP.NET web 服務：</span><span class="sxs-lookup"><span data-stu-id="e63c0-241">Or, using WCF instead of ASP.NET web services:</span></span>

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e63c0-242">在所有這些情況下，威脅模型和安全性保證與[ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。</span><span class="sxs-lookup"><span data-stu-id="e63c0-242">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="e63c0-243">透過 XmlSerializer 還原序列化 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e63c0-243">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="e63c0-244">開發人員可以使用來還原序列化 `XmlSerializer` `DataSet` 和 `DataTable` 實例，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-244">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e63c0-245">在這些情況下，威脅模型和安全性保證與[ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。</span><span class="sxs-lookup"><span data-stu-id="e63c0-245">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="e63c0-246">透過 Jsonconvert.deserializeobject 還原序列化 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e63c0-246">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="e63c0-247">熱門的協力廠商 Newtonsoft 程式庫[JSON.NET](https://www.newtonsoft.com/json)可用於還原序列化 `DataSet` 和 `DataTable` 實例，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e63c0-247">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="e63c0-248">`DataSet` `DataTable` 以這種方式從不受信任的 JSON blob 還原序列化或是不安全的。</span><span class="sxs-lookup"><span data-stu-id="e63c0-248">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="e63c0-249">此模式很容易遭到阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="e63c0-249">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="e63c0-250">這類攻擊可能會使應用程式損毀或呈現無回應。</span><span class="sxs-lookup"><span data-stu-id="e63c0-250">Such an attack could crash the app or render it unresponsive.</span></span>

<span data-ttu-id="e63c0-251">**注意**： Microsoft 不保證或不支援執行協力廠商程式庫，例如_上的Newtonsoft.Js_。</span><span class="sxs-lookup"><span data-stu-id="e63c0-251">**Note**: Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="e63c0-252">這項資訊是為了完整性而提供，而且在撰寫本文時是正確的。</span><span class="sxs-lookup"><span data-stu-id="e63c0-252">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="e63c0-253">透過 BinaryFormatter 還原序列化 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="e63c0-253">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="e63c0-254">開發人員絕對不能使用 `BinaryFormatter` 、 `NetDataContractSerializer` 、 `SoapFormatter` 或相關的***unsafe***格式子，將 `DataSet` 或 `DataTable` 實例從不受信任的承載還原序列化：</span><span class="sxs-lookup"><span data-stu-id="e63c0-254">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="e63c0-255">這很容易受到完整的遠端程式碼執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="e63c0-255">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="e63c0-256">使用自訂 `SerializationBinder` 並不足以防止這類攻擊。</span><span class="sxs-lookup"><span data-stu-id="e63c0-256">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="e63c0-257">安全取代</span><span class="sxs-lookup"><span data-stu-id="e63c0-257">Safe replacements</span></span>

<span data-ttu-id="e63c0-258">針對下列任一應用程式：</span><span class="sxs-lookup"><span data-stu-id="e63c0-258">For apps that either:</span></span>

* <span data-ttu-id="e63c0-259">接受 `DataSet` 或 `DataTable` 透過 .asmx SOAP 端點或 WCF 端點。</span><span class="sxs-lookup"><span data-stu-id="e63c0-259">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="e63c0-260">將不受信任的資料還原序列化為或的實例 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="e63c0-260">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="e63c0-261">請考慮取代物件模型，以使用[Entity Framework](/ef)。</span><span class="sxs-lookup"><span data-stu-id="e63c0-261">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="e63c0-262">Entity Framework：</span><span class="sxs-lookup"><span data-stu-id="e63c0-262">Entity Framework:</span></span>

* <span data-ttu-id="e63c0-263">是一種豐富、現代化、物件導向的架構，可以代表關聯式資料。</span><span class="sxs-lookup"><span data-stu-id="e63c0-263">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="e63c0-264">引進[了各種不同](/ef/core/providers/)的資料庫提供者生態系統，讓您可以輕鬆地透過 Entity Framework 物件模型來投影資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="e63c0-264">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="e63c0-265">從不受信任的來源還原序列化資料時，提供內建的保護功能。</span><span class="sxs-lookup"><span data-stu-id="e63c0-265">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="e63c0-266">針對使用 SOAP 端點的應用程式 `.aspx` ，請考慮將這些端點變更為使用[WCF](/dotnet/framework/wcf/)。</span><span class="sxs-lookup"><span data-stu-id="e63c0-266">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](/dotnet/framework/wcf/).</span></span> <span data-ttu-id="e63c0-267">WCF 是一種功能更完整的 `.asmx` web 服務取代。</span><span class="sxs-lookup"><span data-stu-id="e63c0-267">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="e63c0-268">WCF 端點[可以透過 SOAP 公開](/dotnet/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients)，以與現有的呼叫端相容。</span><span class="sxs-lookup"><span data-stu-id="e63c0-268">WCF endpoints [can be exposed via SOAP](/dotnet/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients) for compatibility with existing callers.</span></span>
