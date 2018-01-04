---
title: "版本相容序列化"
ms.date: 08/08/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 46a6ccde7c978fe18737c6ae8733dd2e1e1ec858
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="d1645-102">版本相容序列化</span><span class="sxs-lookup"><span data-stu-id="d1645-102">Version tolerant serialization</span></span>
<span data-ttu-id="d1645-103">在 .NET Framework 1.0 和 1.1 版中，建立可以從應用程式的某個版本，延續到下一個版本使用的可序列化型別，有其問題存在。</span><span class="sxs-lookup"><span data-stu-id="d1645-103">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="d1645-104">如果型別因加入其他欄位而變更，將會發生下列問題：</span><span class="sxs-lookup"><span data-stu-id="d1645-104">If a type was modified by adding extra fields, the following problems would occur:</span></span>  
  
-   <span data-ttu-id="d1645-105">當要求將新版的舊型別還原序列化時，舊版應用程式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1645-105">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>  
  
-   <span data-ttu-id="d1645-106">新版的應用程式在還原序列化資料遺失的舊版型別時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1645-106">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>  
  
 <span data-ttu-id="d1645-107">版本相容序列化 (VTS) 為 .NET Framework 2.0 引進的一組功能，讓變更序列化型別隨著時間更加簡單。</span><span class="sxs-lookup"><span data-stu-id="d1645-107">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="d1645-108">具體地說，VTS 功能是為套用 <xref:System.SerializableAttribute> 屬性的類別啟用，包括泛型型別。</span><span class="sxs-lookup"><span data-stu-id="d1645-108">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="d1645-109">VTS 可在不破壞與其他版本之型別相容性的情況下，將新欄位加入那些類別。</span><span class="sxs-lookup"><span data-stu-id="d1645-109">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="d1645-110">如需可用的範例應用程式，請參閱[版本相容序列化技術範例](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="d1645-110">For a working sample application, see [Version Tolerant Serialization Technology Sample](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span></span>  
  
 <span data-ttu-id="d1645-111">使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>時，會啟用 VTS 功能。</span><span class="sxs-lookup"><span data-stu-id="d1645-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="d1645-112">除此之外，使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>時，除了沒有直接關聯的資料容錯功能外，其他所有功能都會啟用。</span><span class="sxs-lookup"><span data-stu-id="d1645-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="d1645-113">如需使用這些類別進行序列化的詳細資訊，請參閱[二進位序列化](binary-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="d1645-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="d1645-114">功能清單</span><span class="sxs-lookup"><span data-stu-id="d1645-114">Feature list</span></span>  
 <span data-ttu-id="d1645-115">功能集包括以下內容：</span><span class="sxs-lookup"><span data-stu-id="d1645-115">The set of features includes the following:</span></span>  
  
-   <span data-ttu-id="d1645-116">沒有直接關聯的容錯或未預期的資料。</span><span class="sxs-lookup"><span data-stu-id="d1645-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="d1645-117">這樣可以讓新版的型別傳送資料給舊版的型別。</span><span class="sxs-lookup"><span data-stu-id="d1645-117">This enables newer versions of the type to send data to older versions.</span></span>  
  
-   <span data-ttu-id="d1645-118">遺失的選用資料容錯。</span><span class="sxs-lookup"><span data-stu-id="d1645-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="d1645-119">這樣可以讓舊版傳送資料給新版。</span><span class="sxs-lookup"><span data-stu-id="d1645-119">This enables older versions to send data to newer versions.</span></span>  
  
-   <span data-ttu-id="d1645-120">序列化回呼。</span><span class="sxs-lookup"><span data-stu-id="d1645-120">Serialization callbacks.</span></span> <span data-ttu-id="d1645-121">這樣能在資料遺失時，啟用智慧性預設值設定。</span><span class="sxs-lookup"><span data-stu-id="d1645-121">This enables intelligent default value setting in cases where data is missing.</span></span>  
  
 <span data-ttu-id="d1645-122">除此之外，還有在新增了新選項欄位時宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="d1645-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="d1645-123">這是 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> 屬性 (attribute) 的 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="d1645-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>  
  
 <span data-ttu-id="d1645-124">這些功能將在稍後詳述。</span><span class="sxs-lookup"><span data-stu-id="d1645-124">These features are discussed in greater detail below.</span></span>  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="d1645-125">沒有直接關聯的容錯或未預期的資料</span><span class="sxs-lookup"><span data-stu-id="d1645-125">Tolerance of extraneous or unexpected data</span></span>  
 <span data-ttu-id="d1645-126">在過去，還原序列化期間，任何沒有直接關聯或未預期的資料會導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1645-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="d1645-127">在同樣的狀況下使用 VTS，任何沒有直接關聯或未預期的資料都會略過，而不會導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1645-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="d1645-128">這樣可讓應用程式使用較新版的型別 (即包含較多欄位的版本) 以傳送資訊給預期相同之型別為較舊版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1645-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>  
  
 <span data-ttu-id="d1645-129">在以下的範例中，當較舊的應用程式還原序列化較新版本時，`CountryField` 類別 2.0 版的 `Address` 所包含的額外資料將略過。</span><span class="sxs-lookup"><span data-stu-id="d1645-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>  
  
```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  
  
## <a name="tolerance-of-missing-data"></a><span data-ttu-id="d1645-130">遺失資料的容錯</span><span class="sxs-lookup"><span data-stu-id="d1645-130">Tolerance of missing data</span></span>  
 <span data-ttu-id="d1645-131">將 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性套用至欄位，能將欄位標示為選擇性。</span><span class="sxs-lookup"><span data-stu-id="d1645-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="d1645-132">在還原序列化期間，若遺失了選項資料，則序列化引擎會忽略遺失的資料，不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1645-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="d1645-133">如此，預期較舊版之型別的應用程式可將資料傳送至預期較新版之相同型別的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1645-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>  
  
 <span data-ttu-id="d1645-134">下列範例顯示標示為選擇性之具有 `Address` 欄位的 `CountryField` 類別 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="d1645-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="d1645-135">若較舊的應用程式將第 1 版傳送至預期 2.0 版之較新的應用程式，則會略過遺失的資料。</span><span class="sxs-lookup"><span data-stu-id="d1645-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
  
    [OptionalField]  
    public string CountryField;  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
  
    <OptionalField> _  
    Public CountryField As String  
End Class  
```  
  
## <a name="serialization-callbacks"></a><span data-ttu-id="d1645-136">序列化回呼</span><span class="sxs-lookup"><span data-stu-id="d1645-136">Serialization callbacks</span></span>  
 <span data-ttu-id="d1645-137">序列化回呼是在四個點上對序列化/還原序列化程序提供攔截的機制。</span><span class="sxs-lookup"><span data-stu-id="d1645-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>  
  
|<span data-ttu-id="d1645-138">屬性</span><span class="sxs-lookup"><span data-stu-id="d1645-138">Attribute</span></span>|<span data-ttu-id="d1645-139">呼叫關聯方法的時機</span><span class="sxs-lookup"><span data-stu-id="d1645-139">When the Associated Method is Called</span></span>|<span data-ttu-id="d1645-140">一般用法</span><span class="sxs-lookup"><span data-stu-id="d1645-140">Typical Use</span></span>|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="d1645-141">還原序列化之前。*</span><span class="sxs-lookup"><span data-stu-id="d1645-141">Before deserialization.*</span></span>|<span data-ttu-id="d1645-142">對選擇性欄位初始化預設值。</span><span class="sxs-lookup"><span data-stu-id="d1645-142">Initialize default values for optional fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="d1645-143">還原序列化之後。</span><span class="sxs-lookup"><span data-stu-id="d1645-143">After deserialization.</span></span>|<span data-ttu-id="d1645-144">根據其他欄位的內容修正選擇性欄位值。</span><span class="sxs-lookup"><span data-stu-id="d1645-144">Fix optional field values based on contents of other fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="d1645-145">序列化之前。</span><span class="sxs-lookup"><span data-stu-id="d1645-145">Before serialization.</span></span>|<span data-ttu-id="d1645-146">準備序列化。</span><span class="sxs-lookup"><span data-stu-id="d1645-146">Prepare for serialization.</span></span> <span data-ttu-id="d1645-147">例如，建立選擇性資料架構。</span><span class="sxs-lookup"><span data-stu-id="d1645-147">For example, create optional data structures.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="d1645-148">序列化之後。</span><span class="sxs-lookup"><span data-stu-id="d1645-148">After serialization.</span></span>|<span data-ttu-id="d1645-149">記錄序列化事件。</span><span class="sxs-lookup"><span data-stu-id="d1645-149">Log serialization events.</span></span>|  
  
 <span data-ttu-id="d1645-150">\* 此回呼是在還原序列化建構函式之前叫用 (若有建構函式的話)。</span><span class="sxs-lookup"><span data-stu-id="d1645-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>  
  
### <a name="using-callbacks"></a><span data-ttu-id="d1645-151">使用回呼</span><span class="sxs-lookup"><span data-stu-id="d1645-151">Using callbacks</span></span>  
 <span data-ttu-id="d1645-152">若要使用回呼，將適當屬性套用至接受 <xref:System.Runtime.Serialization.StreamingContext> 參數的方法。</span><span class="sxs-lookup"><span data-stu-id="d1645-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="d1645-153">每個類別只有一個方法可以使用每個這些屬性來標示。</span><span class="sxs-lookup"><span data-stu-id="d1645-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="d1645-154">例如：</span><span class="sxs-lookup"><span data-stu-id="d1645-154">For example:</span></span>  
  
```csharp  
[OnDeserializing]  
private void SetCountryRegionDefault(StreamingContext sc)  
{  
    CountryField = "Japan";  
}  
```  
  
```vb  
<OnDeserializing>  
Private Sub SetCountryRegionDefault(StreamingContext sc)  
    CountryField = "Japan";  
End Sub  
```  
  
 <span data-ttu-id="d1645-155">這些方法的用途是版本控制。</span><span class="sxs-lookup"><span data-stu-id="d1645-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="d1645-156">在還原序列化期間，若欄位的資料遺失，則選擇性欄位或許無法正確初始化。</span><span class="sxs-lookup"><span data-stu-id="d1645-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="d1645-157">建立指派正確值的方法，然後將 **OnDeserializingAttribute** 或 **OnDeserializedAttribute** 屬性套用至方法，即可修正此狀況。</span><span class="sxs-lookup"><span data-stu-id="d1645-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>  
  
 <span data-ttu-id="d1645-158">以下範例顯示型別內容中的方法。</span><span class="sxs-lookup"><span data-stu-id="d1645-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="d1645-159">若先前版的應用程式將 `Address` 類別的執行個體傳送至較新版的應用程式，則 `CountryField` 欄位資料將遺失。</span><span class="sxs-lookup"><span data-stu-id="d1645-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="d1645-160">但在還原序列化之後，欄位將設定為預設值 "Japan"。</span><span class="sxs-lookup"><span data-stu-id="d1645-160">But after deserialization, the field will be set to a default value "Japan."</span></span>  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    [OptionalField]  
    public string CountryField;  
  
    [OnDeserializing]  
    private void SetCountryRegionDefault (StreamingContext sc)  
    {  
        CountryField = "Japan";  
    }  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    <OptionalField> _  
    Public CountryField As String  
  
    <OnDeserializing> _  
    Private Sub SetCountryRegionDefault(StreamingContext sc)  
        CountryField = "Japan";  
    End Sub  
End Class  
```  
  
## <a name="the-versionadded-property"></a><span data-ttu-id="d1645-161">VersionAdded 屬性</span><span class="sxs-lookup"><span data-stu-id="d1645-161">The VersionAdded property</span></span>  
 <span data-ttu-id="d1645-162">**OptionalFieldAttribute** 具有 **VersionAdded** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d1645-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="d1645-163">這在 .NET Framework 2.0 版中不使用。</span><span class="sxs-lookup"><span data-stu-id="d1645-163">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="d1645-164">然而，正確設定此屬性以確保類型與未來序列化引擎相容很重要。</span><span class="sxs-lookup"><span data-stu-id="d1645-164">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>  
  
 <span data-ttu-id="d1645-165">屬性會指示指定的欄位已加入哪個版本的型別。</span><span class="sxs-lookup"><span data-stu-id="d1645-165">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="d1645-166">如下列範例所示，每次變更型別時，正好遞增 1 (從 2 開始)：</span><span class="sxs-lookup"><span data-stu-id="d1645-166">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>  
  
```csharp  
// Version 1.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
}  
  
// Version 2.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded = 2)]  
    public string NickName;  
    [OptionalField(VersionAdded = 2)]  
    public DateTime BirthDate;  
}  
  
// Version 3.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded=2)]  
    public string NickName;  
    [OptionalField(VersionAdded=2)]  
    public DateTime BirthDate;  
  
    [OptionalField(VersionAdded=3)]  
    public int Weight;  
}  
```  
  
```vb  
' Version 1.0  
<Serializable> _  
Public Class Person  
    Public FullName  
