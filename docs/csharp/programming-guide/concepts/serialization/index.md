---
title: 序列化 (C#)
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167591"
---
# <a name="serialization-c"></a><span data-ttu-id="6b065-102">序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="6b065-102">Serialization (C#)</span></span>

<span data-ttu-id="6b065-103">序列化程序會將物件轉換成位元組資料流，以將物件儲存或傳輸到記憶體、資料庫或檔案。</span><span class="sxs-lookup"><span data-stu-id="6b065-103">Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file.</span></span> <span data-ttu-id="6b065-104">其主要目的是儲存物件的狀態，這樣就能在需要時重新建立該物件。</span><span class="sxs-lookup"><span data-stu-id="6b065-104">Its main purpose is to save the state of an object in order to be able to recreate it when needed.</span></span> <span data-ttu-id="6b065-105">反向的程序則稱為還原序列化。</span><span class="sxs-lookup"><span data-stu-id="6b065-105">The reverse process is called deserialization.</span></span>

## <a name="how-serialization-works"></a><span data-ttu-id="6b065-106">序列化的運作方式</span><span class="sxs-lookup"><span data-stu-id="6b065-106">How serialization works</span></span>

<span data-ttu-id="6b065-107">下圖顯示序列化的整體程序：</span><span class="sxs-lookup"><span data-stu-id="6b065-107">This illustration shows the overall process of serialization:</span></span>

![序列化圖形](./media/index/serialization-process.gif)

<span data-ttu-id="6b065-109">物件序列化為傳輸資料的流。</span><span class="sxs-lookup"><span data-stu-id="6b065-109">The object is serialized to a stream that carries the data.</span></span> <span data-ttu-id="6b065-110">流可能還包含有關物件類型的資訊，例如其版本、區域性和程式集名稱。</span><span class="sxs-lookup"><span data-stu-id="6b065-110">The stream may also have information about the object's type, such as its version, culture, and assembly name.</span></span> <span data-ttu-id="6b065-111">從該流中，物件可以存儲在資料庫、檔或記憶體中。</span><span class="sxs-lookup"><span data-stu-id="6b065-111">From that stream, the object can be stored in a database, a file, or memory.</span></span>

### <a name="uses-for-serialization"></a><span data-ttu-id="6b065-112">序列化的用法</span><span class="sxs-lookup"><span data-stu-id="6b065-112">Uses for serialization</span></span>

<span data-ttu-id="6b065-113">序列化允許開發人員保存物件的狀態並根據需要重新創建它，從而提供物件的存儲和資料交換。</span><span class="sxs-lookup"><span data-stu-id="6b065-113">Serialization allows the developer to save the state of an object and re-create it as needed, providing storage of objects as well as data exchange.</span></span> <span data-ttu-id="6b065-114">通過序列化，開發人員可以執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6b065-114">Through serialization, a developer can perform actions such as:</span></span>

* <span data-ttu-id="6b065-115">使用 Web 服務將物件發送到遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="6b065-115">Sending the object to a remote application by using a web service</span></span>
* <span data-ttu-id="6b065-116">將物件從一個域傳遞到另一個域</span><span class="sxs-lookup"><span data-stu-id="6b065-116">Passing an object from one domain to another</span></span>
* <span data-ttu-id="6b065-117">將物件作為 JSON 或 XML 字串通過防火牆傳遞</span><span class="sxs-lookup"><span data-stu-id="6b065-117">Passing an object through a firewall as a JSON or XML string</span></span>
* <span data-ttu-id="6b065-118">跨應用程式維護安全或特定于使用者的資訊</span><span class="sxs-lookup"><span data-stu-id="6b065-118">Maintaining security or user-specific information across applications</span></span>

## <a name="json-serialization"></a><span data-ttu-id="6b065-119">JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="6b065-119">JSON serialization</span></span>

<span data-ttu-id="6b065-120">命名<xref:System.Text.Json>空間包含 JavaScript 物件符號 （JSON） 序列化和反序列化的類。</span><span class="sxs-lookup"><span data-stu-id="6b065-120">The <xref:System.Text.Json> namespace contains classes for JavaScript Object Notation (JSON) serialization and deserialization.</span></span> <span data-ttu-id="6b065-121">JSON 是一個開放的標準，通常用於通過網路共用資料。</span><span class="sxs-lookup"><span data-stu-id="6b065-121">JSON is an open standard that is commonly used for sharing data across the web.</span></span>

<span data-ttu-id="6b065-122">JSON 序列化將物件的公共屬性序列化為符合[RFC 8259 JSON 規範的](https://tools.ietf.org/html/rfc8259)字串、位元組陣列或流。</span><span class="sxs-lookup"><span data-stu-id="6b065-122">JSON serialization serializes the public properties of an object into a string, byte array, or stream that conforms to [the RFC 8259 JSON specification](https://tools.ietf.org/html/rfc8259).</span></span> <span data-ttu-id="6b065-123">要控制類實例<xref:System.Text.Json.JsonSerializer>的序列化或反序列化方式，可以：</span><span class="sxs-lookup"><span data-stu-id="6b065-123">To control the way <xref:System.Text.Json.JsonSerializer> serializes or deserializes an instance of the class:</span></span>

* <span data-ttu-id="6b065-124">使用<xref:System.Text.Json.JsonSerializerOptions>物件</span><span class="sxs-lookup"><span data-stu-id="6b065-124">Use a <xref:System.Text.Json.JsonSerializerOptions> object</span></span>
* <span data-ttu-id="6b065-125">將命名空間的屬性<xref:System.Text.Json.Serialization>應用於類或屬性</span><span class="sxs-lookup"><span data-stu-id="6b065-125">Apply attributes from the <xref:System.Text.Json.Serialization> namespace to classes or properties</span></span>
* [<span data-ttu-id="6b065-126">實現自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="6b065-126">Implement custom converters</span></span>](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a><span data-ttu-id="6b065-127">二進位與 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="6b065-127">Binary and XML serialization</span></span>

<span data-ttu-id="6b065-128">命名<xref:System.Runtime.Serialization>空間包含用於二進位和 XML 序列化和反序列化的類。</span><span class="sxs-lookup"><span data-stu-id="6b065-128">The <xref:System.Runtime.Serialization> namespace contains classes for binary and XML serialization and deserialization.</span></span>

<span data-ttu-id="6b065-129">二進位序列化使用二進位編碼來產生精簡的序列化，適用於儲存或通訊端型網路資料流。</span><span class="sxs-lookup"><span data-stu-id="6b065-129">Binary serialization uses binary encoding to produce compact serialization for uses such as storage or socket-based network streams.</span></span> <span data-ttu-id="6b065-130">在二進位序列化中，系統會序列化所有成員 (即使是唯讀的成員)，且效能會增強。</span><span class="sxs-lookup"><span data-stu-id="6b065-130">In binary serialization, all members, even members that are read-only, are serialized, and performance is enhanced.</span></span>

<span data-ttu-id="6b065-131">XML 序列化會將物件的公用欄位和屬性，或是方法的參數和傳回值，序列化為與特定 XML 結構描述定義語言 (XSD) 文件相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="6b065-131">XML serialization serializes the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="6b065-132">XML 序列化會產生強型別的類別，其中包含的公用屬性和欄位都會轉換成 XML。</span><span class="sxs-lookup"><span data-stu-id="6b065-132">XML serialization results in strongly typed classes with public properties and fields that are converted to XML.</span></span> <span data-ttu-id="6b065-133"><xref:System.Xml.Serialization>包含用於序列化和反序列化 XML 的類。</span><span class="sxs-lookup"><span data-stu-id="6b065-133"><xref:System.Xml.Serialization> contains classes for serializing and deserializing XML.</span></span> <span data-ttu-id="6b065-134">您可以將屬性套用至類別和類別成員，以便控制 <xref:System.Xml.Serialization.XmlSerializer> 序列化或還原序列化類別執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="6b065-134">You apply attributes to classes and class members to control the way the <xref:System.Xml.Serialization.XmlSerializer> serializes or deserializes an instance of the class.</span></span>

### <a name="making-an-object-serializable"></a><span data-ttu-id="6b065-135">讓物件可序列化</span><span class="sxs-lookup"><span data-stu-id="6b065-135">Making an object serializable</span></span>

<span data-ttu-id="6b065-136">對於二進位或 XML 序列化，您需要：</span><span class="sxs-lookup"><span data-stu-id="6b065-136">For binary or XML serialization, you need:</span></span>

* <span data-ttu-id="6b065-137">要序列化的物件</span><span class="sxs-lookup"><span data-stu-id="6b065-137">The object to be serialized</span></span>
* <span data-ttu-id="6b065-138">包含序列化物件的流</span><span class="sxs-lookup"><span data-stu-id="6b065-138">A stream to contain the serialized object</span></span>
* <span data-ttu-id="6b065-139"><xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>實例</span><span class="sxs-lookup"><span data-stu-id="6b065-139">A <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> instance</span></span>

<span data-ttu-id="6b065-140">將<xref:System.SerializableAttribute>屬性應用於類型以指示類型實例可以序列化。</span><span class="sxs-lookup"><span data-stu-id="6b065-140">Apply the <xref:System.SerializableAttribute> attribute to a type to indicate that instances of the type can be serialized.</span></span> <span data-ttu-id="6b065-141">如果您嘗試序列化但該類型沒有 <xref:System.SerializableAttribute> 屬性，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b065-141">An  exception is thrown if you attempt to serialize but the type doesn't have the <xref:System.SerializableAttribute> attribute.</span></span>

<span data-ttu-id="6b065-142">要防止欄位序列化，請應用該<xref:System.NonSerializedAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="6b065-142">To prevent a field from being serialized, apply the <xref:System.NonSerializedAttribute> attribute.</span></span> <span data-ttu-id="6b065-143">如果可序列化型別的欄位包含指標、控制代碼，或一些其他特定環境專屬的資料結構，且無法以有意義的方式在不同環境中重新建構該欄位，則您可能想要讓它成為不可序列化的。</span><span class="sxs-lookup"><span data-stu-id="6b065-143">If a field of a serializable type contains a pointer, a handle, or some other data structure that is specific to a particular environment, and the field cannot be meaningfully reconstituted in a different environment, then you may want to make it nonserializable.</span></span>

<span data-ttu-id="6b065-144">如果序列化類別包含對其他類別之物件的參考，且該類別標記為 <xref:System.SerializableAttribute>，則系統也會將那些物件序列化。</span><span class="sxs-lookup"><span data-stu-id="6b065-144">If a serialized class contains references to objects of other classes that are marked <xref:System.SerializableAttribute>, those objects will also be serialized.</span></span>

### <a name="basic-and-custom-serialization"></a><span data-ttu-id="6b065-145">基本和自訂序列化</span><span class="sxs-lookup"><span data-stu-id="6b065-145">Basic and custom serialization</span></span>

<span data-ttu-id="6b065-146">二進位和XML序列化可以通過兩種方式執行，基本和自訂。</span><span class="sxs-lookup"><span data-stu-id="6b065-146">Binary and XML serialization can be performed in two ways, basic and custom.</span></span>

<span data-ttu-id="6b065-147">基本序列化使用 .NET Framework 來自動序列化物件。</span><span class="sxs-lookup"><span data-stu-id="6b065-147">Basic serialization uses the .NET Framework to automatically serialize the object.</span></span> <span data-ttu-id="6b065-148">唯一的要求是類已應用該<xref:System.SerializableAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="6b065-148">The only requirement is that the class has the <xref:System.SerializableAttribute> attribute applied.</span></span> <span data-ttu-id="6b065-149">可以使用 <xref:System.NonSerializedAttribute> 來防止特定欄位被序列化。</span><span class="sxs-lookup"><span data-stu-id="6b065-149">The <xref:System.NonSerializedAttribute> can be used to keep specific fields from being serialized.</span></span>

<span data-ttu-id="6b065-150">當您使用基本序列化時，物件的版本控制可能產生問題。</span><span class="sxs-lookup"><span data-stu-id="6b065-150">When you use basic serialization, the versioning of objects may create problems.</span></span> <span data-ttu-id="6b065-151">版本控制的問題很重要時，建議使用自訂序列化。</span><span class="sxs-lookup"><span data-stu-id="6b065-151">You would use custom serialization when versioning issues are important.</span></span> <span data-ttu-id="6b065-152">基本序列化是執行序列化最簡單的方式，但它對該程序提供的控制機制並不多。</span><span class="sxs-lookup"><span data-stu-id="6b065-152">Basic serialization is the easiest way to perform serialization, but it does not provide much control over the process.</span></span>

<span data-ttu-id="6b065-153">在自訂序列化中，您可以明確指定要序列化的物件，以及序列化的方式。</span><span class="sxs-lookup"><span data-stu-id="6b065-153">In custom serialization, you can specify exactly which objects will be serialized and how it will be done.</span></span> <span data-ttu-id="6b065-154">類別必須標記為 <xref:System.SerializableAttribute> 並實作 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="6b065-154">The class must be marked <xref:System.SerializableAttribute> and implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="6b065-155">如果希望以自訂方式反序列化物件，請使用自訂建構函式。</span><span class="sxs-lookup"><span data-stu-id="6b065-155">If you want your object to be deserialized in a custom manner as well, use a custom constructor.</span></span>

## <a name="designer-serialization"></a><span data-ttu-id="6b065-156">設計工具序列化</span><span class="sxs-lookup"><span data-stu-id="6b065-156">Designer serialization</span></span>

<span data-ttu-id="6b065-157">設計工具序列化是特殊格式的序列化，其中包含一種與開發工具相關聯的物件持續性。</span><span class="sxs-lookup"><span data-stu-id="6b065-157">Designer serialization is a special form of serialization that involves the kind of object persistence associated with development tools.</span></span> <span data-ttu-id="6b065-158">設計工具序列化程序的作用是將物件圖形轉換成來源檔案，而該檔案稍後可用於復原物件圖形。</span><span class="sxs-lookup"><span data-stu-id="6b065-158">Designer serialization is the process of converting an object graph into a source file that can later be used to recover the object graph.</span></span> <span data-ttu-id="6b065-159">來源檔案可以包含程式碼、標記，或甚至 SQL 資料表資訊。</span><span class="sxs-lookup"><span data-stu-id="6b065-159">A source file can contain code, markup, or even SQL table information.</span></span>

## <a name="BKMK_RelatedTopics"></a> <span data-ttu-id="6b065-160">相關主題和範例</span><span class="sxs-lookup"><span data-stu-id="6b065-160">Related Topics and Examples</span></span>  

<span data-ttu-id="6b065-161">[系統.文本.Json 概述](../../../../standard/serialization/system-text-json-overview.md)演示如何獲取`System.Text.Json`庫。</span><span class="sxs-lookup"><span data-stu-id="6b065-161">[System.Text.Json overview](../../../../standard/serialization/system-text-json-overview.md) Shows how to get the `System.Text.Json` library.</span></span>

<span data-ttu-id="6b065-162">[如何在 .NET 中序列化和反序列化 JSON。](../../../../standard/serialization/system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="6b065-162">[How to serialize and deserialize JSON in .NET](../../../../standard/serialization/system-text-json-how-to.md).</span></span>
<span data-ttu-id="6b065-163">演示如何使用<xref:System.Text.Json.JsonSerializer>類讀取和寫入 JSON 的物件資料。</span><span class="sxs-lookup"><span data-stu-id="6b065-163">Shows how to read and write object data to and from JSON using the <xref:System.Text.Json.JsonSerializer> class.</span></span>

[<span data-ttu-id="6b065-164">逐步解說：在 Visual Studio 中保存物件 (#C)</span><span class="sxs-lookup"><span data-stu-id="6b065-164">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>](walkthrough-persisting-an-object-in-visual-studio.md)  
<span data-ttu-id="6b065-165">示範序列化能如何用來保存物件在執行個體之間的資料，可讓您儲存值，並且在下次物件具現化時擷取它們。</span><span class="sxs-lookup"><span data-stu-id="6b065-165">Demonstrates how serialization can be used to persist an object's data between instances, allowing you to store values and retrieve them the next time the object is instantiated.</span></span>

[<span data-ttu-id="6b065-166">如何從 XML 檔 （C#） 讀取物件資料</span><span class="sxs-lookup"><span data-stu-id="6b065-166">How to read object data from an XML file (C#)</span></span>](how-to-read-object-data-from-an-xml-file.md)  
<span data-ttu-id="6b065-167">示範如何讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。</span><span class="sxs-lookup"><span data-stu-id="6b065-167">Shows how to read object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>

[<span data-ttu-id="6b065-168">如何將物件資料寫入 XML 檔 （C#）</span><span class="sxs-lookup"><span data-stu-id="6b065-168">How to write object data to an XML file (C#)</span></span>](how-to-write-object-data-to-an-xml-file.md)  
<span data-ttu-id="6b065-169">示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6b065-169">Shows how to write the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>
