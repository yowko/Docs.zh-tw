---
title: "物件的預設封送處理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Interop 封送處理, 物件"
  - "物件, Interop 封送處理"
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 物件的預設封送處理
型別為 <xref:System.Object?displayProperty=fullName> 的參數和欄位可以公開 \(Expose\) 給 Unmanaged 程式碼，做為下列其中一個型別：  
  
-   Variant \- 當物件是參數時。  
  
-   Interface \- 當物件是結構欄位時。  
  
 只有 COM Interop 支援物件型別的封送處理 \(Marshaling\)。  預設行為是將物件封送處理至 COM Variant。  這些規則只能套用至 **Object** 型別，而且無法套用至衍生自 **Object** 類別的強型別 \(Strongly Typed\) 物件。  
  
 這個主題提供以下有關封送處理物件型別的其他資訊：  
  
-   [封送處理選項](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [將物件封送處理至介面](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [將物件封送處理至 Variant](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [將 Variant 封送處理至物件](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [封送處理 ByRef Variant](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## 封送處理選項  
 下表顯示 **Object** 資料型別的封送處理選項。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供多個 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值封送處理物件。  
  
|列舉型別|Unmanaged 格式的說明|  
|----------|---------------------|  
|**UnmanagedType.Struct**<br /><br /> \(參數的預設值\)|COM\-style Variant|  
|**UnmanagedType.Interface**|**IDispatch** 介面 \(如果可能\)，否則為 **IUnknown** 介面|  
|**UnmanagedType.IUnknown**<br /><br /> \(欄位的預設值\)|**IUnknown** 介面|  
|**UnmanagedType.IDispatch**|**IDispatch** 介面|  
  
 下列範例顯示 `MarshalObject` 的 Managed 介面定義。  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 下列程式碼會將 `MarshalObject` 介面匯出至型別程式庫。  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  Interop 封送處理器會在呼叫後自動釋放 Variant 內的任何配置物件。  
  
 下列範例顯示格式化的實值型別 \(Value Type\)。  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 下列程式碼會將格式化的型別匯出至型別程式庫。  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## 將物件封送處理至介面  
 將物件當成介面公開給 COM 時，該介面是 Managed 型別 <xref:System.Object> \(**\_Object** 介面\) 的類別介面。  在產生的型別程式庫中，此介面的型別設定為 **IDispatch** \([UnmanagedType.IDispatch](frlrfSystemRuntimeInteropServicesUnmanagedTypeClassTopic)\) 或 **IUnknown** \(**UnmanagedType.IUnknown**\)。  COM 用戶端可以動態地透過 **\_Object** 介面叫用 Managed 類別的成員或其衍生類別 \(Derived Class\) 所實作的任何成員。  用戶端也可以呼叫 **QueryInterface**，取得任何其他由 Managed 型別明確實作的介面。  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## 將物件封送處理至 Variant  
 將物件封送處理至 Variant 時，會根據以下規則來決定執行階段時內部 Variant 型別：  
  
-   如果物件參考是 null \(在 Visual Basic 中為 **Nothing**\)，則該物件會封送處理至 **VT\_EMPTY** 型別的 Variant。  
  
-   如果物件是任何列在下表中的任何型別之執行個體，則內建在封送處理器的規則會決定產生的 Variant 型別，如下表所示。  
  
-   其他需要明確控制封送處理行為的物件可以實作 <xref:System.IConvertible> 介面。  在這種情況下，從 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=fullName> 方法傳回的型別程式碼會決定 Variant 型別。  否則，物件會封送處理為 **VT\_UNKNOWN** 型別的 Variant。  
  
### 將系統型別封送處理至 Variant  
 下表顯示 Managed 物件型別和其對應的 COM Variant 型別。  這些型別只有在呼叫之方法的簽章 \(Signature\) 是 <xref:System.Object?displayProperty=fullName> 型別時才會進行轉換。  
  
|物件型別|COM Variant 型別|  
|----------|--------------------|  
|Null 物件參考 \(在 Visual Basic 中為 **Nothing**\)|**VT\_EMPTY**|  
|<xref:System.DBNull?displayProperty=fullName>|**VT\_NULL**|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=fullName>|**VT\_ERROR**|  
|<xref:System.Reflection.Missing?displayProperty=fullName>|**VT\_ERROR** 和 **E\_PARAMNOTFOUND**|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=fullName>|**VT\_DISPATCH**|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=fullName>|**VT\_UNKNOWN**|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=fullName>|**VT\_CY**|  
|<xref:System.Boolean?displayProperty=fullName>|**VT\_BOOL**|  
|<xref:System.SByte?displayProperty=fullName>|**VT\_I1**|  
|<xref:System.Byte?displayProperty=fullName>|**VT\_UI1**|  
|<xref:System.Int16?displayProperty=fullName>|**VT\_I2**|  
|<xref:System.UInt16?displayProperty=fullName>|**VT\_UI2**|  
|<xref:System.Int32?displayProperty=fullName>|**VT\_I4**|  
|<xref:System.UInt32?displayProperty=fullName>|**VT\_UI4**|  
|<xref:System.Int64?displayProperty=fullName>|**VT\_I8**|  
|<xref:System.UInt64?displayProperty=fullName>|**VT\_UI8**|  
|<xref:System.Single?displayProperty=fullName>|**VT\_R4**|  
|<xref:System.Double?displayProperty=fullName>|**VT\_R8**|  
|<xref:System.Decimal?displayProperty=fullName>|**VT\_DECIMAL**|  
|<xref:System.DateTime?displayProperty=fullName>|**VT\_DATE**|  
|<xref:System.String?displayProperty=fullName>|**VT\_BSTR**|  
|<xref:System.IntPtr?displayProperty=fullName>|**VT\_INT**|  
|<xref:System.UIntPtr?displayProperty=fullName>|**VT\_UINT**|  
|<xref:System.Array?displayProperty=fullName>|**VT\_ARRAY**|  
  
 使用前一個範例定義的 `MarshalObject` 介面，下列程式碼範例示範如何將不同 Variant 型別傳遞給 COM 伺服器。  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 您可以使用包裝函式類別 \(Wrapper Class\) 如 <xref:System.Runtime.InteropServices.ErrorWrapper>、<xref:System.Runtime.InteropServices.DispatchWrapper>、<xref:System.Runtime.InteropServices.UnknownWrapper> 和 <xref:System.Runtime.InteropServices.CurrencyWrapper>，封送處理沒有對應 Managed 型別的 COM 型別。  下列程式碼範例示範如何使用這些包裝函式，將不同的 Variant 型別傳遞給 COM 伺服器。  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 包裝函式類別是在 <xref:System.Runtime.InteropServices> 命名空間 \(Namespace\) 中定義。  
  
### 將 IConvertible 介面封送處理至 Variant  
 除了在上一節中所列的型別之外，型別可以藉由實作 <xref:System.IConvertible> 介面來控制其封送處理的方式。  如果物件實作 **IConvertible** 介面，則從 <xref:System.IConvertible.GetTypeCode%2A?displayProperty=fullName> 方法傳回的 <xref:System.TypeCode> 列舉值會在執行階段決定 COM Variant 型別。  
  
 下表顯示 **TypeCode** 可能的列舉值，以及每一個值的對應 COM Variant 型別。  
  
|TypeCode|COM Variant 型別|  
|--------------|--------------------|  
|**TypeCode.Empty**|**VT\_EMPTY**|  
|**TypeCode.Object**|**VT\_UNKNOWN**|  
|**TypeCode.DBNull**|**VT\_NULL**|  
|**TypeCode.Boolean**|**VT\_BOOL**|  
|**TypeCode.Char**|**VT\_UI2**|  
|**TypeCode.Sbyte**|**VT\_I1**|  
|**TypeCode.Byte**|**VT\_UI1**|  
|**TypeCode.Int16**|**VT\_I2**|  
|**TypeCode.UInt16**|**VT\_UI2**|  
|**TypeCode.Int32**|**VT\_I4**|  
|**TypeCode.UInt32**|**VT\_UI4**|  
|**TypeCode.Int64**|**VT\_I8**|  
|**TypeCode.UInt64**|**VT\_UI8**|  
|**TypeCode.Single**|**VT\_R4**|  
|**TypeCode.Double**|**VT\_R8**|  
|**TypeCode.Decimal**|**VT\_DECIMAL**|  
|**TypeCode.DateTime**|**VT\_DATE**|  
|**TypeCode.String**|**VT\_BSTR**|  
|不支援。|**VT\_INT**|  
|不支援。|**VT\_UINT**|  
|不支援。|**VT\_ARRAY**|  
|不支援。|**VT\_RECORD**|  
|不支援。|**VT\_CY**|  
|不支援。|**VT\_VARIANT**|  
  
 COM Variant 的值是由呼叫 **IConvertible.To** *Type* 介面決定，其中 **To** *Type* 為轉換常式，會對應從 **IConvertible.GetTypeCode** 傳回的型別。  例如，從 **IConvertible.GetTypeCode** 傳回 **TypeCode.Double** 的物件，會封送處理為 **VT\_R8** 型別的 COM Variant。  透過轉型 \(Casting\) 至 **IConvertible** 介面和呼叫 <xref:System.IConvertible.ToDouble%2A> 方法，您可以取得 Variant \(存放在 COM Variant 的 **dblVal** 欄位\) 的值。  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## 將 Variant 封送處理至物件  
 將 Variant 封送處理至物件時，封送處理的 Variant 之型別 \(有時候是值\) 會決定產生的物件型別。  下表識別每一個 Variant 型別和對應的物件型別 \(此物件型別是 Variant 從 COM 傳遞到 .NET Framework 時由封送處理器所建立的\)。  
  
|COM Variant 型別|物件型別|  
|--------------------|----------|  
|**VT\_EMPTY**|Null 物件參考 \(在 Visual Basic 中為 **Nothing**\)|  
|**VT\_NULL**|<xref:System.DBNull?displayProperty=fullName>|  
|**VT\_DISPATCH**|**System.\_\_ComObject** 或如果 \(pdispVal \=\= null\) 則為 null|  
|**VT\_UNKNOWN**|**System.\_\_ComObject** 或如果 \(punkVal \=\= null\) 則為 null|  
|**VT\_ERROR**|<xref:System.UInt32?displayProperty=fullName>|  
|**VT\_BOOL**|<xref:System.Boolean?displayProperty=fullName>|  
|**VT\_I1**|<xref:System.SByte?displayProperty=fullName>|  
|**VT\_UI1**|<xref:System.Byte?displayProperty=fullName>|  
|**VT\_I2**|<xref:System.Int16?displayProperty=fullName>|  
|**VT\_UI2**|<xref:System.UInt16?displayProperty=fullName>|  
|**VT\_I4**|<xref:System.Int32?displayProperty=fullName>|  
|**VT\_UI4**|<xref:System.UInt32?displayProperty=fullName>|  
|**VT\_I8**|<xref:System.Int64?displayProperty=fullName>|  
|**VT\_UI8**|<xref:System.UInt64?displayProperty=fullName>|  
|**VT\_R4**|<xref:System.Single?displayProperty=fullName>|  
|**VT\_R8**|<xref:System.Double?displayProperty=fullName>|  
|**VT\_DECIMAL**|<xref:System.Decimal?displayProperty=fullName>|  
|**VT\_DATE**|<xref:System.DateTime?displayProperty=fullName>|  
|**VT\_BSTR**|<xref:System.String?displayProperty=fullName>|  
|**VT\_INT**|<xref:System.Int32?displayProperty=fullName>|  
|**VT\_UINT**|<xref:System.UInt32?displayProperty=fullName>|  
|**VT\_ARRAY** &#124; **VT\_\***|<xref:System.Array?displayProperty=fullName>|  
|**VT\_CY**|<xref:System.Decimal?displayProperty=fullName>|  
|**VT\_RECORD**|對應的 Boxed 實值型別|  
|**VT\_VARIANT**|不支援。|  
  
 從 COM 傳遞到 Managed 程式碼然後回到 COM 的 Variant 型別可能無法在呼叫期間保持相同的 Variant 型別。  請考量當 **VT\_DISPATCH** 型別的 Variant 是從 COM 傳遞到 .NET Framework 時會發生什麼狀況。  在封送處理期間，Variant 會轉換成 <xref:System.Object?displayProperty=fullName>。  如果接著將 **Object** 傳回 COM，它會封送處理回 **VT\_UNKNOWN** 型別的 Variant。  無法保證在從 Managed 程式碼將物件封送處理至 COM 時產生的 Variant，會和最初用來產生該物件的 Variant 有相同的型別。  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## 封送處理 ByRef Variant  
 雖然 Variant 本身可以利用傳值 \(By Value\) 或傳址 \(By Reference\) 方式進行傳遞，但 **VT\_BYREF** 旗標也可以與任何 Variant 型別一起使用，來指示 Variant 的內容是以傳址方式而非傳值方式傳遞。  以傳址方式封送處理 Variant 和以 **VT\_BYREF** 旗標組封送處理 Variant 之間的差異可能會令人產生混淆。  下圖會澄清這個差異。  
  
 ![堆疊上傳遞的變數](../../../docs/framework/interop/media/interopvariant.gif "interopvariant")  
以傳值或傳址方式傳遞的 Variant  
  
 **以傳值方式封送處理物件和 Variant 的預設行為**  
  
-   將物件從 Managed 程式碼傳遞至 COM 時，會使用[將物件封送處理至 Variant](#cpcondefaultmarshalingforobjectsanchor3) 中定義的規則 \(Rule\)，物件的內容複製到封送處理器所建立的新 Variant 中。  對 Unmanaged 端上的 Variant 所做的變更並不會在從呼叫中返回時傳回至原始物件。  
  
-   將 Variant 從 COM 傳遞至 Managed 程式碼時，會使用[將 Variant 封送處理至物件](#cpcondefaultmarshalingforobjectsanchor4)中定義的規則，將 Variant 的內容複製到全新建立的物件中。  對 Managed 端上的物件所做的變更並不會在從呼叫中返回時傳回至原始 Variant。  
  
 **以傳址方式封送處理物件和 Variant 的預設行為**  
  
 若要將變更傳回至呼叫端，參數必須是以傳址方式傳遞。  例如，您可以使用 C\# 中的 **ref** 關鍵字 \(或 Visual Basic Managed 程式碼中的 **ByRef**\)，以傳址方式傳遞參數。  在 COM 中，傳址參數是使用指標 \(例如 **variant \***\) 傳遞的。  
  
-   以傳址方式將物件傳遞至 COM 時，封送處理器會建立新的 Variant，並且在呼叫之前將物件參考的內容複製到 Variant。  Variant 會傳遞到使用者可以隨意變更 Variant 內容的 Unmanaged 函式中。  從呼叫中返回時，任何對 Unmanaged 端上的 Variant 所做的變更會傳回至原始物件。  如果 Variant 的型別不同於傳回給呼叫的 Variant 的型別，則變更會傳回至不同型別的物件。  也就是說，傳遞至呼叫中的物件型別可以不同於從呼叫中傳回的物件型別。  
  
-   以傳址方式將 Variant 傳遞至 Managed 程式碼時，封送處理器會建立新的物件，並且在呼叫之前將 Variant 的內容複製到物件。  物件的參考會傳遞到使用者可以隨意變更物件的 Managed 函式中。  從呼叫中返回時，任何對參考的物件所做的變更會傳回至原始 Variant。  如果物件的型別不同於傳入至呼叫的物件型別，則會變更原始 Variant 的型別，而且將值傳回至 Variant。  再者，傳遞至呼叫中的 Variant 型別可以不同於從呼叫中傳回的 Variant 型別。  
  
 **以 VT\_BYREF 旗標組封送處理 Variant 的預設行為**  
  
-   以傳值方式傳遞到 Managed 程式碼的 Variant 可以具有 **VT\_BYREF** 旗標組，以指示 Variant 包含參考而不是值。  在這種情況下，因為 Variant 是以傳值方式傳遞，因此仍然會封送處理至物件。  封送處理器會在產生呼叫之前，自動將 Variant 的內容解除參考，並將它複製到新建立的物件。  這個物件接著會傳遞到 Managed 函式，但是在從呼叫中返回時，物件不會傳回至原始的 Variant。  而對 Managed 物件所做的變更將會遺失。  
  
    > [!CAUTION]
    >  即使 Variant 已設定 **VT\_BYREF** 旗標，還是無法變更以傳值方式傳遞的 Variant 值。  
  
-   以傳址方式傳遞到 Managed 程式碼的 Variant 也可以具有 **VT\_BYREF** 旗標組來指示 Variant 包含其他參考。  如果如此，Variant 會封送處理至 **ref** 物件，因為 Variant 是以傳址方式傳遞。  封送處理器會在產生呼叫之前，自動將 Variant 的內容解除參考，並將它複製到新建立的物件。  只有在該物件的型別是和傳入的物件一樣時，在從呼叫中返回的時候，這個物件的值會傳回至原始 Variant 內的參考中。  也就是說，傳用不會以 **VT\_BYREF** 旗標組變更 Variant 的型別。  如果在呼叫期間變更物件的型別，則在從呼叫返回時會發生 <xref:System.InvalidCastException>。  
  
 下表總結 Variant 和物件的傳用規則。  
  
|From|若要|變更的傳回|  
|----------|--------|-----------|  
|**Variant**  *v*|**Object**  *o*|永不|  
|**Object**  *o*|**Variant**  *v*|永不|  
|**Variant**   ***\****  *pv*|**Ref Object**  *o*|永遠|  
|**Ref object**  *o*|**Variant**   ***\****  *pv*|永遠|  
|**Variant**  *v* **\(VT\_BYREF** *&#124;*  **VT\_\*\)**|**Object**  *o*|永不|  
|**Variant**  *v* **\(VT\_BYREF** *&#124;*  **VT\_\)**|**Ref Object**  *o*|只有在未變更型別時|  
  
## 請參閱  
 [預設的封送處理行為](../../../docs/framework/interop/default-marshaling-behavior.md)   
 [Blittable 和非 Blittable 類型](../../../docs/framework/interop/blittable-and-non-blittable-types.md)   
 [Directional Attributes](http://msdn.microsoft.com/zh-tw/241ac5b5-928e-4969-8f58-1dbc048f9ea2)   
 [複製和 Pin](../../../docs/framework/interop/copying-and-pinning.md)