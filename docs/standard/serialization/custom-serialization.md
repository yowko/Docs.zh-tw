---
title: 自訂序列化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 6151bf670a455d4c9862e80fd06314e4e1621080
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881911"
---
# <a name="custom-serialization"></a>自訂序列化
自訂序列化是控制型別序列化與還原序列化的程序。 控制序列化就可確保序列化相容性，也就是在類型版本之間進行序列化與還原序列化的作業，而不違反類型的核心功能性。 例如，在第一版的型別中，可能只有兩個欄位。 在型別的下一版中，加入了更多的欄位。 然而第二版的應用程式必須對這兩種型別進行序列化及還原序列化。 下列章節會說明控制序列化的方法。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  在 .NET Framework 4.0 之前的版本中，部分信任組件中自訂使用者資料的序列化是使用 GetObjectData 所完成。 從 4.0 版開始，該方法會標記 <xref:System.Security.SecurityCriticalAttribute> 屬性，因此便無法在部分信任組件中執行。 若要解決此狀況，請實作 <xref:System.Runtime.Serialization.ISafeSerializationData> 介面。  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>序列化期間及序列化之後執行自訂方法  
 最佳做法與最簡單方式 (引入至 .NET Framework 2.0 版) 是套用下列屬性至用來在序列化期間及之後修正資料的方法：  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 這些屬性允許型別參與序列化及還原序列化程序的任何一個或所有四個階段。 屬性指定應在每個階段叫用的型別方法。 這些方法並不存取序列化資料流，而是允許您在序列化前後或還原序列化前後變更物件。 屬性可套用在所有層級的型別繼承階層，且會呼叫從基本到最具衍生性之階層中的每個方法。 此機制避開實作 <xref:System.Runtime.Serialization.ISerializable> 介面的複雜性以及任何產生的問題，方法是將序列化與還原序列化的責任賦予最具衍生性的實作。 除此之外，此機制允許格式子忽略欄位填入以及自序列化資料流的擷取。 如需控制序列化與還原序列化的詳細資訊以及範例，請按一下任何一個先前的連結。  
  
 除此之外，當加入新欄位至現有可序列化型別時，即對欄位套用 <xref:System.Runtime.Serialization.OptionalFieldAttribute> 屬性。 在處理遺漏新欄位的資料流時，<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 及 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 會忽略缺少的欄位。  
  
## <a name="implementing-the-iserializable-interface"></a>實作 ISerializable 介面  
 控制序列化的另一個方法是實作物件上的 <xref:System.Runtime.Serialization.ISerializable> 介面。 不過請注意，前一節的方法會取代此方法來控制序列化。  
  
 此外，對於標記為 [Serializable](xref:System.SerializableAttribute) 屬性且在類別層級或其建構函式上擁有宣告式或命令式安全性的類別，不應使用預設序列化。 取代的做法是讓這些類別實作 <xref:System.Runtime.Serialization.ISerializable> 介面。  
  
 實作 <xref:System.Runtime.Serialization.ISerializable> 包括實作 `GetObjectData` 方法，以及還原序列化某物件時使用的特殊建構函式。 下列範例程式碼顯示如何在上一個章節的 <xref:System.Runtime.Serialization.ISerializable> 類別上實作 `MyObject`。  
  
```csharp  
[Serializable]  
public class MyObject : ISerializable   
{  
  public int n1;  
  public int n2;  
  public String str;  
  
  public MyObject()  
  {  
  }  
  
  protected MyObject(SerializationInfo info, StreamingContext context)  
  {  
    n1 = info.GetInt32("i");  
    n2 = info.GetInt32("j");  
    str = info.GetString("k");  
  }  
[SecurityPermissionAttribute(SecurityAction.Demand,   
SerializationFormatter =true)]  
  
public virtual void GetObjectData(SerializationInfo info, StreamingContext context)  
  {  
    info.AddValue("i", n1);  
    info.AddValue("j", n2);  
    info.AddValue("k", str);  
  }  
}  
```  
  
