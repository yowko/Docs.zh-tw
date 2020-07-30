---
title: 序列化 (C#)
description: 序列化會將物件轉換成位元組資料流程，以儲存物件或將它傳送至記憶體、資料庫或檔案。
ms.date: 01/02/2020
ms.openlocfilehash: b2b3105887ad6f000fcba895452a483881ae5a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302772"
---
# <a name="serialization-c"></a><span data-ttu-id="17b75-103">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="17b75-103">Serialization (C#)</span></span>

<span data-ttu-id="17b75-104">序列化程序會將物件轉換成位元組資料流，以將物件儲存或傳輸到記憶體、資料庫或檔案。</span><span class="sxs-lookup"><span data-stu-id="17b75-104">Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file.</span></span> <span data-ttu-id="17b75-105">其主要目的是儲存物件的狀態，這樣就能在需要時重新建立該物件。</span><span class="sxs-lookup"><span data-stu-id="17b75-105">Its main purpose is to save the state of an object in order to be able to recreate it when needed.</span></span> <span data-ttu-id="17b75-106">反向的程序則稱為還原序列化。</span><span class="sxs-lookup"><span data-stu-id="17b75-106">The reverse process is called deserialization.</span></span>

## <a name="how-serialization-works"></a><span data-ttu-id="17b75-107">序列化的運作方式</span><span class="sxs-lookup"><span data-stu-id="17b75-107">How serialization works</span></span>

<span data-ttu-id="17b75-108">下圖顯示序列化的整體程序：</span><span class="sxs-lookup"><span data-stu-id="17b75-108">This illustration shows the overall process of serialization:</span></span>

![序列化圖形](./media/index/serialization-process.gif)

<span data-ttu-id="17b75-110">物件會序列化為攜帶資料的資料流程。</span><span class="sxs-lookup"><span data-stu-id="17b75-110">The object is serialized to a stream that carries the data.</span></span> <span data-ttu-id="17b75-111">資料流程可能也會有物件類型的相關資訊，例如其版本、文化特性和元件名稱。</span><span class="sxs-lookup"><span data-stu-id="17b75-111">The stream may also have information about the object's type, such as its version, culture, and assembly name.</span></span> <span data-ttu-id="17b75-112">從該資料流程，物件可以儲存在資料庫、檔案或記憶體中。</span><span class="sxs-lookup"><span data-stu-id="17b75-112">From that stream, the object can be stored in a database, a file, or memory.</span></span>

### <a name="uses-for-serialization"></a><span data-ttu-id="17b75-113">序列化的用法</span><span class="sxs-lookup"><span data-stu-id="17b75-113">Uses for serialization</span></span>

<span data-ttu-id="17b75-114">序列化可讓開發人員儲存物件的狀態，並視需要重新建立，提供物件的儲存以及資料交換。</span><span class="sxs-lookup"><span data-stu-id="17b75-114">Serialization allows the developer to save the state of an object and re-create it as needed, providing storage of objects as well as data exchange.</span></span> <span data-ttu-id="17b75-115">藉由序列化，開發人員可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="17b75-115">Through serialization, a developer can perform actions such as:</span></span>

* <span data-ttu-id="17b75-116">使用 web 服務將物件傳送至遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="17b75-116">Sending the object to a remote application by using a web service</span></span>
* <span data-ttu-id="17b75-117">將一個或多個網域的物件傳遞給另一個</span><span class="sxs-lookup"><span data-stu-id="17b75-117">Passing an object from one domain to another</span></span>
* <span data-ttu-id="17b75-118">透過防火牆傳遞物件作為 JSON 或 XML 字串</span><span class="sxs-lookup"><span data-stu-id="17b75-118">Passing an object through a firewall as a JSON or XML string</span></span>
* <span data-ttu-id="17b75-119">維護應用程式間的安全性或使用者特定資訊</span><span class="sxs-lookup"><span data-stu-id="17b75-119">Maintaining security or user-specific information across applications</span></span>

## <a name="json-serialization"></a><span data-ttu-id="17b75-120">JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="17b75-120">JSON serialization</span></span>

<span data-ttu-id="17b75-121"><xref:System.Text.Json>命名空間包含 JavaScript 物件標記法（JSON）序列化和還原序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="17b75-121">The <xref:System.Text.Json> namespace contains classes for JavaScript Object Notation (JSON) serialization and deserialization.</span></span> <span data-ttu-id="17b75-122">JSON 是一種開放式標準，通常用來在網路上共用資料。</span><span class="sxs-lookup"><span data-stu-id="17b75-122">JSON is an open standard that is commonly used for sharing data across the web.</span></span>

<span data-ttu-id="17b75-123">JSON 序列化會將物件的公用屬性序列化為符合[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259)的字串、位元組陣列或資料流程。</span><span class="sxs-lookup"><span data-stu-id="17b75-123">JSON serialization serializes the public properties of an object into a string, byte array, or stream that conforms to [the RFC 8259 JSON specification](https://tools.ietf.org/html/rfc8259).</span></span> <span data-ttu-id="17b75-124">若要控制序列化 <xref:System.Text.Json.JsonSerializer> 或還原序列化類別實例的方式：</span><span class="sxs-lookup"><span data-stu-id="17b75-124">To control the way <xref:System.Text.Json.JsonSerializer> serializes or deserializes an instance of the class:</span></span>

* <span data-ttu-id="17b75-125">使用 <xref:System.Text.Json.JsonSerializerOptions> 物件</span><span class="sxs-lookup"><span data-stu-id="17b75-125">Use a <xref:System.Text.Json.JsonSerializerOptions> object</span></span>
* <span data-ttu-id="17b75-126">將命名空間中的屬性套用 <xref:System.Text.Json.Serialization> 至類別或屬性</span><span class="sxs-lookup"><span data-stu-id="17b75-126">Apply attributes from the <xref:System.Text.Json.Serialization> namespace to classes or properties</span></span>
* [<span data-ttu-id="17b75-127">執行自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="17b75-127">Implement custom converters</span></span>](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a><span data-ttu-id="17b75-128">二進位與 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="17b75-128">Binary and XML serialization</span></span>

<span data-ttu-id="17b75-129"><xref:System.Runtime.Serialization>命名空間包含二進位和 XML 序列化和還原序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="17b75-129">The <xref:System.Runtime.Serialization> namespace contains classes for binary and XML serialization and deserialization.</span></span>

<span data-ttu-id="17b75-130">二進位序列化使用二進位編碼來產生精簡的序列化，適用於儲存或通訊端型網路資料流。</span><span class="sxs-lookup"><span data-stu-id="17b75-130">Binary serialization uses binary encoding to produce compact serialization for uses such as storage or socket-based network streams.</span></span> <span data-ttu-id="17b75-131">在二進位序列化中，系統會序列化所有成員 (即使是唯讀的成員)，且效能會增強。</span><span class="sxs-lookup"><span data-stu-id="17b75-131">In binary serialization, all members, even members that are read-only, are serialized, and performance is enhanced.</span></span>

<span data-ttu-id="17b75-132">XML 序列化會將物件的公用欄位和屬性，或是方法的參數和傳回值，序列化為與特定 XML 結構描述定義語言 (XSD) 文件相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="17b75-132">XML serialization serializes the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="17b75-133">XML 序列化會產生強型別的類別，其中包含的公用屬性和欄位都會轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="17b75-133">XML serialization results in strongly typed classes with public properties and fields that are converted to XML.</span></span> <span data-ttu-id="17b75-134"><xref:System.Xml.Serialization>包含用來序列化和還原序列化 XML 的類別。</span><span class="sxs-lookup"><span data-stu-id="17b75-134"><xref:System.Xml.Serialization> contains classes for serializing and deserializing XML.</span></span> <span data-ttu-id="17b75-135">您可以將屬性套用至類別和類別成員，以便控制 <xref:System.Xml.Serialization.XmlSerializer> 序列化或還原序列化類別執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="17b75-135">You apply attributes to classes and class members to control the way the <xref:System.Xml.Serialization.XmlSerializer> serializes or deserializes an instance of the class.</span></span>

### <a name="making-an-object-serializable"></a><span data-ttu-id="17b75-136">讓物件可序列化</span><span class="sxs-lookup"><span data-stu-id="17b75-136">Making an object serializable</span></span>

<span data-ttu-id="17b75-137">針對二進位或 XML 序列化，您需要：</span><span class="sxs-lookup"><span data-stu-id="17b75-137">For binary or XML serialization, you need:</span></span>

* <span data-ttu-id="17b75-138">要序列化的物件</span><span class="sxs-lookup"><span data-stu-id="17b75-138">The object to be serialized</span></span>
* <span data-ttu-id="17b75-139">包含序列化物件的資料流程</span><span class="sxs-lookup"><span data-stu-id="17b75-139">A stream to contain the serialized object</span></span>
* <span data-ttu-id="17b75-140"><xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>實例</span><span class="sxs-lookup"><span data-stu-id="17b75-140">A <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> instance</span></span>

<span data-ttu-id="17b75-141">將 <xref:System.SerializableAttribute> 屬性套用至類型，以指出可以序列化類型的實例。</span><span class="sxs-lookup"><span data-stu-id="17b75-141">Apply the <xref:System.SerializableAttribute> attribute to a type to indicate that instances of the type can be serialized.</span></span> <span data-ttu-id="17b75-142">如果您嘗試序列化但該類型沒有 <xref:System.SerializableAttribute> 屬性，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="17b75-142">An  exception is thrown if you attempt to serialize but the type doesn't have the <xref:System.SerializableAttribute> attribute.</span></span>

<span data-ttu-id="17b75-143">若要防止將欄位序列化，請套用 <xref:System.NonSerializedAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="17b75-143">To prevent a field from being serialized, apply the <xref:System.NonSerializedAttribute> attribute.</span></span> <span data-ttu-id="17b75-144">如果可序列化型別的欄位包含指標、控制代碼，或一些其他特定環境專屬的資料結構，且無法以有意義的方式在不同環境中重新建構該欄位，則您可能想要讓它成為不可序列化的。</span><span class="sxs-lookup"><span data-stu-id="17b75-144">If a field of a serializable type contains a pointer, a handle, or some other data structure that is specific to a particular environment, and the field cannot be meaningfully reconstituted in a different environment, then you may want to make it nonserializable.</span></span>

<span data-ttu-id="17b75-145">如果序列化類別包含對其他類別之物件的參考，且該類別標記為 <xref:System.SerializableAttribute>，則系統也會將那些物件序列化。</span><span class="sxs-lookup"><span data-stu-id="17b75-145">If a serialized class contains references to objects of other classes that are marked <xref:System.SerializableAttribute>, those objects will also be serialized.</span></span>

### <a name="basic-and-custom-serialization"></a><span data-ttu-id="17b75-146">基本和自訂序列化</span><span class="sxs-lookup"><span data-stu-id="17b75-146">Basic and custom serialization</span></span>

<span data-ttu-id="17b75-147">二進位和 XML 序列化可以透過兩種方式來執行：基本和自訂。</span><span class="sxs-lookup"><span data-stu-id="17b75-147">Binary and XML serialization can be performed in two ways, basic and custom.</span></span>

<span data-ttu-id="17b75-148">基本序列化會使用 .NET 自動序列化物件。</span><span class="sxs-lookup"><span data-stu-id="17b75-148">Basic serialization uses .NET to automatically serialize the object.</span></span> <span data-ttu-id="17b75-149">唯一的要求是類別已套用 <xref:System.SerializableAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="17b75-149">The only requirement is that the class has the <xref:System.SerializableAttribute> attribute applied.</span></span> <span data-ttu-id="17b75-150">可以使用 <xref:System.NonSerializedAttribute> 來防止特定欄位被序列化。</span><span class="sxs-lookup"><span data-stu-id="17b75-150">The <xref:System.NonSerializedAttribute> can be used to keep specific fields from being serialized.</span></span>

<span data-ttu-id="17b75-151">當您使用基本序列化時，物件的版本控制可能產生問題。</span><span class="sxs-lookup"><span data-stu-id="17b75-151">When you use basic serialization, the versioning of objects may create problems.</span></span> <span data-ttu-id="17b75-152">版本控制的問題很重要時，建議使用自訂序列化。</span><span class="sxs-lookup"><span data-stu-id="17b75-152">You would use custom serialization when versioning issues are important.</span></span> <span data-ttu-id="17b75-153">基本序列化是執行序列化最簡單的方式，但它對該程序提供的控制機制並不多。</span><span class="sxs-lookup"><span data-stu-id="17b75-153">Basic serialization is the easiest way to perform serialization, but it does not provide much control over the process.</span></span>

<span data-ttu-id="17b75-154">在自訂序列化中，您可以明確指定要序列化的物件，以及序列化的方式。</span><span class="sxs-lookup"><span data-stu-id="17b75-154">In custom serialization, you can specify exactly which objects will be serialized and how it will be done.</span></span> <span data-ttu-id="17b75-155">類別必須標記為 <xref:System.SerializableAttribute> 並實作 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="17b75-155">The class must be marked <xref:System.SerializableAttribute> and implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="17b75-156">如果您也想要以自訂方式還原序列化物件，請使用自訂的函式。</span><span class="sxs-lookup"><span data-stu-id="17b75-156">If you want your object to be deserialized in a custom manner as well, use a custom constructor.</span></span>

## <a name="designer-serialization"></a><span data-ttu-id="17b75-157">設計工具序列化</span><span class="sxs-lookup"><span data-stu-id="17b75-157">Designer serialization</span></span>

<span data-ttu-id="17b75-158">設計工具序列化是特殊格式的序列化，其中包含一種與開發工具相關聯的物件持續性。</span><span class="sxs-lookup"><span data-stu-id="17b75-158">Designer serialization is a special form of serialization that involves the kind of object persistence associated with development tools.</span></span> <span data-ttu-id="17b75-159">設計工具序列化程序的作用是將物件圖形轉換成來源檔案，而該檔案稍後可用於復原物件圖形。</span><span class="sxs-lookup"><span data-stu-id="17b75-159">Designer serialization is the process of converting an object graph into a source file that can later be used to recover the object graph.</span></span> <span data-ttu-id="17b75-160">來源檔案可以包含程式碼、標記，或甚至 SQL 資料表資訊。</span><span class="sxs-lookup"><span data-stu-id="17b75-160">A source file can contain code, markup, or even SQL table information.</span></span>

## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a> <span data-ttu-id="17b75-161">相關主題和範例</span><span class="sxs-lookup"><span data-stu-id="17b75-161">Related Topics and Examples</span></span>  

<span data-ttu-id="17b75-162">[System.Text.Js總覽](../../../../standard/serialization/system-text-json-overview.md)說明如何取得連結 `System.Text.Json` 庫。</span><span class="sxs-lookup"><span data-stu-id="17b75-162">[System.Text.Json overview](../../../../standard/serialization/system-text-json-overview.md) Shows how to get the `System.Text.Json` library.</span></span>

<span data-ttu-id="17b75-163">[如何在 .net 中序列化和還原序列化 JSON](../../../../standard/serialization/system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="17b75-163">[How to serialize and deserialize JSON in .NET](../../../../standard/serialization/system-text-json-how-to.md).</span></span>
<span data-ttu-id="17b75-164">示範如何使用類別，在 JSON 中讀取和寫入物件資料 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="17b75-164">Shows how to read and write object data to and from JSON using the <xref:System.Text.Json.JsonSerializer> class.</span></span>

[<span data-ttu-id="17b75-165">逐步解說：在 Visual Studio 中保存物件 (#C)</span><span class="sxs-lookup"><span data-stu-id="17b75-165">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>](walkthrough-persisting-an-object-in-visual-studio.md)  
<span data-ttu-id="17b75-166">示範序列化能如何用來保存物件在執行個體之間的資料，可讓您儲存值，並且在下次物件具現化時擷取它們。</span><span class="sxs-lookup"><span data-stu-id="17b75-166">Demonstrates how serialization can be used to persist an object's data between instances, allowing you to store values and retrieve them the next time the object is instantiated.</span></span>

[<span data-ttu-id="17b75-167">如何從 XML 檔案讀取物件資料（c #）</span><span class="sxs-lookup"><span data-stu-id="17b75-167">How to read object data from an XML file (C#)</span></span>](how-to-read-object-data-from-an-xml-file.md)  
<span data-ttu-id="17b75-168">示範如何讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="17b75-168">Shows how to read object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>

[<span data-ttu-id="17b75-169">如何將物件資料寫入 XML 檔案（c #）</span><span class="sxs-lookup"><span data-stu-id="17b75-169">How to write object data to an XML file (C#)</span></span>](how-to-write-object-data-to-an-xml-file.md)  
<span data-ttu-id="17b75-170">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="17b75-170">Shows how to write the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>
