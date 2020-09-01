---
title: DataSet 和 DataTable 安全性指引
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 4fe8a062c762cc70d33243e3443aa9bf55635f98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137613"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="ed804-102">DataSet 和 DataTable 安全性指引</span><span class="sxs-lookup"><span data-stu-id="ed804-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="ed804-103">本文適用于：</span><span class="sxs-lookup"><span data-stu-id="ed804-103">This article applies to:</span></span>

* <span data-ttu-id="ed804-104">.NET Framework (所有版本) </span><span class="sxs-lookup"><span data-stu-id="ed804-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="ed804-105">.NET Core 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ed804-105">.NET Core and later</span></span>
* <span data-ttu-id="ed804-106">.NET 5.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ed804-106">.NET 5.0 and later</span></span>

<span data-ttu-id="ed804-107">[DataSet](/dotnet/api/system.data.dataset)和[DataTable](/dotnet/api/system.data.datatable)類型是舊版 .net 元件，可將資料集表示為 managed 物件。</span><span class="sxs-lookup"><span data-stu-id="ed804-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="ed804-108">這些元件是在 .NET 1.0 中引進，作為原始 [ADO.NET 基礎結構](/dotnet/framework/data/adonet/dataset-datatable-dataview/)的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed804-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span></span> <span data-ttu-id="ed804-109">其目標是要提供關聯式資料集的 managed 視圖，並將資料的基礎來源抽象化為 XML、SQL 或其他技術。</span><span class="sxs-lookup"><span data-stu-id="ed804-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="ed804-110">如需 ADO.NET 的詳細資訊，包括更多新式資料檢視範例，請參閱 [ADO.NET 檔](/dotnet/framework/data/adonet/)。</span><span class="sxs-lookup"><span data-stu-id="ed804-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](/dotnet/framework/data/adonet/).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="ed804-111">從 XML 還原序列化資料集或 DataTable 時的預設限制</span><span class="sxs-lookup"><span data-stu-id="ed804-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="ed804-112">在所有支援的 .NET Framework、.NET Core 和 .NET 版本上，並對已還原序列化 `DataSet` `DataTable` 的資料中可能存在的物件類型進行下列限制。</span><span class="sxs-lookup"><span data-stu-id="ed804-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="ed804-113">根據預設，此清單受限於：</span><span class="sxs-lookup"><span data-stu-id="ed804-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="ed804-114">基本和基本類型： `bool` 、 `char` 、 `sbyte` 、 `byte` 、 `short` 、 `ushort` 、 `int` 、、 `uint` `long` 、 `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、和。</span><span class="sxs-lookup"><span data-stu-id="ed804-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="ed804-115">常用的非基本： `Type` 、 `Uri` 和 `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="ed804-116">常用的 _系統。繪圖_ 類型： `Color` 、 `Point` 、 `PointF` 、 `Rectangle` 、 `RectangleF` 、 `Size` 和 `SizeF` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="ed804-117">`Enum` 類型。</span><span class="sxs-lookup"><span data-stu-id="ed804-117">`Enum` types.</span></span>
* <span data-ttu-id="ed804-118">上述類型的陣列和清單。</span><span class="sxs-lookup"><span data-stu-id="ed804-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="ed804-119">如果傳入的 XML 資料包含的物件類型不在此清單中：</span><span class="sxs-lookup"><span data-stu-id="ed804-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="ed804-120">擲回例外狀況，並顯示下列訊息和堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="ed804-120">An exception is thrown with the following message and stack trace.</span></span>  
<span data-ttu-id="ed804-121">錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="ed804-121">Error Message:</span></span>  
<span data-ttu-id="ed804-122">這裡不允許 InvalidOperationException： Type ' \<Type Name\> 、Version = \<n.n.n.n\> 、Culture = \<culture\> 、PublicKeyToken = \<token value\> '。</span><span class="sxs-lookup"><span data-stu-id="ed804-122">System.InvalidOperationException : Type '\<Type Name\>, Version=\<n.n.n.n\>, Culture=\<culture\>, PublicKeyToken=\<token value\>' is not allowed here.</span></span> <span data-ttu-id="ed804-123">如需詳細資訊，請參閱 [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) 。</span><span class="sxs-lookup"><span data-stu-id="ed804-123">See [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) for more details.</span></span>  
<span data-ttu-id="ed804-124">堆疊追蹤：</span><span class="sxs-lookup"><span data-stu-id="ed804-124">Stack Trace:</span></span>  
<span data-ttu-id="ed804-125">在 TypeLimiter. EnsureTypeIsAllowed (類型 type、TypeLimiter capturedLimiter) </span><span class="sxs-lookup"><span data-stu-id="ed804-125">at System.Data.TypeLimiter.EnsureTypeIsAllowed(Type type, TypeLimiter capturedLimiter)</span></span>  
<span data-ttu-id="ed804-126">UpdateColumnType (Type type，StorageType typeCode) </span><span class="sxs-lookup"><span data-stu-id="ed804-126">at System.Data.DataColumn.UpdateColumnType(Type type, StorageType typeCode)</span></span>  
<span data-ttu-id="ed804-127">在 System.Data.DataColumn.set_DataType (類型值) </span><span class="sxs-lookup"><span data-stu-id="ed804-127">at System.Data.DataColumn.set_DataType(Type value)</span></span>  