```vb  
<Serializable()>  _  
Public Class MyObject  
    Implements ISerializable  
    Public n1 As Integer  
    Public n2 As Integer  
    Public str As String  
  
    Public Sub New()   
    End Sub   
  
    Protected Sub New(ByVal info As SerializationInfo, _  
    ByVal context As StreamingContext)   
        n1 = info.GetInt32("i")  
        n2 = info.GetInt32("j")  
        str = info.GetString("k")  
    End Sub 'New  
  
    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Public Overridable Sub GetObjectData(ByVal info As _  
    SerializationInfo, ByVal context As StreamingContext)   
        info.AddValue("i", n1)  
        info.AddValue("j", n2)  
        info.AddValue("k", str)  
    End Sub   
End Class  
```  
  
 在序列化期間呼叫 **GetObjectData** 時，您必須填入方法呼叫所提供的 <xref:System.Runtime.Serialization.SerializationInfo>。 以名稱與值的配對，加入想要序列化的變數。 任何文字都能當成名稱使用。 您可自由決定要加入哪些成員變數至 <xref:System.Runtime.Serialization.SerializationInfo>，前提是在還原序列化期間序列化足夠的資料以還原物件。 如果基底物件實作 <xref:System.Runtime.Serialization.ISerializable>，衍生類別應呼叫基底物件的 **GetObjectData** 方法。  
  
 請注意，序列化可允許其他程式碼看到或變更原本無法存取的物件執行個體資料。 因此，執行序列化的程式碼需要已指定 <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> 旗標的 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute)。 依照預設原則，這個使用權限不會授與給網際網路下載或內部網路的程式碼；只有本機電腦上的程式碼才會被授與這個使用權限。 **GetObjectData** 方法必須明確加以保護，做法是要求已指定 <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> 旗標的 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) 或要求專門協助保護私人資料的其他權限。  
  
 如果私用欄位儲存機密資訊，您應該要求 **GetObjectData** 的適當權限以保護資料。 請記住，擁有已指定 **SerializationFormatter** 旗標之 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) 授權的程式碼，可以檢視與變更儲存在私用欄位的資料。 已授與此 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) 的惡意呼叫者，可檢視資料 (例如隱藏的目錄位置或授與的權限) 並以資料利用電腦上的安全性弱點。 如需可指定的安全性權限旗標完整清單，請參閱 [SecurityPermissionFlag 列舉](xref:System.Security.Permissions.SecurityPermissionFlag)。  
  
 特別要強調的是，將 <xref:System.Runtime.Serialization.ISerializable> 新增至類別時，您必須同時實作 **GetObjectData** 以及特殊的建構函式。 如果遺漏 **GetObjectData**，編譯器會警告您。 然而，因為不可能強制實作建構函式，因此若缺少建構函式時並不會發出警告，若試圖對無建構函式的類別還原序列化時會擲出例外狀況。  
  
 目前設計在避開潛在安全性與版本設定問題上，較 <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> 方法更受歡迎。 例如，若 `SetObjectData` 方法定義為介面的一部分，就必須為公用，因此使用者必須撰寫程式碼避免多次呼叫 **SetObjectData** 方法。 否則，對執行作業程序中物件呼叫 **SetObjectData** 方法的惡意應用程式，就可能造成潛在的問題。  
  
 在還原序列化期間，<xref:System.Runtime.Serialization.SerializationInfo> 將使用專門的建構函式傳遞給類別。 物件還原序列化後，即忽略所有對建構函式所設定的可視性約束，因此您可將類別標示為公用的、保護的、內部的或私用的。 不過，最好的做法是除非類別已密封，此時應將建構函式標示為保護的，在此狀況下建構函式應標示為私人的。 建構函式應進行徹底的輸入驗證。 為了避免惡意程式碼的濫用，建構函式應使用任何其他建構函式，強制執行取得類別的執行個體時所需的相同安全性檢查和使用權限。 如果您未遵循此建議，惡意程式碼可以預先序列化物件，並以指定為 <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> 旗標的 [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) 取得控制，然後在用戶端電腦還原序列化物件，略過所有使用公用建構函式在標準執行個體建構期間套用的安全性。  
  
 若想要還原物件的狀態，只要從 <xref:System.Runtime.Serialization.SerializationInfo> 以序列化期間使用的名稱擷取變數值， 若基底類別實作 <xref:System.Runtime.Serialization.ISerializable>，應呼叫基底建構函式以允許基底物件還原變數。  
  
 從實作 <xref:System.Runtime.Serialization.ISerializable> 的類別衍生新類別時，若也有需要序列化的變數時，衍生類別必須也實作兩者的建構函式以及 **GetObjectData** 方法。 下列程式碼範例示範如何使用先前所示的 `MyObject` 類別做到這點。  
  
```csharp  
[Serializable]  
public class ObjectTwo : MyObject  
{  
    public int num;  
  
    public ObjectTwo() : base()  
    {  
    }  
  
    protected ObjectTwo(SerializationInfo si,   
    StreamingContext context) : base(si,context)  
    {  
        num = si.GetInt32("num");  
    }  
[SecurityPermissionAttribute(SecurityAction.Demand,  
SerializationFormatter = true)]  
    public override void GetObjectData(SerializationInfo si,   
    StreamingContext context)  
    {  
        base.GetObjectData(si,context);  
        si.AddValue("num", num);  
    }  
}  
```  
  
```vb  
<Serializable()>  _  
Public Class ObjectTwo  
    Inherits MyObject  
    Public num As Integer  
  
    Public Sub New()   
  
    End Sub       
  
    Protected Sub New(ByVal si As SerializationInfo, _  
    ByVal context As StreamingContext)   
        MyBase.New(si, context)  
        num = si.GetInt32("num")      
    End Sub   
  
    <SecurityPermissionAttribute(SecurityAction.Demand, _  
    SerializationFormatter := True)>  _  
    Public Overrides Sub GetObjectData(ByVal si As _  
    SerializationInfo, ByVal context As StreamingContext)   
        MyBase.GetObjectData(si, context)  
        si.AddValue("num", num)      
    End Sub   
End Class  
```  
  
 請不要忘記在還原序列化建構函式中呼叫基底類別。 若不這麼做，將永遠不會呼叫基底類別上的建構函式，物件在還原序列化之後就不會完整建構。  
  
 物件由內向外重新建構；在還原序列化期間呼叫方法可能會造成無法想像的副作用，因為呼叫的方法可能參考該呼叫尚未還原序列化時的物件參考。 如果還原序列化的類別實作 <xref:System.Runtime.Serialization.IDeserializationCallback>，在整個物件圖形還原序列化後，即自動呼叫 <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> 方法。 此時，所有參考的子物件已完整還原。 雜湊表是不使用事件接聽程式就很難還原序列化的常見類別範例。 在還原序列化期間擷取索引鍵與值組很容易，但將這些物件加回雜湊表卻會造成問題，因為無法保證從雜湊表衍生的類別已還原序列化。 因此於此階段呼叫雜湊表上的方法實屬不當。  
  
## <a name="see-also"></a>另請參閱

- [二進位序列化](binary-serialization.md)  
- [XML 和 SOAP 序列化](xml-and-soap-serialization.md)  
- [安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)
