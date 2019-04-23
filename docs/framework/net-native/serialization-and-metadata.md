---
title: 序列化和中繼資料
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207026"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="5336d-102">序列化和中繼資料</span><span class="sxs-lookup"><span data-stu-id="5336d-102">Serialization and Metadata</span></span>
<span data-ttu-id="5336d-103">如果您的應用程式將物件序列化和還原序列化，您可能需要將項目加入至執行階段指示詞 (.rd.xml) 檔案，以確保執行階段有必要的中繼資料存在。</span><span class="sxs-lookup"><span data-stu-id="5336d-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="5336d-104">有兩種類別的序列化程式，在執行階段指示詞檔案中，各需要不同的處理：</span><span class="sxs-lookup"><span data-stu-id="5336d-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
-   <span data-ttu-id="5336d-105">反映型協力廠商序列化程式。</span><span class="sxs-lookup"><span data-stu-id="5336d-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="5336d-106">這些序列化程式需要修改您的執行階段指示詞檔案，將在下一節中討論。</span><span class="sxs-lookup"><span data-stu-id="5336d-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
-   <span data-ttu-id="5336d-107">您可以在 .NET Framework 類別庫中找到非反映型序列化程式。</span><span class="sxs-lookup"><span data-stu-id="5336d-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="5336d-108">這些序列化程式可能需要修改您的執行階段指示詞檔案，將在 [Microsoft 序列化程式](#Microsoft)一節中討論。</span><span class="sxs-lookup"><span data-stu-id="5336d-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="5336d-109">協力廠商序列化程式</span><span class="sxs-lookup"><span data-stu-id="5336d-109">Third-party serializers</span></span>  
 <span data-ttu-id="5336d-110">協力廠商序列化程式 (包括 Newtonsoft.JSON) 通常是反映型。</span><span class="sxs-lookup"><span data-stu-id="5336d-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="5336d-111">若指定序列化資料的二進位大型物件 (BLOB)，將會依名稱查閱目標類型的欄位，以將資料中的欄位指派給具象類型。</span><span class="sxs-lookup"><span data-stu-id="5336d-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="5336d-112">針對您嘗試在 `List<Type>` 集合中序列化或還原序列化的每個 <xref:System.Type> 物件，使用這些程式庫至少會導致 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5336d-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="5336d-113">若要為這些序列化程式解決因遺失中繼資料而導致的問題，最簡單的方法，就是收集要在單一命名空間 (例如 `App.Models`) 之下用於序列化的類型，並套用 `Serialize` 中繼資料指示詞：</span><span class="sxs-lookup"><span data-stu-id="5336d-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="5336d-114">如需範例中所使用語法的資訊，請參閱 [\<Namespace> 項目](../../../docs/framework/net-native/namespace-element-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="5336d-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="5336d-115">Microsoft 序列化程式</span><span class="sxs-lookup"><span data-stu-id="5336d-115">Microsoft serializers</span></span>  
 <span data-ttu-id="5336d-116">雖然 <xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer> 類別不會依賴反映，但確實需要根據所要序列化或還原序列化的物件來產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="5336d-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="5336d-117">適用於每個序列化程式的多載建構函式，包括用來指定要序列化或還原序列化之類型的 <xref:System.Type> 參數。</span><span class="sxs-lookup"><span data-stu-id="5336d-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="5336d-118">您用來將該類型指定在程式碼中的方式，會定義您必須採取的動作，在下兩節中將進行討論。</span><span class="sxs-lookup"><span data-stu-id="5336d-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="5336d-119">用於建構函式的 typeof</span><span class="sxs-lookup"><span data-stu-id="5336d-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="5336d-120">如果您呼叫這些序列化類別的建構函式，並將 C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) 關鍵字包含在方法呼叫中，**就不需要執行任何額外的工作**。</span><span class="sxs-lookup"><span data-stu-id="5336d-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="5336d-121">例如，在對序列化類別建構函式進行的下列每個呼叫中，`typeof` 關鍵字會用來做為傳遞至建構函式之運算式的一部分。</span><span class="sxs-lookup"><span data-stu-id="5336d-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="5336d-122">[!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器將會自動處理這個程式碼。</span><span class="sxs-lookup"><span data-stu-id="5336d-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="5336d-123">在建構函式外部使用的 typeof</span><span class="sxs-lookup"><span data-stu-id="5336d-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="5336d-124">如果您呼叫這些序列化類別的建構函式，並且在提供給建構函式之 <xref:System.Type> 參數的運算式外部，使用 C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) 關鍵字 (如下列程式碼所示)，則 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器無法解析類型：</span><span class="sxs-lookup"><span data-stu-id="5336d-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="5336d-125">在此情況下，您必須加入像下列這樣的項目，以在執行階段指示詞檔案中指定類型：</span><span class="sxs-lookup"><span data-stu-id="5336d-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="5336d-126">同樣地，如果您呼叫 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> 之類的建構函式，並提供要序列化的其他 <xref:System.Type> 物件陣列 (如下列程式碼)，則 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器無法解析這些類型。</span><span class="sxs-lookup"><span data-stu-id="5336d-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="5336d-127">您必須針對每一種類型，在執行階段指示詞檔案中加入像下列的項目：</span><span class="sxs-lookup"><span data-stu-id="5336d-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="5336d-128">如需範例中所使用語法的資訊，請參閱 [\<Type> 項目](../../../docs/framework/net-native/type-element-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="5336d-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5336d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5336d-129">See also</span></span>

- [<span data-ttu-id="5336d-130">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="5336d-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="5336d-131">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="5336d-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="5336d-132">\<型別 > 項目</span><span class="sxs-lookup"><span data-stu-id="5336d-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="5336d-133">\<Namespace> 項目</span><span class="sxs-lookup"><span data-stu-id="5336d-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