* <span data-ttu-id="ed804-128">還原序列化作業失敗。</span><span class="sxs-lookup"><span data-stu-id="ed804-128">The deserialization operation fails.</span></span>

<span data-ttu-id="ed804-129">將 XML 載入至現有的 `DataSet` 或 `DataTable` 實例時，也會將現有的資料行定義列入考慮。</span><span class="sxs-lookup"><span data-stu-id="ed804-129">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="ed804-130">如果資料表已經包含自訂類型的資料行定義，則該類型會暫時加入至 XML 還原序列化作業期間的允許清單中。</span><span class="sxs-lookup"><span data-stu-id="ed804-130">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

> [!NOTE]
> <span data-ttu-id="ed804-131">當您將資料行加入至之後 `DataTable` ， `ReadXml` 將不會從 XML 讀取架構，如果架構不符合，就不會讀取記錄，因此您必須自行加入所有資料行，才能使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="ed804-131">Once you add columns to a `DataTable`, `ReadXml` will not read the schema from the XML, and if the schema does not match it will also not read in the records, so you will need to add all the columns yourself to use this method.</span></span>

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

<span data-ttu-id="ed804-132">使用還原序列化或的實例時，也適用物件類型限制 `XmlSerializer` `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-132">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="ed804-133">不過，當使用還原序列化或的實例時，它們可能不適用 `BinaryFormatter` `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-133">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="ed804-134">使用時，不會套用物件類型限制 `DataAdapter.Fill` ，例如， `DataTable` 直接從資料庫填入實例時，不會使用 XML 還原序列化 api。</span><span class="sxs-lookup"><span data-stu-id="ed804-134">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="ed804-135">擴充允許類型的清單</span><span class="sxs-lookup"><span data-stu-id="ed804-135">Extend the list of allowed types</span></span>

<span data-ttu-id="ed804-136">除了上述內建類型之外，應用程式還可以擴充允許的類型清單，以包含自訂類型。</span><span class="sxs-lookup"><span data-stu-id="ed804-136">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="ed804-137">如果擴充允許的類型清單，則變更會_all_影響 `DataSet` `DataTable` 應用程式內的所有和實例。</span><span class="sxs-lookup"><span data-stu-id="ed804-137">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="ed804-138">類型無法從內建的允許類型清單中移除。</span><span class="sxs-lookup"><span data-stu-id="ed804-138">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="ed804-139">擴充到 configuration ( .NET Framework 4.0-4.8) </span><span class="sxs-lookup"><span data-stu-id="ed804-139">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="ed804-140">_App.config_ 可以用來擴充允許的類型清單。</span><span class="sxs-lookup"><span data-stu-id="ed804-140">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="ed804-141">若要擴充允許的類型清單：</span><span class="sxs-lookup"><span data-stu-id="ed804-141">To extend the allowed types list:</span></span>

* <span data-ttu-id="ed804-142">您可以使用專案 `<configSections>` ，將參考加入至 [ _system.object_ 設定] 區段。</span><span class="sxs-lookup"><span data-stu-id="ed804-142">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="ed804-143">用 `<system.data.dataset.serialization>` / `<allowedTypes>` 來指定其他類型。</span><span class="sxs-lookup"><span data-stu-id="ed804-143">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="ed804-144">每個專案都 `<add>` 只能使用其元件限定類型名稱來指定一種類型。</span><span class="sxs-lookup"><span data-stu-id="ed804-144">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="ed804-145">若要將其他類型加入至允許的類型清單，請使用多個 `<add>` 元素。</span><span class="sxs-lookup"><span data-stu-id="ed804-145">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="ed804-146">下列範例顯示如何藉由新增自訂類型來擴充允許的類型清單 `Fabrikam.CustomType` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-146">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

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

