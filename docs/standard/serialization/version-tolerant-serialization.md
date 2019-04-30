---
title: 版本相容序列化
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
ms.openlocfilehash: c899cfe1015a25adc25fc28ee84d0a37a397defe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028248"
---
# <a name="version-tolerant-serialization"></a>版本相容序列化
在 .NET Framework 1.0 和 1.1 版中，建立可以從應用程式的某個版本，延續到下一個版本使用的可序列化型別，有其問題存在。 如果型別因加入其他欄位而變更，將會發生下列問題：  
  
- 當要求將新版的舊型別還原序列化時，舊版應用程式會擲回例外狀況。  
  
- 新版的應用程式在還原序列化資料遺失的舊版型別時，會擲回例外狀況。  
  
 版本相容序列化 (VTS) 為 .NET Framework 2.0 引進的一組功能，讓變更序列化型別隨著時間更加簡單。 具體地說，VTS 功能是為套用 <xref:System.SerializableAttribute> 屬性的類別啟用，包括泛型型別。 VTS 可在不破壞與其他版本之型別相容性的情況下，將新欄位加入那些類別。 如需可用的範例應用程式，請參閱[版本相容序列化技術範例](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md)。  
  
 使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>時，會啟用 VTS 功能。 除此之外，使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>時，除了沒有直接關聯的資料容錯功能外，其他所有功能都會啟用。 如需使用這些類別進行序列化的詳細資訊，請參閱[二進位序列化](binary-serialization.md)。  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>功能清單  
 功能集包括以下內容：  
  
- 沒有直接關聯的容錯或未預期的資料。 這樣可以讓新版的型別傳送資料給舊版的型別。  
  
- 遺失的選用資料容錯。 這樣可以讓舊版傳送資料給新版。  
  
- 序列化回呼。 這樣能在資料遺失時，啟用智慧性預設值設定。  
  
 除此之外，還有在新增了新選項欄位時宣告的功能。 這是 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> 屬性 (attribute) 的 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性 (property)。  
  
 這些功能將在稍後詳述。  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a>沒有直接關聯的容錯或未預期的資料  
 在過去，還原序列化期間，任何沒有直接關聯或未預期的資料會導致擲回例外狀況。 在同樣的狀況下使用 VTS，任何沒有直接關聯或未預期的資料都會略過，而不會導致擲回例外狀況。 這樣可讓應用程式使用較新版的型別 (即包含較多欄位的版本) 以傳送資訊給預期相同之型別為較舊版的應用程式。  
  
 在以下的範例中，當較舊的應用程式還原序列化較新版本時，`CountryField` 類別 2.0 版的 `Address` 所包含的額外資料將略過。  
  
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
  
## <a name="tolerance-of-missing-data"></a>遺失資料的容錯  
 將 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性套用至欄位，能將欄位標示為選擇性。 在還原序列化期間，若遺失了選項資料，則序列化引擎會忽略遺失的資料，不會擲回例外狀況。 如此，預期較舊版之型別的應用程式可將資料傳送至預期較新版之相同型別的應用程式。  
  
 下列範例顯示標示為選擇性之具有 `Address` 欄位的 `CountryField` 類別 2.0 版。 若較舊的應用程式將第 1 版傳送至預期 2.0 版之較新的應用程式，則會略過遺失的資料。  
  
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
  
## <a name="serialization-callbacks"></a>序列化回呼  
 序列化回呼是在四個點上對序列化/還原序列化程序提供攔截的機制。  
  
|屬性|呼叫關聯方法的時機|一般用法|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|還原序列化之前。*|對選擇性欄位初始化預設值。|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|還原序列化之後。|根據其他欄位的內容修正選擇性欄位值。|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|序列化之前。|準備序列化。 例如，建立選擇性資料架構。|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|序列化之後。|記錄序列化事件。|  
  
 \* 此回呼是在還原序列化建構函式之前叫用 (若有建構函式的話)。  
  
### <a name="using-callbacks"></a>使用回呼  
 若要使用回呼，將適當屬性套用至接受 <xref:System.Runtime.Serialization.StreamingContext> 參數的方法。 每個類別只有一個方法可以使用每個這些屬性來標示。 例如:   
  
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
  
 這些方法的用途是版本控制。 在還原序列化期間，若欄位的資料遺失，則選擇性欄位或許無法正確初始化。 建立指派正確值的方法，然後將 **OnDeserializingAttribute** 或 **OnDeserializedAttribute** 屬性套用至方法，即可修正此狀況。  
  
 以下範例顯示型別內容中的方法。 若先前版的應用程式將 `Address` 類別的執行個體傳送至較新版的應用程式，則 `CountryField` 欄位資料將遺失。 但在還原序列化之後，欄位將設定為預設值 "Japan"。  
  
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
  
## <a name="the-versionadded-property"></a>VersionAdded 屬性  
 **OptionalFieldAttribute** 具有 **VersionAdded** 屬性。 這在 .NET Framework 2.0 版中不使用。 然而，正確設定此屬性以確保類型與未來序列化引擎相容很重要。  
  
 屬性會指示指定的欄位已加入哪個版本的型別。 如下列範例所示，每次變更型別時，正好遞增 1 (從 2 開始)：  
  
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
  
## <a name="serializationbinder"></a>SerializationBinder  
 某些使用者可能因為伺服器和用戶端上需要不同版本的類別，而需要控制要序列化和還原序列化的類別。 <xref:System.Runtime.Serialization.SerializationBinder> 是抽象類別，用來控制序列化和還原序列化期間使用的實際型別。  若要使用此類別，請從 <xref:System.Runtime.Serialization.SerializationBinder> 衍生一個類別，然後覆寫 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> 和 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> 方法。 如需詳細資訊，請參閱 <<c0> [ 控制序列化和還原序列化以 SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md)。  
  
## <a name="best-practices"></a>最佳作法  
 若要確定版本控制行為適當，修改版本中的型別時，請遵循這些規則：  
  
- 絕不移除已序列化的欄位。  
  
- 若屬性在之前的版本未套用至欄位，絕不套用 <xref:System.NonSerializedAttribute> 屬性至欄位。  
  
- 絕不變更名稱或序列化欄位的型別。  
  
- 新增新的序列化欄位時，請套用 **OptionalFieldAttribute** 屬性。  
  
- 自欄位 (在先前版本中為不可序列化的欄位) 移除 **NonSerializedAttribute** 屬性時，請套用 **OptionalFieldAttribute** 屬性。  
  
- 對所有選擇性欄位，除非可接受 0 或 **null** 作為預設值，否則使用序列化回呼來設定有意義的預設值。  
  
 若要確定型別與未來序列化引擎相容，請遵循下列方針：  
  
- 一律在 **OptionalFieldAttribute** 屬性 (attribute) 上正確設定 **VersionAdded** 屬性 (property)。  
  
- 避免分支版本控制。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [二進位序列化](binary-serialization.md)
