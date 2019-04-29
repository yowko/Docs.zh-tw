---
title: 序列化方針
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: 05cbe8b18a0d9635091b373d0acddb2ba665cc37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794300"
---
# <a name="serialization-guidelines"></a><span data-ttu-id="c0986-102">序列化方針</span><span class="sxs-lookup"><span data-stu-id="c0986-102">Serialization guidelines</span></span>
<span data-ttu-id="c0986-103">本文件列出在設計要序列化的 API 時所要考量的指導方針。</span><span class="sxs-lookup"><span data-stu-id="c0986-103">This document lists the guidelines to consider when designing an API to be serialized.</span></span>  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 <span data-ttu-id="c0986-104">.NET 提供已針對多個序列化案例最佳化的三個主要序列化技術。</span><span class="sxs-lookup"><span data-stu-id="c0986-104">.NET offers three main serialization technologies that are optimized for various serialization scenarios.</span></span> <span data-ttu-id="c0986-105">下表列出這些技術以及與這些技術相關的主要 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="c0986-105">The following table lists these technologies and the main .NET types related to these technologies.</span></span>  
  
|<span data-ttu-id="c0986-106">技術</span><span class="sxs-lookup"><span data-stu-id="c0986-106">Technology</span></span>|<span data-ttu-id="c0986-107">相關類別</span><span class="sxs-lookup"><span data-stu-id="c0986-107">Relevant Classes</span></span>|<span data-ttu-id="c0986-108">注意</span><span class="sxs-lookup"><span data-stu-id="c0986-108">Notes</span></span>|  
|----------------|----------------------|-----------|  
|<span data-ttu-id="c0986-109">資料合約序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-109">Data Contract Serialization</span></span>|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|<span data-ttu-id="c0986-110">一般持續性</span><span class="sxs-lookup"><span data-stu-id="c0986-110">General persistence</span></span><br /><br /> <span data-ttu-id="c0986-111">Web 服務</span><span class="sxs-lookup"><span data-stu-id="c0986-111">Web Services</span></span><br /><br /> <span data-ttu-id="c0986-112">JSON</span><span class="sxs-lookup"><span data-stu-id="c0986-112">JSON</span></span>|  
|<span data-ttu-id="c0986-113">XML 序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-113">XML Serialization</span></span>|<xref:System.Xml.Serialization.XmlSerializer>|<span data-ttu-id="c0986-114">XML 格式</span><span class="sxs-lookup"><span data-stu-id="c0986-114">XML format</span></span> <br /><span data-ttu-id="c0986-115">(具有完全控制)</span><span class="sxs-lookup"><span data-stu-id="c0986-115">with full control</span></span>|  
|<span data-ttu-id="c0986-116">執行階段 - 序列化 (二進位和 SOAP)</span><span class="sxs-lookup"><span data-stu-id="c0986-116">Runtime -Serialization (Binary and SOAP)</span></span>|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|<span data-ttu-id="c0986-117">.NET 遠端處理</span><span class="sxs-lookup"><span data-stu-id="c0986-117">.NET Remoting</span></span>|  
  
 <span data-ttu-id="c0986-118">當您設計新的型別時，您應該決定這些型別必須支援哪些技術 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="c0986-118">When you design new types, you should decide which, if any, of these technologies those types need to support.</span></span> <span data-ttu-id="c0986-119">下列指導方針說明如何做出這項決定以及如何提供這類支援。</span><span class="sxs-lookup"><span data-stu-id="c0986-119">The following guidelines describe how to make that choice and how to provide such support.</span></span> <span data-ttu-id="c0986-120">這些指導方針並不是為了幫助您選擇應該在應用程式或程式庫的實作中使用哪一種序列化技術。</span><span class="sxs-lookup"><span data-stu-id="c0986-120">These guidelines are not meant to help you choose which serialization technology you should use in the implementation of your application or library.</span></span> <span data-ttu-id="c0986-121">這類指導方針與 API 設計沒有直接的關聯性，所以不在本主題的討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="c0986-121">Such guidelines are not directly related to API design and thus are not within the scope of this topic.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="c0986-122">方針</span><span class="sxs-lookup"><span data-stu-id="c0986-122">Guidelines</span></span>  
  
