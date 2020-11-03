---
title: 版本相容序列化
description: 瞭解版本容錯序列化，這是一組可讓您更輕鬆地修改可序列化類型的功能。
ms.date: 08/08/2017
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
ms.openlocfilehash: e7c4d6ca4c72390c3e0803502aa9c1a675e02345
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282410"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="93076-103">版本相容序列化</span><span class="sxs-lookup"><span data-stu-id="93076-103">Version tolerant serialization</span></span>

<span data-ttu-id="93076-104">在最早的 .NET Framework 版本中，建立可從某個應用程式版本重複使用到下一個版本的可序列化型別有問題。</span><span class="sxs-lookup"><span data-stu-id="93076-104">In the earliest versions of .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="93076-105">如果型別因加入其他欄位而變更，將會發生下列問題：</span><span class="sxs-lookup"><span data-stu-id="93076-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="93076-106">當要求將新版的舊型別還原序列化時，舊版應用程式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93076-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="93076-107">新版的應用程式在還原序列化資料遺失的舊版型別時，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93076-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="93076-108">版本相容序列化 (VTS) 是一組功能，可讓您更輕鬆地在一段時間內修改可序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="93076-108">Version Tolerant Serialization (VTS) is a set of features that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="93076-109">具體地說，VTS 功能是為套用 <xref:System.SerializableAttribute> 屬性的類別啟用，包括泛型型別。</span><span class="sxs-lookup"><span data-stu-id="93076-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="93076-110">VTS 可在不破壞與其他版本之型別相容性的情況下，將新欄位加入那些類別。</span><span class="sxs-lookup"><span data-stu-id="93076-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="93076-111">如需可用的範例應用程式，請參閱[版本相容序列化技術範例](basic-serialization-technology-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="93076-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md).</span></span>