End Class  
  
' Version 2.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
End Class  
  
' Version 3.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
  
    <OptionalField(VersionAdded := 3)> _  
    Public Weight As Integer  
End Class  
```  
  
## <a name="serializationbinder"></a><span data-ttu-id="d1645-167">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="d1645-167">SerializationBinder</span></span>  
 <span data-ttu-id="d1645-168">某些使用者可能因為伺服器和用戶端上需要不同版本的類別，而需要控制要序列化和還原序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="d1645-168">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="d1645-169"><xref:System.Runtime.Serialization.SerializationBinder> 是抽象類別，用來控制序列化和還原序列化期間使用的實際型別。</span><span class="sxs-lookup"><span data-stu-id="d1645-169"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span>  <span data-ttu-id="d1645-170">若要使用此類別，請從 <xref:System.Runtime.Serialization.SerializationBinder> 衍生一個類別，然後覆寫 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> 和 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d1645-170">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d1645-171">[控制序列化和還原序列化以 SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md)。</span><span class="sxs-lookup"><span data-stu-id="d1645-171"> [Controlling Serialization and Deserialization with SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="d1645-172">最佳作法</span><span class="sxs-lookup"><span data-stu-id="d1645-172">Best practices</span></span>  
 <span data-ttu-id="d1645-173">若要確定版本控制行為適當，修改版本中的型別時，請遵循這些規則：</span><span class="sxs-lookup"><span data-stu-id="d1645-173">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>  
  
-   <span data-ttu-id="d1645-174">絕不移除已序列化的欄位。</span><span class="sxs-lookup"><span data-stu-id="d1645-174">Never remove a serialized field.</span></span>  
  
-   <span data-ttu-id="d1645-175">若屬性在之前的版本未套用至欄位，絕不套用 <xref:System.NonSerializedAttribute> 屬性至欄位。</span><span class="sxs-lookup"><span data-stu-id="d1645-175">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>  
  
-   <span data-ttu-id="d1645-176">絕不變更名稱或序列化欄位的型別。</span><span class="sxs-lookup"><span data-stu-id="d1645-176">Never change the name or the type of a serialized field.</span></span>  
  
-   <span data-ttu-id="d1645-177">新增新的序列化欄位時，請套用 **OptionalFieldAttribute** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d1645-177">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>  
  
-   <span data-ttu-id="d1645-178">自欄位 (在先前版本中為不可序列化的欄位) 移除 **NonSerializedAttribute** 屬性時，請套用 **OptionalFieldAttribute** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d1645-178">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>  
  
-   <span data-ttu-id="d1645-179">對所有選擇性欄位，除非可接受 0 或 **null** 作為預設值，否則使用序列化回呼來設定有意義的預設值。</span><span class="sxs-lookup"><span data-stu-id="d1645-179">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>  
  
 <span data-ttu-id="d1645-180">若要確定型別與未來序列化引擎相容，請遵循下列方針：</span><span class="sxs-lookup"><span data-stu-id="d1645-180">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="d1645-181">一律在 **OptionalFieldAttribute** 屬性 (attribute) 上正確設定 **VersionAdded** 屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="d1645-181">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>  
  
-   <span data-ttu-id="d1645-182">避免分支版本控制。</span><span class="sxs-lookup"><span data-stu-id="d1645-182">Avoid branched versioning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1645-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1645-183">See also</span></span>  
 <xref:System.SerializableAttribute>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 <xref:System.NonSerializedAttribute>  
 [<span data-ttu-id="d1645-184">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="d1645-184">Binary Serialization</span></span>](binary-serialization.md)