<span data-ttu-id="ed804-147">若要取出型別的元件限定名稱，請使用 [AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ed804-147">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="ed804-148">擴充到 configuration ( .NET Framework 2.0-3.5) </span><span class="sxs-lookup"><span data-stu-id="ed804-148">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="ed804-149">如果您的應用程式是以 .NET Framework 2.0 或3.5 為目標，您仍然可以使用上述 _App.config_ 機制來擴充允許的類型清單。</span><span class="sxs-lookup"><span data-stu-id="ed804-149">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="ed804-150">不過，您 `<configSections>` 的專案看起來會稍微不同，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-150">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

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

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="ed804-151">以程式設計方式擴充 ( .NET Framework、.NET Core、.NET 5.0 +) </span><span class="sxs-lookup"><span data-stu-id="ed804-151">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="ed804-152">您也可以使用 [AppDomain](/dotnet/api/system.appdomain.setdata) 搭配已知的金鑰 _DataSetDefaultAllowedTypes_，以程式設計方式擴充允許的類型清單，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ed804-152">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="ed804-153">如果使用延伸模組機制，則與金鑰 _DataSetDefaultAllowedTypes_ 相關聯的值必須為類型 `Type[]` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-153">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="ed804-154">在 .NET Framework 上，可使用 _App.config_ 和來擴充允許類型的清單 `AppDomain.SetData` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-154">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="ed804-155">在此情況下 `DataSet` ， `DataTable` 如果物件的類型存在於其中一個清單中，則會允許物件還原序列化為數據的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed804-155">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="ed804-156">在 audit 模式中執行應用程式 ( .NET Framework) </span><span class="sxs-lookup"><span data-stu-id="ed804-156">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="ed804-157">在 .NET Framework 中， `DataSet` 並 `DataTable` 提供「稽核模式」功能。</span><span class="sxs-lookup"><span data-stu-id="ed804-157">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="ed804-158">當啟用稽核模式時，會將 `DataSet` `DataTable` 傳入物件的類型與允許的類型清單進行比較。</span><span class="sxs-lookup"><span data-stu-id="ed804-158">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="ed804-159">但是，如果看不到類型為的物件，就 **不** 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ed804-159">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="ed804-160">相反 `DataSet` 地， `DataTable` 會通知任何附加的 `TraceListener` 實例有可疑的類型存在，讓 `TraceListener` 記錄這項資訊。</span><span class="sxs-lookup"><span data-stu-id="ed804-160">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="ed804-161">不會擲回例外狀況，而且還原序列化作業會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="ed804-161">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="ed804-162">在「audit 模式」中執行應用程式應該只是用於測試的暫時量值。</span><span class="sxs-lookup"><span data-stu-id="ed804-162">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="ed804-163">啟用稽核模式時， `DataSet` `DataTable` 不會強制執行類型限制，這可能會在您的應用程式中引進安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="ed804-163">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="ed804-164">如需詳細資訊，請參閱標題為移除[不受信任輸入](#swr)之[所有類型限制](#ratr)和安全性的章節。</span><span class="sxs-lookup"><span data-stu-id="ed804-164">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="ed804-165">您可以透過 _App.config_啟用 Audit 模式：</span><span class="sxs-lookup"><span data-stu-id="ed804-165">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="ed804-166">請參閱本檔中的「 [透過設定延伸](#etc) 」一節，以取得要為元素放置之適當值的相關資訊 `<configSections>` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-166">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="ed804-167">使用 `<allowedTypes auditOnly="true">` 啟用 audit 模式，如下列標記所示。</span><span class="sxs-lookup"><span data-stu-id="ed804-167">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

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

<span data-ttu-id="ed804-168">啟用稽核模式之後，您就可以使用_App.config_ ，將您偏好的內 `TraceListener` `DataSet` `TraceSource.` 建追蹤來源的名稱_System.Data.DataSet_連接到 system.string。</span><span class="sxs-lookup"><span data-stu-id="ed804-168">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="ed804-169">下列範例示範如何將追蹤事件寫入主控台 _和_ 磁片上的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="ed804-169">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

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

<span data-ttu-id="ed804-170">如需和的詳細資訊 `TraceSource` `TraceListener` ，請參閱檔 [如何：搭配追蹤接聽程式使用 TraceSource 和篩選](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)。</span><span class="sxs-lookup"><span data-stu-id="ed804-170">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ed804-171">在 .NET Core 或 .NET 5.0 和更新版本中，無法使用以 audit 模式執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed804-171">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="ed804-172">移除所有類型限制</span><span class="sxs-lookup"><span data-stu-id="ed804-172">Remove all type restrictions</span></span>

<span data-ttu-id="ed804-173">如果應用程式必須從和移除所有類型限制 `DataSet` 限制 `DataTable` ：</span><span class="sxs-lookup"><span data-stu-id="ed804-173">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="ed804-174">有幾個選項可隱藏類型限制限制。</span><span class="sxs-lookup"><span data-stu-id="ed804-174">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="ed804-175">可用的選項取決於應用程式的目標架構。</span><span class="sxs-lookup"><span data-stu-id="ed804-175">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="ed804-176">移除所有類型限制可能會在應用程式中引進安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="ed804-176">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="ed804-177">使用這種機制時，請確定應用 **程式不會使用** `DataSet` 或 `DataTable` 讀取不受信任的輸入。</span><span class="sxs-lookup"><span data-stu-id="ed804-177">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="ed804-178">如需詳細資訊，請參閱有關未[受信任的輸入之安全性的](#swr) [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147)和下一節。</span><span class="sxs-lookup"><span data-stu-id="ed804-178">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="ed804-179">透過 AppCoNtext configuration ( .NET Framework 4.6-4.8、.NET Core 2.1 和更新版本、.NET 5.0 和更新版本) </span><span class="sxs-lookup"><span data-stu-id="ed804-179">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="ed804-180">`AppContext` `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` 當設為時，參數會 `true` 從和移除所有類型限制 `DataSet` 限制 `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-180">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="ed804-181">在 .NET Framework 中，可以透過 _App.config_啟用此參數，如下列設定所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-181">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="ed804-182">在 ASP.NET 中， `<AppContextSwitchOverrides>` 無法使用元素。</span><span class="sxs-lookup"><span data-stu-id="ed804-182">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="ed804-183">相反地，您可以透過 _Web.config_啟用交換器，如下列設定所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-183">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="ed804-184">如需詳細資訊，請參閱 [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="ed804-184">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="ed804-185">在 .NET Core、.NET 5 和 ASP.NET Core 中，此設定是由 _runtimeconfig.js_來控制，如下列 JSON 所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-185">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="ed804-186">如需詳細資訊，請參閱「 [.Net Core 執行時間設定](/dotnet/core/run-time-config/)」。</span><span class="sxs-lookup"><span data-stu-id="ed804-186">For more information, see [".NET Core run-time configuration settings"](/dotnet/core/run-time-config/).</span></span>

<span data-ttu-id="ed804-187">`AllowArbitraryDataSetTypeInstantiation` 也可以透過 [AppCoNtext SetSwitch](/dotnet/api/system.appcontext.setswitch) 以程式設計方式設定，而不是使用設定檔，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-187">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="ed804-188">如果您選擇上述的程式設計方法，對的呼叫 `AppContext.SetSwitch` 應該會在應用程式啟動初期發生。</span><span class="sxs-lookup"><span data-stu-id="ed804-188">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="ed804-189">透過整個電腦的登錄 ( .NET Framework 2.0-4.8) </span><span class="sxs-lookup"><span data-stu-id="ed804-189">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="ed804-190">如果 `AppContext` 無法使用，則可以使用 Windows 登錄來停用類型限制檢查：</span><span class="sxs-lookup"><span data-stu-id="ed804-190">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="ed804-191">系統管理員必須設定登錄。</span><span class="sxs-lookup"><span data-stu-id="ed804-191">An administrator must configure the registry.</span></span>
* <span data-ttu-id="ed804-192">使用登錄是全電腦的變更，將會影響在電腦上執行的 _所有_ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed804-192">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="ed804-193">類型</span><span class="sxs-lookup"><span data-stu-id="ed804-193">Type</span></span>  |  <span data-ttu-id="ed804-194">值</span><span class="sxs-lookup"><span data-stu-id="ed804-194">Value</span></span> |
|---|---|
| <span data-ttu-id="ed804-195">**登錄機碼**</span><span class="sxs-lookup"><span data-stu-id="ed804-195">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="ed804-196">**值名稱**</span><span class="sxs-lookup"><span data-stu-id="ed804-196">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="ed804-197">**值類型**</span><span class="sxs-lookup"><span data-stu-id="ed804-197">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="ed804-198">**值資料**</span><span class="sxs-lookup"><span data-stu-id="ed804-198">**Value data**</span></span> | `true` |

<span data-ttu-id="ed804-199">在64位的作業系統上，必須為上述的64位金鑰新增此值， (如上所示) 和32位金鑰。</span><span class="sxs-lookup"><span data-stu-id="ed804-199">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="ed804-200">32位金鑰位於 `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-200">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="ed804-201">如需使用登錄設定的詳細資訊 `AppContext` ，請參閱「連結 [庫取用者的 AppCoNtext](/dotnet/api/system.appcontext#appcontext-for-library-consumers)」。</span><span class="sxs-lookup"><span data-stu-id="ed804-201">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="ed804-202">不受信任輸入的安全性</span><span class="sxs-lookup"><span data-stu-id="ed804-202">Safety with regard to untrusted input</span></span>

<span data-ttu-id="ed804-203">雖然 `DataSet` 和 `DataTable` 的確會針對在還原序列化 XML 承載時允許出現的型別強加預設限制， __ `DataSet` 而且 `DataTable` 在填入未受信任的輸入時__，也不安全。</span><span class="sxs-lookup"><span data-stu-id="ed804-203">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="ed804-204">以下是 `DataSet` 或 `DataTable` 實例可能讀取未受信任之輸入的非詳盡清單。</span><span class="sxs-lookup"><span data-stu-id="ed804-204">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="ed804-205">`DataAdapter`參考資料庫，並 `DataAdapter.Fill` 使用方法來填入 `DataSet` 資料庫查詢的內容。</span><span class="sxs-lookup"><span data-stu-id="ed804-205">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="ed804-206">`DataSet.ReadXml`或 `DataTable.ReadXml` 方法是用來讀取包含資料行和資料列資訊的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ed804-206">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="ed804-207">`DataSet`或 `DataTable` 實例會序列化為 ASP.NET (SOAP) web 服務或 WCF 端點的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed804-207">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="ed804-208">序列化程式（例如） `XmlSerializer` 是用來將 `DataSet` `DataTable` XML 資料流程中的或實例還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ed804-208">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="ed804-209">序列化程式（例如） `JsonConvert` 是用來 `DataSet` `DataTable` 從 JSON 資料流程還原序列化或實例。</span><span class="sxs-lookup"><span data-stu-id="ed804-209">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="ed804-210">`JsonConvert` 是受歡迎的協力廠商 [Newtonsoft.Js在](https://www.newtonsoft.com/json) 程式庫的方法。</span><span class="sxs-lookup"><span data-stu-id="ed804-210">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="ed804-211">序列化程式（例如） `BinaryFormatter` 是用來 `DataSet` `DataTable` 從原始位元組資料流程還原序列化或實例。</span><span class="sxs-lookup"><span data-stu-id="ed804-211">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="ed804-212">本檔討論上述案例的安全性考慮。</span><span class="sxs-lookup"><span data-stu-id="ed804-212">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="ed804-213">用 `DataAdapter.Fill` 來 `DataSet` 從不受信任的資料來源填入</span><span class="sxs-lookup"><span data-stu-id="ed804-213">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="ed804-214">您 `DataSet` 可以 `DataAdapter` 使用 [ `DataAdapter.Fill` 方法](/dotnet/api/system.data.common.dataadapter.fill)，從來填入實例，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ed804-214">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="ed804-215"> (上述的程式碼範例是 [從 DataAdapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)的較大範例的一部分。 ) </span><span class="sxs-lookup"><span data-stu-id="ed804-215">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="ed804-216">大部分的應用程式都可以簡化，並假設它們的資料庫層是受信任的。</span><span class="sxs-lookup"><span data-stu-id="ed804-216">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="ed804-217">但是，如果您習慣使用您的應用程式來 [建立威脅](https://www.microsoft.com/securityengineering/sdl/threatmodeling) 模型，則威脅模型可能會將應用程式 (用戶端) 和資料庫層之間的信任界限視為 (伺服器) 。</span><span class="sxs-lookup"><span data-stu-id="ed804-217">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="ed804-218">在用戶端與伺服器之間使用 [相互驗證](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) 或 [AAD 驗證](/azure/azure-sql/database/authentication-aad-overview) 是協助解決與此相關的風險的一種方式。</span><span class="sxs-lookup"><span data-stu-id="ed804-218">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="ed804-219">本節的其餘部分將討論用戶端連接到不受信任的伺服器的可能結果。</span><span class="sxs-lookup"><span data-stu-id="ed804-219">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="ed804-220">`DataAdapter`在不受信任的資料來源中指向的結果，取決於本身的實 `DataAdapter` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-220">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="ed804-221">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="ed804-221">SqlDataAdapter</span></span>

<span data-ttu-id="ed804-222">針對內建類型 [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)，參考不受信任的資料來源可能會導致拒絕服務 (DoS) 攻擊。</span><span class="sxs-lookup"><span data-stu-id="ed804-222">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="ed804-223">DoS 攻擊可能會導致應用程式變成沒有回應或損毀。</span><span class="sxs-lookup"><span data-stu-id="ed804-223">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="ed804-224">如果攻擊者可以與應用程式一起植入 DLL，它們也可以達成本機程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="ed804-224">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="ed804-225">其他 DataAdapter 類型</span><span class="sxs-lookup"><span data-stu-id="ed804-225">Other DataAdapter types</span></span>

<span data-ttu-id="ed804-226">協力廠商的 `DataAdapter` 執行必須自行評定其在不受信任的輸入時所提供的安全性保證。</span><span class="sxs-lookup"><span data-stu-id="ed804-226">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="ed804-227">.NET 無法針對這些執行提供任何安全保證。</span><span class="sxs-lookup"><span data-stu-id="ed804-227">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="ed804-228">DataSet. ReadXml 和 DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="ed804-228">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="ed804-229">搭配 `DataSet.ReadXml` `DataTable.ReadXml` 未受信任的輸入使用時，和方法不安全。</span><span class="sxs-lookup"><span data-stu-id="ed804-229">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="ed804-230">強烈建議取用者改為考慮使用本檔稍後所述的其中一個替代方案。</span><span class="sxs-lookup"><span data-stu-id="ed804-230">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="ed804-231">和的實 `DataSet.ReadXml` 作為 `DataTable.ReadXml` 最初在序列化弱點之前建立的，是很容易理解的威脅類別。</span><span class="sxs-lookup"><span data-stu-id="ed804-231">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="ed804-232">因此，程式碼不會遵循目前的安全性最佳作法。</span><span class="sxs-lookup"><span data-stu-id="ed804-232">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="ed804-233">這些 Api 可以作為攻擊者用來對 web 應用程式執行 DoS 攻擊的向量。</span><span class="sxs-lookup"><span data-stu-id="ed804-233">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="ed804-234">這些攻擊可能會導致 web 服務沒有回應，或導致非預期的進程終止。</span><span class="sxs-lookup"><span data-stu-id="ed804-234">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="ed804-235">此架構不提供這些攻擊類別的緩和措施，而 .NET 會將此行為視為「依設計」。</span><span class="sxs-lookup"><span data-stu-id="ed804-235">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="ed804-236">.NET 已發行安全性更新，可減輕某些問題，例如和中的資訊洩漏或遠端程式碼執行 `DataSet.ReadXml` `DataTable.ReadXml` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-236">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="ed804-237">.NET 安全性更新可能不會針對這些威脅類別提供完整的保護。</span><span class="sxs-lookup"><span data-stu-id="ed804-237">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="ed804-238">取用者應該評估其個別案例，並考慮其對這些風險的潛在風險。</span><span class="sxs-lookup"><span data-stu-id="ed804-238">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="ed804-239">取用者應該注意，在某些情況下，這些 Api 的安全性更新可能會影響應用程式相容性。</span><span class="sxs-lookup"><span data-stu-id="ed804-239">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="ed804-240">此外，也有可能會探索這些 Api 中的新穎弱點，而 .NET 無法實際發佈安全性更新。</span><span class="sxs-lookup"><span data-stu-id="ed804-240">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="ed804-241">我們建議這些 Api 的取用者可能：</span><span class="sxs-lookup"><span data-stu-id="ed804-241">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="ed804-242">請考慮使用本檔稍後所述的其中一個替代方案。</span><span class="sxs-lookup"><span data-stu-id="ed804-242">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="ed804-243">對其應用程式執行個別的風險評估。</span><span class="sxs-lookup"><span data-stu-id="ed804-243">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="ed804-244">消費者必須自行負責判斷是否要使用這些 Api。</span><span class="sxs-lookup"><span data-stu-id="ed804-244">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="ed804-245">取用者應該使用這些 Api 來評估任何安全性、技術和法律風險，包括法規需求。</span><span class="sxs-lookup"><span data-stu-id="ed804-245">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="ed804-246">透過 ASP.NET web 服務或 WCF 的資料集和 DataTable</span><span class="sxs-lookup"><span data-stu-id="ed804-246">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="ed804-247">您可以接受 `DataSet` `DataTable` ASP.NET (SOAP) web 服務中的或實例，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-247">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

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

<span data-ttu-id="ed804-248">的變化不是接受 `DataSet` 或 `DataTable` 直接作為參數，而是在整體 SOAP 序列化物件圖形中接受它，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-248">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

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

<span data-ttu-id="ed804-249">或者，使用 WCF 而不是 ASP.NET web 服務：</span><span class="sxs-lookup"><span data-stu-id="ed804-249">Or, using WCF instead of ASP.NET web services:</span></span>

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

<span data-ttu-id="ed804-250">在上述所有情況下，威脅模型和安全性保證與 [ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。</span><span class="sxs-lookup"><span data-stu-id="ed804-250">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="ed804-251">透過 XmlSerializer 還原序列化 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="ed804-251">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="ed804-252">開發人員可以使用還原序列化 `XmlSerializer` `DataSet` 和 `DataTable` 實例，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-252">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

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

<span data-ttu-id="ed804-253">在這些情況下，威脅模型和安全性保證與[ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。</span><span class="sxs-lookup"><span data-stu-id="ed804-253">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="ed804-254">透過 >jsonconvert.deserializeobject 還原序列化資料集或 DataTable</span><span class="sxs-lookup"><span data-stu-id="ed804-254">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="ed804-255">熱門的協力廠商 Newtonsoft 程式庫 [JSON.NET](https://www.newtonsoft.com/json) 可以用來還原序列化 `DataSet` 和 `DataTable` 實例，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="ed804-255">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

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

<span data-ttu-id="ed804-256">從不 `DataSet` 受信任的 JSON blob 還原序列化或以此 `DataTable` 方式並不安全。</span><span class="sxs-lookup"><span data-stu-id="ed804-256">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="ed804-257">這種模式很容易遭到阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="ed804-257">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="ed804-258">這類攻擊可能會導致應用程式損毀，或使其無法回應。</span><span class="sxs-lookup"><span data-stu-id="ed804-258">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="ed804-259">Microsoft 不保證或支援協力廠商程式庫（例如 _Newtonsoft.Js_）的執行。</span><span class="sxs-lookup"><span data-stu-id="ed804-259">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="ed804-260">這項資訊是為了完整性而提供，而且在撰寫本文時，是正確的。</span><span class="sxs-lookup"><span data-stu-id="ed804-260">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="ed804-261">透過 BinaryFormatter 還原序列化資料集或 DataTable</span><span class="sxs-lookup"><span data-stu-id="ed804-261">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="ed804-262">開發人員絕不能使用 `BinaryFormatter` 、 `NetDataContractSerializer` 、 `SoapFormatter` 或相關的 ***unsafe*** 格式子， `DataSet` `DataTable` 從不受信任的承載還原序列化或實例：</span><span class="sxs-lookup"><span data-stu-id="ed804-262">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="ed804-263">這很容易受到完整的遠端程式碼執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="ed804-263">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="ed804-264">使用自訂 `SerializationBinder` 並不足以防止這類攻擊。</span><span class="sxs-lookup"><span data-stu-id="ed804-264">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="ed804-265">安全取代</span><span class="sxs-lookup"><span data-stu-id="ed804-265">Safe replacements</span></span>

<span data-ttu-id="ed804-266">針對下列任一項的應用程式：</span><span class="sxs-lookup"><span data-stu-id="ed804-266">For apps that either:</span></span>

* <span data-ttu-id="ed804-267">接受 `DataSet` 或 `DataTable` 透過 .asmx SOAP 端點或 WCF 端點。</span><span class="sxs-lookup"><span data-stu-id="ed804-267">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="ed804-268">將不受信任的資料還原序列化為或的實例 `DataSet` `DataTable` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-268">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="ed804-269">請考慮將物件模型取代為使用 [Entity Framework](/ef)。</span><span class="sxs-lookup"><span data-stu-id="ed804-269">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="ed804-270">Entity Framework：</span><span class="sxs-lookup"><span data-stu-id="ed804-270">Entity Framework:</span></span>

* <span data-ttu-id="ed804-271">是一種功能豐富、現代化的物件導向架構，可代表關聯式資料。</span><span class="sxs-lookup"><span data-stu-id="ed804-271">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="ed804-272">引進不同的資料庫提供者 [生態系統](/ef/core/providers/) ，讓您輕鬆地透過 Entity Framework 物件模型來投影資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="ed804-272">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="ed804-273">從不受信任的來源還原序列化資料時，提供內建的保護。</span><span class="sxs-lookup"><span data-stu-id="ed804-273">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="ed804-274">針對使用 SOAP 端點的應用程式 `.aspx` ，請考慮將這些端點變更為使用 [WCF](/dotnet/framework/wcf/)。</span><span class="sxs-lookup"><span data-stu-id="ed804-274">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](/dotnet/framework/wcf/).</span></span> <span data-ttu-id="ed804-275">WCF 是 web 服務的功能更完整的取代 `.asmx` 。</span><span class="sxs-lookup"><span data-stu-id="ed804-275">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="ed804-276">您 [可以透過 SOAP 公開](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) WCF 端點，以與現有的呼叫端相容。</span><span class="sxs-lookup"><span data-stu-id="ed804-276">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="ed804-277">程式碼分析器</span><span class="sxs-lookup"><span data-stu-id="ed804-277">Code analyzers</span></span>

<span data-ttu-id="ed804-278">編譯原始程式碼時所執行的程式碼分析器安全性規則，可協助您在 c # 和 Visual Basic 程式碼中找到與此安全性問題相關的弱點。</span><span class="sxs-lookup"><span data-stu-id="ed804-278">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="ed804-279">CodeAnalysis 將 microsoft.codeanalysis.fxcopanalyzers 是在 [nuget.org](https://www.nuget.org/)上散發之程式碼分析器的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="ed804-279">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="ed804-280">如需程式碼分析器的總覽，請參閱 [原始程式碼分析器的總覽](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview)。</span><span class="sxs-lookup"><span data-stu-id="ed804-280">For an overview of code analyzers, see [Overview of source code analyzers](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="ed804-281">啟用下列 CodeAnalysis 規則：</span><span class="sxs-lookup"><span data-stu-id="ed804-281">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="ed804-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350)：不使用 DataTable. ReadXml ( # A1 與不受信任的資料</span><span class="sxs-lookup"><span data-stu-id="ed804-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="ed804-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351)：不使用資料集. ReadXml ( # A1 與不受信任的資料</span><span class="sxs-lookup"><span data-stu-id="ed804-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="ed804-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352)：可序列化類型的 Unsafe DataSet 或 DataTable 可能很容易受到遠端程式碼執行攻擊</span><span class="sxs-lookup"><span data-stu-id="ed804-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="ed804-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353)： serializable 類型中不安全的 DataSet 或 DataTable</span><span class="sxs-lookup"><span data-stu-id="ed804-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="ed804-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354)：還原序列化的物件圖形中不安全的資料集或 DataTable 可能很容易受到遠端程式碼執行攻擊</span><span class="sxs-lookup"><span data-stu-id="ed804-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="ed804-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355)：在還原序列化物件圖形中找到 Unsafe 資料集或 DataTable 類型</span><span class="sxs-lookup"><span data-stu-id="ed804-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="ed804-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356)： web 還原序列化物件圖形中不安全的資料集或 DataTable 類型</span><span class="sxs-lookup"><span data-stu-id="ed804-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="ed804-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361)：確定包含資料集的自動產生類別 ReadXml ( # A1 未與不受信任的資料搭配使用</span><span class="sxs-lookup"><span data-stu-id="ed804-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="ed804-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362)：自動產生的可序列化類型中不安全的資料集或 DataTable 可能很容易受到遠端程式碼執行攻擊</span><span class="sxs-lookup"><span data-stu-id="ed804-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="ed804-291">如需設定規則的詳細資訊，請參閱 [使用程式碼分析器](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers)。</span><span class="sxs-lookup"><span data-stu-id="ed804-291">For more information about configuring rules, see [Use code analyzers](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="ed804-292">下列 NuGet 套件中提供新的安全性規則：</span><span class="sxs-lookup"><span data-stu-id="ed804-292">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="ed804-293">CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 3.3.0：適用于 Visual Studio 2019 16.3 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="ed804-293">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="ed804-294">CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 2.9.11：適用于 Visual Studio 2017 15.9 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="ed804-294">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