<span data-ttu-id="93076-112">使用 時，會啟用 VTS 功能。</span><span class="sxs-lookup"><span data-stu-id="93076-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="93076-113">除此之外，使用 時，除了沒有直接關聯的資料容錯功能外，其他所有功能都會啟用。</span><span class="sxs-lookup"><span data-stu-id="93076-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="93076-114">如需使用這些類別進行序列化的詳細資訊，請參閱[二進位序列化](binary-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="93076-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="93076-115">功能清單</span><span class="sxs-lookup"><span data-stu-id="93076-115">Feature list</span></span>

<span data-ttu-id="93076-116">功能集包括以下內容：</span><span class="sxs-lookup"><span data-stu-id="93076-116">The set of features includes the following:</span></span>

- <span data-ttu-id="93076-117">沒有直接關聯的容錯或未預期的資料。</span><span class="sxs-lookup"><span data-stu-id="93076-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="93076-118">這樣可以讓新版的型別傳送資料給舊版的型別。</span><span class="sxs-lookup"><span data-stu-id="93076-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="93076-119">遺失的選用資料容錯。</span><span class="sxs-lookup"><span data-stu-id="93076-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="93076-120">這樣可以讓舊版傳送資料給新版。</span><span class="sxs-lookup"><span data-stu-id="93076-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="93076-121">序列化回呼。</span><span class="sxs-lookup"><span data-stu-id="93076-121">Serialization callbacks.</span></span> <span data-ttu-id="93076-122">這樣能在資料遺失時，啟用智慧性預設值設定。</span><span class="sxs-lookup"><span data-stu-id="93076-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="93076-123">除此之外，還有在新增了新選項欄位時宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="93076-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="93076-124">這是 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> 屬性 (attribute) 的 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="93076-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="93076-125">這些功能將在下列各節中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="93076-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="93076-126">沒有直接關聯的容錯或未預期的資料</span><span class="sxs-lookup"><span data-stu-id="93076-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="93076-127">在過去，還原序列化期間，任何沒有直接關聯或未預期的資料會導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93076-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="93076-128">在同樣的狀況下使用 VTS，任何沒有直接關聯或未預期的資料都會略過，而不會導致擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93076-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="93076-129">這樣可讓應用程式使用較新版的型別 (即包含較多欄位的版本) 以傳送資訊給預期相同之型別為較舊版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="93076-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="93076-130">在以下的範例中，當較舊的應用程式還原序列化較新版本時，`CountryField` 類別 2.0 版的 `Address` 所包含的額外資料將略過。</span><span class="sxs-lookup"><span data-stu-id="93076-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

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

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="93076-131">遺失資料的容錯</span><span class="sxs-lookup"><span data-stu-id="93076-131">Tolerance of missing data</span></span>

<span data-ttu-id="93076-132">將 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性套用至欄位，能將欄位標示為選擇性。</span><span class="sxs-lookup"><span data-stu-id="93076-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="93076-133">在還原序列化期間，若遺失了選項資料，則序列化引擎會忽略遺失的資料，不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93076-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="93076-134">如此，預期較舊版之型別的應用程式可將資料傳送至預期較新版之相同型別的應用程式。</span><span class="sxs-lookup"><span data-stu-id="93076-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="93076-135">下列範例顯示標示為選擇性之具有 `Address` 欄位的 `CountryField` 類別 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="93076-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="93076-136">若較舊的應用程式將第 1 版傳送至預期 2.0 版之較新的應用程式，則會略過遺失的資料。</span><span class="sxs-lookup"><span data-stu-id="93076-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

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
  
### <a name="serialization-callbacks"></a><span data-ttu-id="93076-137">序列化回呼</span><span class="sxs-lookup"><span data-stu-id="93076-137">Serialization callbacks</span></span>

<span data-ttu-id="93076-138">序列化回呼是在四個點上對序列化/還原序列化程序提供攔截的機制。</span><span class="sxs-lookup"><span data-stu-id="93076-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="93076-139">屬性</span><span class="sxs-lookup"><span data-stu-id="93076-139">Attribute</span></span>|<span data-ttu-id="93076-140">呼叫關聯方法的時機</span><span class="sxs-lookup"><span data-stu-id="93076-140">When the Associated Method is Called</span></span>|<span data-ttu-id="93076-141">一般用法</span><span class="sxs-lookup"><span data-stu-id="93076-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="93076-142">還原序列化之前。\*</span><span class="sxs-lookup"><span data-stu-id="93076-142">Before deserialization.\*</span></span>|<span data-ttu-id="93076-143">對選擇性欄位初始化預設值。</span><span class="sxs-lookup"><span data-stu-id="93076-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="93076-144">還原序列化之後。</span><span class="sxs-lookup"><span data-stu-id="93076-144">After deserialization.</span></span>|<span data-ttu-id="93076-145">根據其他欄位的內容修正選擇性欄位值。</span><span class="sxs-lookup"><span data-stu-id="93076-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="93076-146">序列化之前。</span><span class="sxs-lookup"><span data-stu-id="93076-146">Before serialization.</span></span>|<span data-ttu-id="93076-147">準備序列化。</span><span class="sxs-lookup"><span data-stu-id="93076-147">Prepare for serialization.</span></span> <span data-ttu-id="93076-148">例如，建立選擇性資料架構。</span><span class="sxs-lookup"><span data-stu-id="93076-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="93076-149">序列化之後。</span><span class="sxs-lookup"><span data-stu-id="93076-149">After serialization.</span></span>|<span data-ttu-id="93076-150">記錄序列化事件。</span><span class="sxs-lookup"><span data-stu-id="93076-150">Log serialization events.</span></span>|

 <span data-ttu-id="93076-151">\* 此回呼是在還原序列化建構函式之前叫用 (若有建構函式的話)。</span><span class="sxs-lookup"><span data-stu-id="93076-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="93076-152">使用回呼</span><span class="sxs-lookup"><span data-stu-id="93076-152">Using callbacks</span></span>

<span data-ttu-id="93076-153">若要使用回呼，將適當屬性套用至接受 <xref:System.Runtime.Serialization.StreamingContext> 參數的方法。</span><span class="sxs-lookup"><span data-stu-id="93076-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="93076-154">每個類別只有一個方法可以使用每個這些屬性來標示。</span><span class="sxs-lookup"><span data-stu-id="93076-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="93076-155">例如：</span><span class="sxs-lookup"><span data-stu-id="93076-155">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="93076-156">這些方法的用途是版本控制。</span><span class="sxs-lookup"><span data-stu-id="93076-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="93076-157">在還原序列化期間，若欄位的資料遺失，則選擇性欄位或許無法正確初始化。</span><span class="sxs-lookup"><span data-stu-id="93076-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="93076-158">建立指派正確值的方法，然後將 **OnDeserializingAttribute** 或 **OnDeserializedAttribute** 屬性套用至方法，即可修正此狀況。</span><span class="sxs-lookup"><span data-stu-id="93076-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="93076-159">以下範例顯示型別內容中的方法。</span><span class="sxs-lookup"><span data-stu-id="93076-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="93076-160">若先前版的應用程式將 `Address` 類別的執行個體傳送至較新版的應用程式，則 `CountryField` 欄位資料將遺失。</span><span class="sxs-lookup"><span data-stu-id="93076-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="93076-161">但在還原序列化之後，欄位將會設定為預設值 "日本"。</span><span class="sxs-lookup"><span data-stu-id="93076-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
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
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="93076-162">VersionAdded 屬性</span><span class="sxs-lookup"><span data-stu-id="93076-162">The VersionAdded property</span></span>

<span data-ttu-id="93076-163">**OptionalFieldAttribute** 具有 **VersionAdded** 屬性。</span><span class="sxs-lookup"><span data-stu-id="93076-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="93076-164">屬性會指示指定的欄位已加入哪個版本的型別。</span><span class="sxs-lookup"><span data-stu-id="93076-164">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="93076-165">如下列範例所示，每次變更型別時，正好遞增 1 (從 2 開始)：</span><span class="sxs-lookup"><span data-stu-id="93076-165">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

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

## <a name="serializationbinder"></a><span data-ttu-id="93076-166">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="93076-166">SerializationBinder</span></span>

<span data-ttu-id="93076-167">某些使用者可能因為伺服器和用戶端上需要不同版本的類別，而需要控制要序列化和還原序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="93076-167">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="93076-168"><xref:System.Runtime.Serialization.SerializationBinder> 是抽象類別，用來控制序列化和還原序列化期間使用的實際型別。</span><span class="sxs-lookup"><span data-stu-id="93076-168"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="93076-169">若要使用此類別，請從 <xref:System.Runtime.Serialization.SerializationBinder> 衍生一個類別，然後覆寫 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> 和 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="93076-169">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="93076-170">如需詳細資訊，請參閱 [使用 SerializationBinder 控制序列化和還原序列化](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md)。</span><span class="sxs-lookup"><span data-stu-id="93076-170">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="93076-171">最佳作法</span><span class="sxs-lookup"><span data-stu-id="93076-171">Best practices</span></span>

<span data-ttu-id="93076-172">若要確定版本控制行為適當，修改版本中的型別時，請遵循這些規則：</span><span class="sxs-lookup"><span data-stu-id="93076-172">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="93076-173">絕不移除已序列化的欄位。</span><span class="sxs-lookup"><span data-stu-id="93076-173">Never remove a serialized field.</span></span>
- <span data-ttu-id="93076-174">若屬性在之前的版本未套用至欄位，絕不套用 <xref:System.NonSerializedAttribute> 屬性至欄位。</span><span class="sxs-lookup"><span data-stu-id="93076-174">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="93076-175">絕不變更名稱或序列化欄位的型別。</span><span class="sxs-lookup"><span data-stu-id="93076-175">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="93076-176">新增新的序列化欄位時，請套用 **OptionalFieldAttribute** 屬性。</span><span class="sxs-lookup"><span data-stu-id="93076-176">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="93076-177">自欄位 (在先前版本中為不可序列化的欄位) 移除 **NonSerializedAttribute** 屬性時，請套用 **OptionalFieldAttribute** 屬性。</span><span class="sxs-lookup"><span data-stu-id="93076-177">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="93076-178">對所有選擇性欄位，除非可接受 0 或 **null** 作為預設值，否則使用序列化回呼來設定有意義的預設值。</span><span class="sxs-lookup"><span data-stu-id="93076-178">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="93076-179">若要確定型別與未來序列化引擎相容，請遵循下列方針：</span><span class="sxs-lookup"><span data-stu-id="93076-179">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="93076-180">一律在 **OptionalFieldAttribute** 屬性 (attribute) 上正確設定 **VersionAdded** 屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="93076-180">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="93076-181">避免分支版本控制。</span><span class="sxs-lookup"><span data-stu-id="93076-181">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="93076-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93076-182">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="93076-183">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="93076-183">Binary Serialization</span></span>](binary-serialization.md)