- <span data-ttu-id="c0986-123">當您設計新的型別時，請務必考量序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-123">DO think about serialization when you design new types.</span></span>  
  
     <span data-ttu-id="c0986-124">對任何型別而言，序列化都是重要的設計考量，因為程式可能需要保存或傳輸該型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0986-124">Serialization is an important design consideration for any type, because programs might need to persist or transmit instances of the type.</span></span>  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a><span data-ttu-id="c0986-125">選擇要支援的正確序列化技術</span><span class="sxs-lookup"><span data-stu-id="c0986-125">Choosing the right serialization technology to support</span></span>  
 <span data-ttu-id="c0986-126">任何給定型別都可以支援零個、一個或多個序列化技術。</span><span class="sxs-lookup"><span data-stu-id="c0986-126">Any given type can support none, one, or more of the serialization technologies.</span></span>  
  
- <span data-ttu-id="c0986-127">如果可能需要在 Web 服務中持續保存或使用類型的執行個體，請考慮支援「資料合約序列化」。</span><span class="sxs-lookup"><span data-stu-id="c0986-127">CONSIDER supporting *data contract serialization* if instances of your type might need to be persisted or used in Web Services.</span></span>  
  
- <span data-ttu-id="c0986-128">如果您需要針對序列化類型時所產生之 XML 格式的更大控制權，請考慮支援「XML 序列化」來取代資料合約序列化，或是兩者都支援。</span><span class="sxs-lookup"><span data-stu-id="c0986-128">CONSIDER supporting the *XML serialization* instead of or in addition to data contract serialization if you need more control over the XML format that is produced when the type is serialized.</span></span>  
  
     <span data-ttu-id="c0986-129">在您需要使用資料合約序列化所不支援的 XML 建構的某些互通性情況下 (例如，為了產生 XML 屬性)，就可能需要這樣的處理方式。</span><span class="sxs-lookup"><span data-stu-id="c0986-129">This may be necessary in some interoperability scenarios where you need to use an XML construct that is not supported by data contract serialization, for example, to produce XML attributes.</span></span>  
  
- <span data-ttu-id="c0986-130">如果類別的執行個體需要橫跨 .NET 遠端處理界限，請考慮支援「執行階段序列化」。</span><span class="sxs-lookup"><span data-stu-id="c0986-130">CONSIDER supporting *runtime serialization* if instances of your type need to travel across .NET Remoting boundaries.</span></span>  
  
- <span data-ttu-id="c0986-131">請避免針對一般持續性理由來支援執行階段序列化或 XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-131">AVOID supporting runtime serialization or XML serialization just for general persistence reasons.</span></span> <span data-ttu-id="c0986-132">請改用資料合約序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-132">Prefer data contract serialization instead</span></span>  
  
#### <a name="supporting-data-contract-serialization"></a><span data-ttu-id="c0986-133">支援資料合約序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-133">Supporting data contract serialization</span></span>  
 <span data-ttu-id="c0986-134">類型可以將 <xref:System.Runtime.Serialization.DataContractAttribute> 套用至類型，並將 <xref:System.Runtime.Serialization.DataMemberAttribute> 套用至類型的成員 (欄位和屬性) 來支援資料合約序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-134">Types can support data contract serialization by applying the <xref:System.Runtime.Serialization.DataContractAttribute> to the type and the <xref:System.Runtime.Serialization.DataMemberAttribute> to the members (fields and properties) of the type.</span></span>  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1. <span data-ttu-id="c0986-135">如果可以在部分信任中使用型別，請考慮將型別的資料成員標記為 public。</span><span class="sxs-lookup"><span data-stu-id="c0986-135">CONSIDER marking data members of your type public if the type can be used in partial trust.</span></span> <span data-ttu-id="c0986-136">在完全信任中，資料合約序列化程式可以序列化及還原序列化非 public 型別和成員，但是只有 public 成員可以在部分信任中序列化及還原序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-136">In full trust, data contract serializers can serialize and deserialize nonpublic types and members, but only public members can be serialized and deserialized in partial trust.</span></span>  
  
