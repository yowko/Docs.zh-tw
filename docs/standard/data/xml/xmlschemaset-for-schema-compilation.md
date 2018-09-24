---
title: 用於結構描述編譯的 XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c24fe637514ba773cecc7824de276b1707a4e90c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517723"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="441ef-102">用於結構描述編譯的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="441ef-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="441ef-103">說明 <xref:System.Xml.Schema.XmlSchemaSet>，它是一種可儲存及驗證 XML 結構描述定義語言 (XSD) 結構描述的快取。</span><span class="sxs-lookup"><span data-stu-id="441ef-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="441ef-104">XmlSchemaSet 類別</span><span class="sxs-lookup"><span data-stu-id="441ef-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="441ef-105"><xref:System.Xml.Schema.XmlSchemaSet> 是一種可儲存及驗證 XML 結構描述定義語言 (XSD) 結構描述的快取。</span><span class="sxs-lookup"><span data-stu-id="441ef-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="441ef-106">在 <xref:System.Xml?displayProperty=nameWithType> 1.0 版中，已將 XML 結構描述載入 <xref:System.Xml.Schema.XmlSchemaCollection> 類別，做為結構描述程式庫。</span><span class="sxs-lookup"><span data-stu-id="441ef-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="441ef-107">在 <xref:System.Xml?displayProperty=nameWithType> 2.0 版中，<xref:System.Xml.XmlValidatingReader> 及 <xref:System.Xml.Schema.XmlSchemaCollection> 類別已過時，並已分別由 <xref:System.Xml.XmlReader.Create%2A> 方法及 <xref:System.Xml.Schema.XmlSchemaSet> 類別取代。</span><span class="sxs-lookup"><span data-stu-id="441ef-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="441ef-108">已經引入 <xref:System.Xml.Schema.XmlSchemaSet> 以修正大量問題，包括標準相容性、效能和過時的 Microsoft XML 資料精簡 (XDR) 結構描述格式。</span><span class="sxs-lookup"><span data-stu-id="441ef-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="441ef-109">下列是 <xref:System.Xml.Schema.XmlSchemaCollection> 類別與 <xref:System.Xml.Schema.XmlSchemaSet> 類別的比較。</span><span class="sxs-lookup"><span data-stu-id="441ef-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="441ef-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="441ef-110">XmlSchemaCollection</span></span>|<span data-ttu-id="441ef-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="441ef-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="441ef-112">支援 Microsoft XDR 和 W3C XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="441ef-113">只支援 W3C XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="441ef-114">當呼叫 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 方法時，會編譯結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="441ef-115">當呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法時，不會編譯結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="441ef-116">這會改進結構描述程式庫建立期間的效能。</span><span class="sxs-lookup"><span data-stu-id="441ef-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="441ef-117">每個結構描述都會產生可導致「結構描述島」的個別編譯版本。</span><span class="sxs-lookup"><span data-stu-id="441ef-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="441ef-118">因此，所有的 Include 和 Import 都只位於該結構描述範圍內。</span><span class="sxs-lookup"><span data-stu-id="441ef-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="441ef-119">編譯的結構描述會產生單一邏輯結構描述 (一「組」結構描述)。</span><span class="sxs-lookup"><span data-stu-id="441ef-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="441ef-120">結構描述內已加入至該組的所有匯入結構描述，都會直接加入至它們自身的組。</span><span class="sxs-lookup"><span data-stu-id="441ef-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="441ef-121">這表示全部型別都可供所有結構描述使用。</span><span class="sxs-lookup"><span data-stu-id="441ef-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="441ef-122">特定目標命名空間在集合中只可以有一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="441ef-123">只要不存在型別衝突，就可以為相同的目標命名空間加入多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="441ef-124">移轉至 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="441ef-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="441ef-125">下列程式碼範例提供從過時的 <xref:System.Xml.Schema.XmlSchemaSet> 類別到新 <xref:System.Xml.Schema.XmlSchemaCollection> 類別的移轉指南。</span><span class="sxs-lookup"><span data-stu-id="441ef-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="441ef-126">該程式碼範例會說明兩種類別之間的下列主要差異。</span><span class="sxs-lookup"><span data-stu-id="441ef-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
-   <span data-ttu-id="441ef-127">不同於 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 類別的 <xref:System.Xml.Schema.XmlSchemaCollection> 方法，當呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法時，不會編譯結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-128">在範例程式碼中，會明確呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法。</span><span class="sxs-lookup"><span data-stu-id="441ef-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
-   <span data-ttu-id="441ef-129">若要重複處理 <xref:System.Xml.Schema.XmlSchemaSet>，則必須使用 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性。</span><span class="sxs-lookup"><span data-stu-id="441ef-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="441ef-130">下列是過時的 <xref:System.Xml.Schema.XmlSchemaCollection> 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="441ef-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="441ef-131">下列是對等的 <xref:System.Xml.Schema.XmlSchemaSet> 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="441ef-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="441ef-132">加入及擷取結構描述</span><span class="sxs-lookup"><span data-stu-id="441ef-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="441ef-133">使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法，可將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet>。</span><span class="sxs-lookup"><span data-stu-id="441ef-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-134">將結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet> 後，便會與目標命名空間 URI 關聯。</span><span class="sxs-lookup"><span data-stu-id="441ef-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="441ef-135">目標命名空間 URI 可指定為 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法的參數，或如果未指定任何目標命名空間，則 <xref:System.Xml.Schema.XmlSchemaSet> 會使用結構描述中定義的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="441ef-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="441ef-136">使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性，可從 <xref:System.Xml.Schema.XmlSchemaSet> 擷取結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-137"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性可讓您重複處理 <xref:System.Xml.Schema.XmlSchema> 中包含的 <xref:System.Xml.Schema.XmlSchemaSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="441ef-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性會傳回 <xref:System.Xml.Schema.XmlSchema> 中包含的所有 <xref:System.Xml.Schema.XmlSchemaSet> 物件，或如果給定目標命名空間參數，則會傳回屬於目標命名空間的所有 <xref:System.Xml.Schema.XmlSchema> 物件。</span><span class="sxs-lookup"><span data-stu-id="441ef-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="441ef-139">如果將 `null` 指定為目標命名空間參數，則 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性會傳回所有結構描述但無命名空間。</span><span class="sxs-lookup"><span data-stu-id="441ef-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="441ef-140">下列範例會將 `books.xsd` 命名空間中的 `http://www.contoso.com/books` 結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet>，從 `http://www.contoso.com/books` 擷取所有屬於 <xref:System.Xml.Schema.XmlSchemaSet> 命名空間的結構描述，然後將那些結構描述寫入 <xref:System.Console>。</span><span class="sxs-lookup"><span data-stu-id="441ef-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="441ef-141">如需在 <xref:System.Xml.Schema.XmlSchemaSet> 物件中加入及擷取結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法及 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 屬性參考文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="441ef-142">編譯結構描述</span><span class="sxs-lookup"><span data-stu-id="441ef-142">Compiling Schemas</span></span>  
 <span data-ttu-id="441ef-143">透過 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法，可將 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述編譯成一個邏輯結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="441ef-144">不同於過時的 <xref:System.Xml.Schema.XmlSchemaCollection> 類別，當呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法時，不會編譯結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="441ef-145">如果 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法執行成功，則 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性會設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="441ef-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="441ef-146">如果結構描述是在 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 時編輯的，則 <xref:System.Xml.Schema.XmlSchemaSet> 屬性不受影響。</span><span class="sxs-lookup"><span data-stu-id="441ef-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-147">也不會追蹤 <xref:System.Xml.Schema.XmlSchemaSet> 中個別結構描述的更新。</span><span class="sxs-lookup"><span data-stu-id="441ef-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="441ef-148">因此，即使 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 中的其中一個結構描述已變更，只要未在 `true` 中加入或移除結構描述，<xref:System.Xml.Schema.XmlSchemaSet> 屬性就可為 <xref:System.Xml.Schema.XmlSchemaSet>。</span><span class="sxs-lookup"><span data-stu-id="441ef-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="441ef-149">下列範例會將 `books.xsd` 檔案加入至 <xref:System.Xml.Schema.XmlSchemaSet>，然後呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="441ef-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="441ef-150">如需編譯 <xref:System.Xml.Schema.XmlSchemaSet> 中結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法參考文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="441ef-151">重新處理結構描述</span><span class="sxs-lookup"><span data-stu-id="441ef-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="441ef-152">當呼叫 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法時，重新處理 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述會執行對結構描述執行的所有前置處理步驟。</span><span class="sxs-lookup"><span data-stu-id="441ef-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="441ef-153">如果 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法呼叫成功，則 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 屬性會設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="441ef-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="441ef-154">在 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 執行編譯之後，如果已修改 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述，則應使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法。</span><span class="sxs-lookup"><span data-stu-id="441ef-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="441ef-155">下列範例說明如何使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法重新處理加入至 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="441ef-156">在使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法編譯 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>，並已修改加入至 <xref:System.Xml.Schema.XmlSchemaSet> 的結構描述之後，<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 屬性會設為 `true` (即使已修改 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述)。</span><span class="sxs-lookup"><span data-stu-id="441ef-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="441ef-157">呼叫 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法會執行 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法所執行的所有前置處理，並將 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="441ef-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="441ef-158">如需重新處理 <xref:System.Xml.Schema.XmlSchemaSet> 中結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法參考文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="441ef-159">檢查結構描述</span><span class="sxs-lookup"><span data-stu-id="441ef-159">Checking for a Schema</span></span>  
 <span data-ttu-id="441ef-160">您可以使用 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法，檢查結構描述是否包含在 <xref:System.Xml.Schema.XmlSchemaSet> 中。</span><span class="sxs-lookup"><span data-stu-id="441ef-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 方法允許檢查目標命名空間或 <xref:System.Xml.Schema.XmlSchema> 物件。</span><span class="sxs-lookup"><span data-stu-id="441ef-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="441ef-162">如果結構描述包含在 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 中，則在這兩種情況下，`true` 方法都會傳回 <xref:System.Xml.Schema.XmlSchemaSet>；否則，傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="441ef-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="441ef-163">如需檢查結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 方法參考文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="441ef-164">移除結構描述</span><span class="sxs-lookup"><span data-stu-id="441ef-164">Removing Schemas</span></span>  
 <span data-ttu-id="441ef-165">使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法，可將結構描述從 <xref:System.Xml.Schema.XmlSchemaSet> 中移除。</span><span class="sxs-lookup"><span data-stu-id="441ef-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 方法會從 <xref:System.Xml.Schema.XmlSchemaSet> 移除指定的結構描述，而 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法會移除指定的結構描述及其從 <xref:System.Xml.Schema.XmlSchemaSet> 匯入的所有結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="441ef-167">下列範例說明如何將多個結構描述加入至 <xref:System.Xml.Schema.XmlSchemaSet>，然後使用 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法移除其中一個結構描述及其匯入的所有結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="441ef-168">如需從 <xref:System.Xml.Schema.XmlSchemaSet> 移除結構描述的詳細資訊，請參閱 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 及 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法參考文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="441ef-169">結構描述解析及 xs:import</span><span class="sxs-lookup"><span data-stu-id="441ef-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="441ef-170">下列範例說明當 <xref:System.Xml.Schema.XmlSchemaSet> 中存在某個指定命名空間的多個結構描述時，匯入結構描述的 <xref:System.Xml.Schema.XmlSchemaSet> 行為。</span><span class="sxs-lookup"><span data-stu-id="441ef-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="441ef-171">例如，設想一個 <xref:System.Xml.Schema.XmlSchemaSet>，假設其中有 `http://www.contoso.com` 命名空間的多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="441ef-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="441ef-172">具有下列 `xs:import` 指示詞的結構描述會加入至 <xref:System.Xml.Schema.XmlSchemaSet>。</span><span class="sxs-lookup"><span data-stu-id="441ef-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="441ef-173"><xref:System.Xml.Schema.XmlSchemaSet> 會嘗試匯入 `http://www.contoso.com` 命名空間的結構描述，方法是從 `http://www.contoso.com/schema.xsd` URL 將其載入。</span><span class="sxs-lookup"><span data-stu-id="441ef-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="441ef-174">即使在 `http://www.contoso.com` 中存在 <xref:System.Xml.Schema.XmlSchemaSet> 命名空間的其他結構描述文件，也只有在結構描述文件中宣告的結構描述宣告及型別才可在匯入結構描述中使用。</span><span class="sxs-lookup"><span data-stu-id="441ef-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-175">如果在 `schema.xsd` URL 處找不到 `http://www.contoso.com/schema.xsd` 檔案，則不會將 `http://www.contoso.com` 命名空間的任何結構描述匯入到匯入結構描述中。</span><span class="sxs-lookup"><span data-stu-id="441ef-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="441ef-176">驗證 XML 文件</span><span class="sxs-lookup"><span data-stu-id="441ef-176">Validating XML Documents</span></span>  
 <span data-ttu-id="441ef-177">您可根據 <xref:System.Xml.Schema.XmlSchemaSet> 中的結構描述來驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="441ef-178">驗證 XML 文件的方法是將結構描述加入至 <xref:System.Xml.XmlReaderSettings> 物件的 <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性，或將 <xref:System.Xml.Schema.XmlSchemaSet> 加入至 <xref:System.Xml.XmlReaderSettings> 物件的 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="441ef-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="441ef-179">然後，<xref:System.Xml.XmlReaderSettings> 類別的 <xref:System.Xml.XmlReader.Create%2A> 方法會使用 <xref:System.Xml.XmlReader> 物件來建立 <xref:System.Xml.XmlReader> 物件並驗證 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="441ef-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="441ef-180">如需有關使用 <xref:System.Xml.Schema.XmlSchemaSet> 驗證 XML 文件的詳細資訊，請參閱 [使用 XmlSchemaSet 驗證 XML 結構描述 (XSD)](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)。</span><span class="sxs-lookup"><span data-stu-id="441ef-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441ef-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="441ef-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
- [<span data-ttu-id="441ef-182">XmlSchemaSet 作為結構描述快取</span><span class="sxs-lookup"><span data-stu-id="441ef-182">XmlSchemaSet as a Schema Cache</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [<span data-ttu-id="441ef-183">使用 XmlSchemaSet 驗證 XML 結構描述 (XSD)</span><span class="sxs-lookup"><span data-stu-id="441ef-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
