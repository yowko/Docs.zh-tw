---
title: 資料合約已知型別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: dc297bd35d7bfdb25fc50135b8e684e1b9452cb2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592579"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="2b207-102">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="2b207-102">Data Contract Known Types</span></span>
<span data-ttu-id="2b207-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> 類別可讓您預先指定在還原序列化期間應該納入考量的型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="2b207-104">如需實用範例，請參閱 [Known Types](../../../../docs/framework/wcf/samples/known-types.md) 範例。</span><span class="sxs-lookup"><span data-stu-id="2b207-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="2b207-105">一般來說，當您在用戶端與服務之間傳送參數並傳回值時，兩邊的端點都會共用要傳送之資料的所有資料合約。</span><span class="sxs-lookup"><span data-stu-id="2b207-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="2b207-106">但是，這種現象在下列情況中不會出現：</span><span class="sxs-lookup"><span data-stu-id="2b207-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="2b207-107">傳送的資料合約是由預期的資料合約衍生而來。</span><span class="sxs-lookup"><span data-stu-id="2b207-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="2b207-108">如需詳細資訊，請參閱中的繼承的小節[資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md))。</span><span class="sxs-lookup"><span data-stu-id="2b207-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="2b207-109">在此情況下，所傳送資料的資料合約與接收的端點所預期的資料合約不會一樣。</span><span class="sxs-lookup"><span data-stu-id="2b207-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="2b207-110">要傳送的資訊宣告型別是一種介面，而不是類別、結構或列舉。</span><span class="sxs-lookup"><span data-stu-id="2b207-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="2b207-111">因此，您無法預先得知實際傳送了哪種可實作介面的型別，也因此接收的端點無法預先判斷已傳送資料的資料合約。</span><span class="sxs-lookup"><span data-stu-id="2b207-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="2b207-112">要傳送的資訊宣告型別為 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="2b207-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="2b207-113">由於每種型別都繼承自 <xref:System.Object>，而且您無法預先得知實際傳送的型別，因此接收的端點無法預先判斷已傳送資料的資料合約。</span><span class="sxs-lookup"><span data-stu-id="2b207-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="2b207-114">這是特殊案例的第一個項目：每個資料合約衍生自預設值，會針對產生的空白資料合約<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="2b207-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="2b207-115">某些類型，其中包含.NET Framework 型別，有上述三種類別中的成員。</span><span class="sxs-lookup"><span data-stu-id="2b207-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="2b207-116">例如， <xref:System.Collections.Hashtable> 會透過 <xref:System.Object> 將實際物件儲存到雜湊資料表中。</span><span class="sxs-lookup"><span data-stu-id="2b207-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="2b207-117">在序列化這些型別時，接收的一方無法預先判斷這些成員的資料合約。</span><span class="sxs-lookup"><span data-stu-id="2b207-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="2b207-118">KnownTypeAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="2b207-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="2b207-119">當資料抵達接收的結束點時，WCF 執行階段會嘗試將資料還原序列化的 common language runtime (CLR) 類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b207-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="2b207-120">還原系列化作業所產生的型別，首先會經由檢查傳入訊息來判斷訊息內容所符合的資料合約來加以選定。</span><span class="sxs-lookup"><span data-stu-id="2b207-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="2b207-121">接著，還原序列化引擎會嘗試尋找可實作資料合約 (相容於訊息內容) 的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="2b207-122">在此處理序中，我們會將還原序列化引擎所允許的候選型別集合稱為還原序列化程式的「已知型別」集合。</span><span class="sxs-lookup"><span data-stu-id="2b207-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="2b207-123">讓還原序列化引擎識別型別的一種方式，就是使用 <xref:System.Runtime.Serialization.KnownTypeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="2b207-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="2b207-124">屬性無法套用至個別資料成員，只能套用至整個資料合約型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="2b207-125">屬性會套用至可以是類別或結構的「 *外部型別* 」(Outer Type)。</span><span class="sxs-lookup"><span data-stu-id="2b207-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="2b207-126">在屬性最基本的用途當中，套用屬性會將型別指定為「已知型別」。</span><span class="sxs-lookup"><span data-stu-id="2b207-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="2b207-127">這樣一來，每當外部型別的物件或是透過其成員參照的任何物件進行還原序列化，已知型別就會變成已知型別集合的一部分。</span><span class="sxs-lookup"><span data-stu-id="2b207-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="2b207-128">超過一個以上的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性可以套用至相同型別中。</span><span class="sxs-lookup"><span data-stu-id="2b207-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="2b207-129">已知型別與基本型別</span><span class="sxs-lookup"><span data-stu-id="2b207-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="2b207-130">基本型別，以及被視為基本型別的特性型別 (例如， <xref:System.DateTime> 和 <xref:System.Xml.XmlElement>) 將一律具有「已知」狀態，而且一律不需要透過此機制來新增。</span><span class="sxs-lookup"><span data-stu-id="2b207-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="2b207-131">但是，您需要明確地新增基本型別陣列。</span><span class="sxs-lookup"><span data-stu-id="2b207-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="2b207-132">大部分的集合都會被視為與陣列相等</span><span class="sxs-lookup"><span data-stu-id="2b207-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="2b207-133">(非泛型集合將被視為與 <xref:System.Object>陣列相等)。</span><span class="sxs-lookup"><span data-stu-id="2b207-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="2b207-134">如需使用基本型別、基本型別陣列，與基本型別集合的範例，請參閱範例 4。</span><span class="sxs-lookup"><span data-stu-id="2b207-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b207-135">與其他基本型別不同的是， <xref:System.DateTimeOffset> 結構預設並不是已知型別，所以必須手動新增至已知型別清單中。</span><span class="sxs-lookup"><span data-stu-id="2b207-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2b207-136">範例</span><span class="sxs-lookup"><span data-stu-id="2b207-136">Examples</span></span>  
 <span data-ttu-id="2b207-137">下列範例說明使用中的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 類別。</span><span class="sxs-lookup"><span data-stu-id="2b207-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="2b207-138">範例 1</span><span class="sxs-lookup"><span data-stu-id="2b207-138">Example 1</span></span>  
 <span data-ttu-id="2b207-139">具有繼承關係的類別共有三個。</span><span class="sxs-lookup"><span data-stu-id="2b207-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="2b207-140">如果 `CompanyLogo` 成員已設為 `ShapeOfLogo` 或 `CircleType` 物件，由於還原序列化引擎無法識別任何具有資料合約名稱 "Circle" 或 "Triangle" 的型別，您將可以序列化下列 `TriangleType` 類別，但是無法加以還原序列化。</span><span class="sxs-lookup"><span data-stu-id="2b207-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="2b207-141">下列程式碼說明如何正確撰寫 `CompanyLogo` 型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="2b207-142">每次在還原序列化外部型別 `CompanyLogo2` 時，還原序列化引擎能夠識別 `CircleType` 和 `TriangleType` ，因此能夠為 "Circle" 和 "Triangle" 資料找尋相符的型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="2b207-143">範例 2</span><span class="sxs-lookup"><span data-stu-id="2b207-143">Example 2</span></span>  
 <span data-ttu-id="2b207-144">在下列範例中，即使 `CustomerTypeA` 和 `CustomerTypeB` 同時具有 `Customer` 資料合約，每當還原序列化 `CustomerTypeB` 時，還是會建立 `PurchaseOrder` 執行個體，因為還原序列化引擎只能識別 `CustomerTypeB` 。</span><span class="sxs-lookup"><span data-stu-id="2b207-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="2b207-145">範例 3</span><span class="sxs-lookup"><span data-stu-id="2b207-145">Example 3</span></span>  
 <span data-ttu-id="2b207-146">在下列範例中， <xref:System.Collections.Hashtable> 會將其內容當成 <xref:System.Object>儲存在內部。</span><span class="sxs-lookup"><span data-stu-id="2b207-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="2b207-147">為了成功還原序列化雜湊資料表，還原序列化引擎必須能夠識別可在該處發生的可能型別集合。</span><span class="sxs-lookup"><span data-stu-id="2b207-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="2b207-148">在此情況下，我們預先知道只有 `Book` 和 `Magazine` 物件會儲存在 `Catalog`中，因此會透過 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性來加以新增。</span><span class="sxs-lookup"><span data-stu-id="2b207-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="2b207-149">範例 4</span><span class="sxs-lookup"><span data-stu-id="2b207-149">Example 4</span></span>  
 <span data-ttu-id="2b207-150">在下列範例中，資料合約會儲存數字與用來執行數字的運算式。</span><span class="sxs-lookup"><span data-stu-id="2b207-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="2b207-151">`Numbers` 資料成員可以是整數、整數陣列，或是包含整數的 <xref:System.Collections.Generic.List%601> 。</span><span class="sxs-lookup"><span data-stu-id="2b207-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2b207-152">如果使用 SVCUTIL.EXE 來產生 WCF Proxy，這將只能在用戶端上運作。</span><span class="sxs-lookup"><span data-stu-id="2b207-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="2b207-153">SVCUTIL.EXE 會從服務擷取中繼資料，包括所有已知的型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="2b207-154">如果沒有這項資訊，用戶端將無法還原序列化型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="2b207-155">下列為應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="2b207-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="2b207-156">已知型別、繼承，與介面</span><span class="sxs-lookup"><span data-stu-id="2b207-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="2b207-157">當已知型別透過 `KnownTypeAttribute` 屬性關聯至特定型別時，已知型別同時已經和該型別的所有衍生型別產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2b207-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="2b207-158">例如，請參閱下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="2b207-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="2b207-159">`DoubleDrawing` 類別不會要求 `KnownTypeAttribute` 屬性使用 `Square` 欄位中的 `Circle` 和 `AdditionalShape` ，因為基底類別 (`Drawing`) 已經套用了這些屬性。</span><span class="sxs-lookup"><span data-stu-id="2b207-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="2b207-160">已知型別只可和類別與結構，而不能與介面產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2b207-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="2b207-161">使用開放式泛型方法的已知型別</span><span class="sxs-lookup"><span data-stu-id="2b207-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="2b207-162">您可能需要將泛型型別新增為已知型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="2b207-163">但是，開放式泛型型別無法當成 `KnownTypeAttribute` 屬性的參數來傳送。</span><span class="sxs-lookup"><span data-stu-id="2b207-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="2b207-164">使用的替代機制，即可解決此問題：撰寫一個方法，傳回一份要加入至已知型別集合的型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="2b207-165">接著，因為某些限制因素，可將方法名稱指定為 `KnownTypeAttribute` 屬性的字串引數。</span><span class="sxs-lookup"><span data-stu-id="2b207-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="2b207-166">方法必須存在於套用 `KnownTypeAttribute` 屬性的型別上、必須是靜態的、絕對不得接受任何參數，而且必須傳回可指派給 <xref:System.Collections.IEnumerable> 之 <xref:System.Type>的物件。</span><span class="sxs-lookup"><span data-stu-id="2b207-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="2b207-167">您無法將 `KnownTypeAttribute` 屬性與方法名稱結合，也無法將 `KnownTypeAttribute` 屬性與相同型別上的實際型別結合。</span><span class="sxs-lookup"><span data-stu-id="2b207-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="2b207-168">此外，您無法將一個以上包含方法名稱的 `KnownTypeAttribute` 套用至相同型別中。</span><span class="sxs-lookup"><span data-stu-id="2b207-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="2b207-169">請參閱下列類別。</span><span class="sxs-lookup"><span data-stu-id="2b207-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="2b207-170">`theDrawing` 欄位包含泛型類別 `ColorDrawing` 和泛型類別 `BlackAndWhiteDrawing`的執行個體，兩者都繼承自泛型類別 `Drawing`。</span><span class="sxs-lookup"><span data-stu-id="2b207-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="2b207-171">一般來說，兩者必須同時新增至已知型別中，但是下列不是有效的屬性語法。</span><span class="sxs-lookup"><span data-stu-id="2b207-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="2b207-172">因此，您必須建立方法來傳回這些型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="2b207-173">下列程式碼將接著說明撰寫此型別的正確方式。</span><span class="sxs-lookup"><span data-stu-id="2b207-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="2b207-174">新增已知型別的其他方式</span><span class="sxs-lookup"><span data-stu-id="2b207-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="2b207-175">另外，您可以透過組態檔來新增已知型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="2b207-176">當您不能控制需要已知型別進行適當還原序列化，例如當使用協力廠商型別程式庫與 Windows Communication Foundation (WCF) 的型別時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="2b207-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="2b207-177">下列組態檔示範如何在組態檔中指定已知的型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="2b207-178">在先前的組態檔中，會宣告稱為 `MyCompany.Library.Shape` 的資料合約型別，而讓 `MyCompany.Library.Circle` 做為已知的型別。</span><span class="sxs-lookup"><span data-stu-id="2b207-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b207-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b207-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="2b207-180">已知類型</span><span class="sxs-lookup"><span data-stu-id="2b207-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)
- [<span data-ttu-id="2b207-181">資料合約等價</span><span class="sxs-lookup"><span data-stu-id="2b207-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="2b207-182">設計服務合約</span><span class="sxs-lookup"><span data-stu-id="2b207-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