2. <span data-ttu-id="c0986-137">請針對具有 Data-MemberAttribute 的所有屬性實作 getter 和 setter。</span><span class="sxs-lookup"><span data-stu-id="c0986-137">DO implement a getter and setter on all properties that have Data-MemberAttribute.</span></span> <span data-ttu-id="c0986-138">資料合約序列化程式需要 getter 和 setter，才能考慮將此型別序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-138">Data contract serializers require both the getter and the setter for the type to be considered serializable.</span></span> <span data-ttu-id="c0986-139">如果此型別不會在部分信任中使用，則其中一個或兩個屬性存取子可以不是 public。</span><span class="sxs-lookup"><span data-stu-id="c0986-139">If the type won’t be used in partial trust, one or both of the property accessors can be nonpublic.</span></span>  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3. <span data-ttu-id="c0986-140">請考慮針對還原序列化之執行個體的初始化使用序列化回呼。</span><span class="sxs-lookup"><span data-stu-id="c0986-140">CONSIDER using the serialization callbacks for initialization of deserialized instances.</span></span>  
  
     <span data-ttu-id="c0986-141">當還原序列化物件時，不會呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="c0986-141">Constructors are not called when objects are deserialized.</span></span> <span data-ttu-id="c0986-142">因此，正常建構期間所執行的任何邏輯都需要實作為其中一個「序列化回呼」。</span><span class="sxs-lookup"><span data-stu-id="c0986-142">Therefore, any logic that executes during normal construction needs to be implemented as one of the *serialization callbacks*.</span></span>  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <span data-ttu-id="c0986-143"><xref:System.Runtime.Serialization.OnDeserializedAttribute> 屬性是最常用的回呼屬性。</span><span class="sxs-lookup"><span data-stu-id="c0986-143">The <xref:System.Runtime.Serialization.OnDeserializedAttribute> attribute is the most commonly used callback attribute.</span></span> <span data-ttu-id="c0986-144">此系列中的其他屬性為 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、</span><span class="sxs-lookup"><span data-stu-id="c0986-144">The other attributes in the family are <xref:System.Runtime.Serialization.OnDeserializingAttribute>,</span></span>    
    <span data-ttu-id="c0986-145"><xref:System.Runtime.Serialization.OnSerializingAttribute>與<xref:System.Runtime.Serialization.OnSerializedAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c0986-145"><xref:System.Runtime.Serialization.OnSerializingAttribute>, and <xref:System.Runtime.Serialization.OnSerializedAttribute>.</span></span> <span data-ttu-id="c0986-146">這些屬性可用來分別標記在還原序列化之前、序列化之前以及最後在序列化之後所執行的回呼。</span><span class="sxs-lookup"><span data-stu-id="c0986-146">They can be used to mark callbacks that get executed before deserialization, before serialization, and finally, after serialization, respectively.</span></span>  
  
4. <span data-ttu-id="c0986-147">當您還原序列化複雜物件圖形時，請考慮使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 來指示應該使用的具象型別。</span><span class="sxs-lookup"><span data-stu-id="c0986-147">CONSIDER using the <xref:System.Runtime.Serialization.KnownTypeAttribute> to indicate concrete types that should be used when deserializing a complex object graph.</span></span>  
  
     <span data-ttu-id="c0986-148">例如，如果還原序列化之資料成員的某個類型以抽象類別來表示，則序列化程式將需要「已知類型」資訊來決定哪一個具象類型要執行個體化以及指派給成員。</span><span class="sxs-lookup"><span data-stu-id="c0986-148">For example, if a type of a deserialized data member is represented by an abstract class, the serializer will need the *known type* information to decide what concrete type to instantiate and assign to the member.</span></span> <span data-ttu-id="c0986-149">如果已知型別不是使用此屬性所指定，它需要明確傳遞給序列化程式 (您可以將已知型別傳遞給序列化程式建構函式來進行這項處理)，或者需要在組態檔中指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="c0986-149">If the known type is not specified using the attribute, it will need to be passed to the serializer explicitly (you can do it by passing known types to the serializer constructor) or it will need to be specified in the configuration file.</span></span>  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     <span data-ttu-id="c0986-150">如果已知類型清單無法以靜態方式得知 (編譯 **Person** 類別時)，**KnownTypeAttribute** 也可指向一個方法，此方法會在執行階段傳回已知類型清單。</span><span class="sxs-lookup"><span data-stu-id="c0986-150">In cases where the list of known types is not known statically (when the **Person** class is compiled), the **KnownTypeAttribute** can also point to a method that returns a list of known types at runtime.</span></span>  
  
