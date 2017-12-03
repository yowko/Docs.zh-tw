---
title: "可序列化的型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a><span data-ttu-id="9f6fc-102">可序列化的型別</span><span class="sxs-lookup"><span data-stu-id="9f6fc-102">Serializable Types</span></span>
<span data-ttu-id="9f6fc-103">根據預設，<xref:System.Runtime.Serialization.DataContractSerializer> 會序列化所有公開可見的型別。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="9f6fc-104">型別的所有公用讀取/寫入屬性 (Property) 和欄位都會序列化。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="9f6fc-105">您可以透過將 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至型別和成員的方式來變更預設行為。當您擁有的型別並非您所能控制，而且無法經過修改以加入屬性時，這個功能便相當實用。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="9f6fc-106"><xref:System.Runtime.Serialization.DataContractSerializer> 會識別這類「未標記」的型別。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="9f6fc-107">序列化預設值</span><span class="sxs-lookup"><span data-stu-id="9f6fc-107">Serialization Defaults</span></span>  
 <span data-ttu-id="9f6fc-108">您可以套用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性，以便明確控制或自訂型別和成員的序列化作業。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="9f6fc-109">此外，您可以將這些屬性套用至私用欄位。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="9f6fc-110">不過，即使未以這些屬性標記的型別，仍可以進行序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="9f6fc-111">以下為適用的規則和例外狀況：</span><span class="sxs-lookup"><span data-stu-id="9f6fc-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="9f6fc-112"><xref:System.Runtime.Serialization.DataContractSerializer> 會使用新建立型別的預設屬性 (Property)，從未包含屬性 (Attribute) 的型別推斷資料合約。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="9f6fc-113">除非您將 `get` 屬性 (Attribute) 套用至該成員，否則所有公用欄位，以及含有公用 `set` 和 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 方法的屬性 (Property) 都會加以序列化。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="9f6fc-114">序列化語意 (Semantics) 與 <xref:System.Xml.Serialization.XmlSerializer> 的語意相似。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="9f6fc-115">在未標記的型別中，只有具有未包含參數之建構函式 (Constructor) 的公用型別才會序列化。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="9f6fc-116">這個規則的例外情形是搭配 <xref:System.Runtime.Serialization.ExtensionDataObject> 介面使用的 <xref:System.Runtime.Serialization.IExtensibleDataObject>。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="9f6fc-117">唯讀欄位、沒有 `get` 或 `set` 方法的屬性，以及具有內部或私用 `set` 或 `get` 方法的屬性不會序列化。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="9f6fc-118">這類屬性會被略過，而且不會擲回例外狀況，但不包括 get-only 集合。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="9f6fc-119"><xref:System.Xml.Serialization.XmlSerializer> 屬性 (例如 `XmlElement`、`XmlAttribute`、`XmlIgnore`、`XmlInclude` 等屬性) 會被略過。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="9f6fc-120">如果您未將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至指定的型別，則序列化程式會忽略該型別中任何已套用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="9f6fc-121">未標記 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> 屬性 (Attribute) 的型別支援 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="9f6fc-122">這包括支援未標記型別上的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="9f6fc-123">若要「選擇不」序列化公用成員、屬性 (Property) 或欄位的處理序，請將 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 屬性 (Attribute) 套用至該成員。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="9f6fc-124">繼承</span><span class="sxs-lookup"><span data-stu-id="9f6fc-124">Inheritance</span></span>  
 <span data-ttu-id="9f6fc-125">未標記的型別 (沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性的型別) 可以繼承自沒有這個屬性的型別，不過不允許反向操作，也就是說，擁有這個屬性的型別無法繼承自未標記的型別。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="9f6fc-126">強制執行這個規則的主要原因，是為了確保與使用舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 撰寫的程式碼回溯相容。</span><span class="sxs-lookup"><span data-stu-id="9f6fc-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6fc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f6fc-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="9f6fc-128">資料合約序列化程式所支援的類型</span><span class="sxs-lookup"><span data-stu-id="9f6fc-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
