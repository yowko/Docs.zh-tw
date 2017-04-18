---
title: "陣列的預設封送處理 | Microsoft Docs"
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
  - "陣列, Interop 封送處理"
  - "Interop 封送處理, 陣列"
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 陣列的預設封送處理
在完全由 Managed 程式碼所組成的應用程式中，Common Language Runtime 會將陣列型別當成 In\/Out 參數傳遞。  相對地，Interop 封送處理器預設會將陣列當成 In 參數傳遞。  
  
 使用 [Pin 的最佳化](../../../docs/framework/interop/copying-and-pinning.md)，在相同 Apartment 中與物件進行互動時，Blittable 陣列可以當成 In\/Out 參數進行操作。  但是，如果您稍後將程式碼匯入型別程式庫 \(用來產生跨電腦 Proxy\)，以及該程式庫是用來封送處理您跨 Apartment 的呼叫，則呼叫可以回復到真實的 In 參數行為。  
  
 陣列本質上是複雜的，而 Managed 和 Unmanaged 陣列的差異比其他非 Blittable 型別提供了更多資訊。  這個主題提供以下有關封送處理陣列的資訊：  
  
-   [Managed 陣列](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Unmanaged 陣列](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [將陣列參數傳遞給 .NET 程式碼](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [將陣列傳遞給 COM](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## Managed 陣列  
 Managed 陣列型別可以改變；但是 <xref:System.Array?displayProperty=fullName> 類別是所有陣列型別的基底類別。  **System.Array** 類別具有決定陣序、長度和陣列下限與上限的屬性，以及具有存取、排序、搜尋和建立陣列的方法。  
  
 這些陣列型別是動態的，而且沒有在基底類別庫中定義的對應靜態型別。  考慮將每個元素型別和陣序規範的組合當成陣列的不同型別是很方便的。  因此，整數的一維陣列和 double 型別的一維陣列是不同的型別。  同樣地，整數的二維陣列不同於整數的一維陣列。  比較型別時，並不會考慮陣列的界限。  
  
 如下表所示，任何 Managed 陣列的執行個體必須是特定元素型別、陣序規範和下限。  
  
|Managed 陣列型別|項目型別|順序|下限|簽章標記法|  
|------------------|----------|--------|--------|-----------|  
|**ELEMENT\_TYPE\_ARRAY**|由 type 指定|由 rank 指定|選擇性地由 bounds 指定|*type* **\[** *n*,*m* **\]**|  
|**ELEMENT\_TYPE\_CLASS**|未知|未知|未知|**System.Array**|  
|**ELEMENT\_TYPE\_SZARRAY**|由 type 指定|1|0|*type* **\[** *n* **\]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## Unmanaged 陣列  
 Unmanaged 陣列是具有固定或可變長度的 COM\-style 安全陣列或 C\-Style 陣列。  安全陣列是自我描述陣列，具有型別、陣序規範和關聯陣列資料的繫結。  C\-Style 陣列是具有固定 0 下限的一維型別的陣列。  封送處理服務對這兩種陣列有限制的支援。  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## 將陣列參數傳遞給 .NET 程式碼  
 從 Unmanaged 程式碼中可以將 C\-Style 陣列和安全陣列傳遞給 .NET 程式碼，其可做為安全陣列或 C\-Style 陣列。  下表顯示 Unmanaged 型別值和匯入的型別。  
  
|Unmanaged 型別|匯入的型別|  
|------------------|-----------|  
|**SafeArray\(** *Type* **\)**|**ELEMENT\_TYPE\_SZARRAY** **\<** *ConvertedType* **\>**<br /><br /> 陣序 \= 1，下限 \= 0。  大小只有包含在 Managed 簽章中時才會知道。  不是陣序規範 \= 1 或下限 \= 0 的安全陣列無法封送處理為 **SZARRAY**。|  
|*Type*  **\[\]**|**ELEMENT\_TYPE\_SZARRAY** **\<** *ConvertedType* **\>**<br /><br /> 陣序 \= 1，下限 \= 0。  大小只有包含在 Managed 簽章中時才會知道。|  
  
### 安全陣列  
 當安全陣列是由型別程式庫匯入至 .NET 組件時，陣列會轉換為已知型別 \(如 **int**\) 的一維陣列。  套用至參數的相同型別轉換也會套用至陣列元素。  例如，**BSTR** 型別的安全陣列會變成字串的 Managed 陣列，而變數的安全陣列會變成物件的 Managed 陣列。  **SAFEARRAY** 元素型別是從型別程式庫中所擷取的，而且儲存在 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉型別的 **SAFEARRAY** 值中。  
  
 因為無法從型別程式庫來判斷安全陣列的陣序和界限，所以陣序會假設等於 1，而下限假設等於 0。  陣序和界限必須在[型別程式庫匯入工具 \(TlbImp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 所產生的 Managed 簽章中定義。  如果傳遞給方法的陣序在執行階段改變，會擲回 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>。  如果傳遞的陣列型別在執行階段改變的話，會擲回 <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException>。  下列範例顯示 Managed 和 Unmanaged 程式碼中的安全陣列。  
  
 **Unmanaged 簽章**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Managed 簽章**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 如果 Tlbimp.exe 所產生的方法簽章修改為表示 **ELEMENT\_TYPE\_ARRAY** \(而非 **ELEMENT\_TYPE\_SZARRAY**\) 的元素型別，則多維或非零界限的安全陣列可以封送處理至 Managed 程式碼中。  或者，您可以搭配 Tlbimp.exe 使用 **\/sysarray** 參數來匯入所有陣列做為 <xref:System.Array?displayProperty=fullName> 物件。  在知道傳遞的陣列是多維陣列的情況下，您可以編輯 Tlbimp.exe 所產生的 Microsoft Intermediate Language \(MSIL\) 程式碼，然後將其重新編譯。  如需如何修改 MSIL 程式碼的詳細資訊，請參閱[自訂執行階段可呼叫包裝函式](http://msdn.microsoft.com/zh-tw/4652beaf-77d0-4f37-9687-ca193288c0be)。  
  
### C\-Style 陣列  
 從型別程式庫中將 C\-Style 陣列匯入至 .NET 組件時，陣列會轉換為 **ELEMENT\_TYPE\_SZARRAY**。  
  
 陣列元素型別會從型別程式庫中決定，以及在匯入期間保留下來。  套用至參數的相同轉換也會套用至陣列元素。  例如，**LPStr** 型別的陣列會變成 **String** 型別的陣列。  Tlbimp.exe 會擷取陣列元素型別，並將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性套用至參數中。  
  
 陣列陣序會假設為等於 1。  如果陣序大於 1，則陣列會被以行為主的順序封送處理為一維陣列。  下限永遠等於 0。  
  
 型別程式庫可以包含固定或可變長度的陣列。  Tlbimp.exe 只能從型別程式庫中匯入固定長度陣列，因為型別程式庫缺少封送處理可變長度陣列所需要的資訊。  以固定長度陣列來說，大小是從型別程式庫匯入的，並且是在套用參數的 **MarshalAsAttribute** 中擷取的。  
  
 您必須手動定義含有可變長度陣列的型別程式庫，如下列範例所顯示。  
  
 **Unmanaged 簽章**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Managed 簽章**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 雖然您可以在介面定義語言 \(IDL\) 的原始程式碼中將 **size\_is** 或 **length\_is** 屬性套用至陣列中，以將大小傳遞給用戶端，但是 Microsoft 介面定義語言 \(MIDL\) 編譯器並不會將該資訊傳播給型別程式庫。  缺乏大小資訊，Interop 封送處理服務將無法封送處理陣列元素。  因此，可變長度陣列就會匯入為參考引數。  例如：  
  
 **Unmanaged 簽章**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Managed 簽章**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 您可以編輯 Tlbimp.exe 所產生的 Microsoft Intermediate Language \(MSIL\) 程式碼然後重新編譯它，來將陣列大小提供給封送處理器。  如需如何修改 MSIL 程式碼的詳細資訊，請參閱[自訂執行階段可呼叫包裝函式](http://msdn.microsoft.com/zh-tw/4652beaf-77d0-4f37-9687-ca193288c0be)。  若要指示陣列中的元素數目，請以下列其中一個方式，將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 型別套用至 Managed 方法定義的陣列參數中：  
  
-   識別其他包含陣列元素數目的參數。  這些參數是以位置識別，開始的第一個參數是數字 0。  \[Visual Basic\]  
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       <MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   將陣列的大小定義為常數。  例如：  
  
    ```vb  
    Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 從 Unmanaged 程式碼將陣列封送處理至 Managed 程式碼時，封送處理器會檢查與參數關聯的 **MarshalAsAttribute** 來決定陣列大小。  如果沒有指定陣列大小，則只有一個元素會封送處理。  
  
> [!NOTE]
>  **MarshalAsAttribute** 對於將 Managed 陣列封送處理 \(Marshaling\) 為 Unmanaged 程式碼不會有影響。  在該方向中，陣列大小會是由檢查結果所決定的。  沒有封送處理 Managed 陣列之子集的方式。  
  
 Interop 封送處理器使用 **CoTaskMemAlloc** 和 **CoTaskMemFree** 方法來配置並擷取記憶體。  由 Unmanaged 程式碼所執行的記憶體配置也必須使用這些方法。  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## 將陣列傳遞給 COM  
 所有的 Managed 陣列型別都可以從 Managed 程式碼中傳遞給 Unmanaged 程式碼。  根據 Managed 型別以及套用至它的屬性，陣列可以存取為安全陣列或 C\-Style 陣列，如下表所顯示。  
  
|Managed 陣列型別|匯出為|  
|------------------|---------|  
|**ELEMENT\_TYPE\_SZARRAY** **\<** *type* **\>**|<xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray\(** *type* **\)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> 簽章中提供的型別。  陣序一定是 1，下限一定是 0。  大小永遠在執行階段時才會知道。|  
|**ELEMENT\_TYPE\_ARRAY** **\<** *type* **\>** **\<** *rank* **\>**\[**\<** *bounds* **\>**\]|**UnmanagedType.SafeArray\(** *type* **\)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> 型別、陣序規範、界限是包含在簽章中。  大小永遠在執行階段時才會知道。|  
|**ELEMENT\_TYPE\_CLASS** **\<**<xref:System.Array?displayProperty=fullName>**\>**|**UT\_Interface**<br /><br /> **UnmanagedType.SafeArray\(** *type* **\)**<br /><br /> 型別、陣序規範、界限和大小永遠在執行階段時才會知道。|  
  
 OLE Automation 有一項限制，與包含 LPSTR 或 LPWSTR 的結構陣列有關。  因此，**String** 欄位必須封送處理成 **UnmanagedType.BSTR**，  否則便會擲回例外狀況。  
  
### ELEMENT\_TYPE\_SZARRAY  
 當含有 **ELEMENT\_TYPE\_SZARRAY** 參數 \(一維陣列\) 的方法是從 .NET 組件匯出至型別程式庫時，陣列參數會轉換為指定型別的 **SAFEARRAY**。  相同的轉換規則將套用至陣列元素型別。  Managed 陣列的內容會自動從 Managed 記憶體中複製到 **SAFEARRAY**。  例如：  
  
#### Managed 簽章  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### Unmanaged 簽章  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 安全陣列的陣序一定是 1，而下限一定是 0。  大小是在執行階段時由已傳遞的 Managed 陣列之大小所決定。  
  
 使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將陣列封送處理為 C\-Style 陣列。  例如：  
  
#### Managed 簽章  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### Unmanaged 簽章  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 雖然封送處理器有封送處理陣列所需的長度資訊，但是陣列長度通常會以個別的引數傳遞，將長度傳遞給被呼叫端。  
  
### ELEMENT\_TYPE\_ARRAY  
 當含有 **ELEMENT\_TYPE\_ARRAY** 參數的方法是從 .NET 組件匯出至型別程式庫時，陣列參數會轉換為指定型別的 **SAFEARRAY**。  Managed 陣列的內容會自動從 Managed 記憶體中複製到 **SAFEARRAY**。  例如：  
  
#### Managed 簽章  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### Unmanaged 簽章  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 安全陣列的陣序規範、大小和界限是執行階段時由 Managed 陣列的特性所決定的。  
  
 套用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將陣列封送處理為 C\-Style 陣列。  例如：  
  
#### Managed 簽章  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### Unmanaged 簽章  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 無法封送處理巢狀陣列。  例如，當使用[型別程式庫匯出工具 \(Tlbexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) 匯出時，以下簽章會產生錯誤。  
  
#### Managed 簽章  
  
```vb  
Sub [New](ar()()() As Long)  
  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### ELEMENT\_TYPE\_CLASS \<System.Array\>  
 當含有 <xref:System.Array?displayProperty=fullName> 參數的方法從 .NET 組件匯出至型別程式庫時，陣列參數會轉換為 **\_Array** 介面。  只有透過 **\_Array** 介面的方法和屬性才可以存取 Managed 陣列的內容。  使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將 **System.Array** 封送處理為 **SAFEARRAY**。  當封送處理為安全陣列時，陣列元素會封送處理為 Variant。  例如：  
  
#### Managed 簽章  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### Unmanaged 簽章  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### 結構內的陣列  
 Unmanaged 結構可以包含內嵌陣列。  根據預設，這些內嵌陣列欄位都會封送處理成 SAFEARRAY。  在下列範例中，`s1` 是直接在結構本身內配置的內嵌陣列。  
  
#### Unmanaged 表示  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 陣列可以封送處理為 [UnmanagedType.ByValArray](frlrfSystemRuntimeInteropServicesUnmanagedTypeClassTopic)，會要求您設定 [MarshalAsAttribute.SizeConst](frlrfSystemRuntimeInteropServicesMarshalAsAttributeClassTopic) 欄位。  大小只可以設為常數。  下列程式碼顯示  `MyStruct` 的對應 Managed 定義。  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## 請參閱  
 [預設的封送處理行為](../../../docs/framework/interop/default-marshaling-behavior.md)   
 [Blittable 和非 Blittable 類型](../../../docs/framework/interop/blittable-and-non-blittable-types.md)   
 [Directional Attributes](http://msdn.microsoft.com/zh-tw/241ac5b5-928e-4969-8f58-1dbc048f9ea2)   
 [複製和 Pin](../../../docs/framework/interop/copying-and-pinning.md)