5. <span data-ttu-id="c0986-151">當建立或變更可序列化的型別時，請務必考慮回溯相容性與向前相容性。</span><span class="sxs-lookup"><span data-stu-id="c0986-151">DO consider backward and forward compatibility when creating or changing serializable types.</span></span>  
  
     <span data-ttu-id="c0986-152">請牢記，型別之未來版本的序列化資料流可以還原序列化成該型別的目前版本，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="c0986-152">Keep in mind that serialized streams of future versions of your type can be deserialized into the current version of the type, and vice versa.</span></span> <span data-ttu-id="c0986-153">請務必了解資料成員 (即使是 private 和內部成員) 在型別的未來版本中無法變更其名稱、型別或甚至是順序，除非採取特別的步驟，利用資料合約屬性的明確參數來保留合約。在變更可序列化的型別時，請測試序列化的相容性。</span><span class="sxs-lookup"><span data-stu-id="c0986-153">Make sure you understand that data members, even private and internal, cannot change their names, types, or even their order in future versions of the type unless special care is taken to preserve the contract using explicit parameters to the data contract attributes.Test compatibility of serialization when making changes to serializable types.</span></span> <span data-ttu-id="c0986-154">請嘗試將新的版本還原序列化成舊的版本，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="c0986-154">Try deserializing the new version into an old version, and vice versa.</span></span>  
  
6. <span data-ttu-id="c0986-155">請考慮實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面來允許在型別的不同版本之間往返。</span><span class="sxs-lookup"><span data-stu-id="c0986-155">CONSIDER implementing <xref:System.Runtime.Serialization.IExtensibleDataObject> interface to allow round-tripping between different versions of the type.</span></span>  
  
     <span data-ttu-id="c0986-156">此介面可讓序列化程式確保往返期間不會有任何資料遺失。</span><span class="sxs-lookup"><span data-stu-id="c0986-156">The interface allows the serializer to ensure that no data is lost during round-tripping.</span></span> <span data-ttu-id="c0986-157"><xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 屬性會儲存來自目前版本未知之型別的未來版本中的任何資料。</span><span class="sxs-lookup"><span data-stu-id="c0986-157">The <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property stores any data from the future version of the type that is unknown to the current version.</span></span> <span data-ttu-id="c0986-158">當目前版本接著序列化並還原序列化成未來版本時，其他資料將會透過 **ExtensionData** 屬性值在序列化資料流中提供。</span><span class="sxs-lookup"><span data-stu-id="c0986-158">When the current version is subsequently serialized and deserialized into a future version, the additional data will be available in the serialized stream through the **ExtensionData** property value.</span></span>  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     <span data-ttu-id="c0986-159">如需詳細資訊，請參閱[向前相容資料合約](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="c0986-159">For more information, see [Forward-Compatible Data Contracts](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
#### <a name="supporting-xml-serialization"></a><span data-ttu-id="c0986-160">支援 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-160">Supporting XML serialization</span></span>  
 <span data-ttu-id="c0986-161">資料合約序列化是 .NET Framework 中的主要 (預設) 序列化技術，但是資料合約序列化不支援一些序列化情節。</span><span class="sxs-lookup"><span data-stu-id="c0986-161">Data contract serialization is the main (default) serialization technology in the .NET Framework, but there are serialization scenarios that data contract serialization does not support.</span></span> <span data-ttu-id="c0986-162">例如，它無法讓您完全控制序列化程式所產生或使用之 XML 的形狀。</span><span class="sxs-lookup"><span data-stu-id="c0986-162">For example, it does not give you full control over the shape of XML produced or consumed by the serializer.</span></span> <span data-ttu-id="c0986-163">如果需要這樣的精確控制，必須使用「XML 序列化」，而且您需要設計您的類型來支援這項序列化技術。</span><span class="sxs-lookup"><span data-stu-id="c0986-163">If such fine control is required, *XML serialization* has to be used, and you need to design your types to support this serialization technology.</span></span>  
  
1. <span data-ttu-id="c0986-164">請避免專門為了 XML 序列化來設計型別，除非您有非常強烈的理由為了控制所產生之 XML 的形狀。</span><span class="sxs-lookup"><span data-stu-id="c0986-164">AVOID designing your types specifically for XML Serialization, unless you have a very strong reason to control the shape of the XML produced.</span></span> <span data-ttu-id="c0986-165">這項序列化技術已經由前一節所討論的資料合約序列化所取代。</span><span class="sxs-lookup"><span data-stu-id="c0986-165">This serialization technology has been superseded by the Data Contract Serialization discussed in the previous section.</span></span>  
  
     <span data-ttu-id="c0986-166">換句話說，請勿將 <xref:System.Xml.Serialization> 命名空間中的屬性套用至新的型別，除非您知道此型別將會搭配 XML 序列化使用。</span><span class="sxs-lookup"><span data-stu-id="c0986-166">In other words, don’t apply attributes from the <xref:System.Xml.Serialization> namespace to new types, unless you know that the type will be used with XML Serialization.</span></span> <span data-ttu-id="c0986-167">下列範例示範如何使用 **System.Xml.Serialization** 來控制所產生 XML 的圖形。</span><span class="sxs-lookup"><span data-stu-id="c0986-167">The following example shows how **System.Xml.Serialization** can be used to control the shape of the XML -produced.</span></span>  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2. <span data-ttu-id="c0986-168">如果您希望對序列化 XML 的形狀有更大的控制權，而不是套用 XML 序列化屬性來使用提供的控制權，請考慮實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="c0986-168">CONSIDER implementing the <xref:System.Xml.Serialization.IXmlSerializable> interface if you want even more control over the shape of the serialized XML than what’s offered by applying the XML Serialization attributes.</span></span> <span data-ttu-id="c0986-169">此介面的兩種方法<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>和<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>，可讓您完全控制序列化的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="c0986-169">Two methods of the interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, allow you to fully control the serialized XML stream.</span></span> <span data-ttu-id="c0986-170">您也可以藉由套用 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性來控制為此型別產生的 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c0986-170">You can also control the XML schema that gets generated for the type by applying the <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute.</span></span>  
  
#### <a name="supporting-runtime-serialization"></a><span data-ttu-id="c0986-171">支援執行階段序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-171">Supporting runtime serialization</span></span>  
 <span data-ttu-id="c0986-172">「執行階段序列化」是 .NET 遠端處理所使用的技術。</span><span class="sxs-lookup"><span data-stu-id="c0986-172">*Runtime serialization* is a technology used by .NET Remoting.</span></span> <span data-ttu-id="c0986-173">如果您認為您的型別將會使用 .NET 遠端處理來傳輸，則需要確定型別有支援執行階段序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-173">If you think your types will be transported using .NET Remoting, you need to make sure they support runtime serialization.</span></span>  
  
 <span data-ttu-id="c0986-174">「執行階段序列化」的基本支援可以藉由套用 <xref:System.SerializableAttribute> 屬性來提供，而更進階的案例則牽涉到實作簡單的「執行階段可序列化模式」(實作 -<xref:System.Runtime.Serialization.ISerializable> 並提供序列化建構函式)。</span><span class="sxs-lookup"><span data-stu-id="c0986-174">The basic support for *runtime serialization* can be provided by applying the <xref:System.SerializableAttribute> attribute, and more advanced scenarios involve implementing a simple *runtime serializable pattern* (implement -<xref:System.Runtime.Serialization.ISerializable> and provide a serialization constructor).</span></span>  
  
1. <span data-ttu-id="c0986-175">如果您的型別將會搭配 .NET 遠端處理使用，請考慮支援執行階段序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-175">CONSIDER supporting runtime serialization if your types will be used with .NET Remoting.</span></span> <span data-ttu-id="c0986-176">例如，<xref:System.AddIn> 命名空間會使用 .NET 遠端處理，因此在 **System.AddIn** 增益集之間交換的所有類型都需要支援執行階段序列化。</span><span class="sxs-lookup"><span data-stu-id="c0986-176">For example, the <xref:System.AddIn> namespace uses .NET Remoting, and so all types exchanged between **System.AddIn** add-ins need to support runtime serialization.</span></span>  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2. <span data-ttu-id="c0986-177">如果您想要擁有序列化處理序的完整控制權，請考慮實作「執行階段可序列化模式」。</span><span class="sxs-lookup"><span data-stu-id="c0986-177">CONSIDER implementing the *runtime serializable pattern* if you want complete control over the serialization process.</span></span> <span data-ttu-id="c0986-178">例如，如果您想要在資料序列化或還原序列化時加以轉換。</span><span class="sxs-lookup"><span data-stu-id="c0986-178">For example, if you want to transform data as it gets serialized or deserialized.</span></span>  
  
     <span data-ttu-id="c0986-179">此模式非常簡單。</span><span class="sxs-lookup"><span data-stu-id="c0986-179">The pattern is very simple.</span></span> <span data-ttu-id="c0986-180">您只需要實作 <xref:System.Runtime.Serialization.ISerializable> 介面，並提供還原序列化物件時使用的特殊建構函式。</span><span class="sxs-lookup"><span data-stu-id="c0986-180">All you need to do is implement the <xref:System.Runtime.Serialization.ISerializable> interface and provide a special constructor that is used when the object is deserialized.</span></span>  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3. <span data-ttu-id="c0986-181">請讓序列化建構函式處於受保護狀態，並提供兩個參數，這兩個參數的型別與名稱與此處範例所顯示的一模一樣。</span><span class="sxs-lookup"><span data-stu-id="c0986-181">DO make the serialization constructor protected and provide two parameters typed and named exactly as shown in the sample here.</span></span>  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4. <span data-ttu-id="c0986-182">請務必明確實作 ISerializable 成員。</span><span class="sxs-lookup"><span data-stu-id="c0986-182">DO implement the ISerializable members explicitly.</span></span>  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5. <span data-ttu-id="c0986-183">DO 會將連結要求套用至 **ISerializable.GetObjectData** 實作。</span><span class="sxs-lookup"><span data-stu-id="c0986-183">DO apply a link demand to **ISerializable.GetObjectData** implementation.</span></span> <span data-ttu-id="c0986-184">如此可確保只有完全受信任的核心和執行階段序列化程式可存取此成員。</span><span class="sxs-lookup"><span data-stu-id="c0986-184">This ensures that only fully trusted core and the runtime serializer have access to the member.</span></span>  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c0986-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0986-185">See also</span></span>

- [<span data-ttu-id="c0986-186">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="c0986-186">Using Data Contracts</span></span>](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="c0986-187">資料合約序列化程式</span><span class="sxs-lookup"><span data-stu-id="c0986-187">Data Contract Serializer</span></span>](../../../docs/framework/wcf/feature-details/data-contract-serializer.md)
- [<span data-ttu-id="c0986-188">資料合約序列化程式支援的類型</span><span class="sxs-lookup"><span data-stu-id="c0986-188">Types Supported by the Data Contract Serializer</span></span>](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [<span data-ttu-id="c0986-189">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-189">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="c0986-190">[.NET 遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c0986-190">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))</span></span>
- [<span data-ttu-id="c0986-191">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-191">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="c0986-192">安全性和序列化</span><span class="sxs-lookup"><span data-stu-id="c0986-192">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
