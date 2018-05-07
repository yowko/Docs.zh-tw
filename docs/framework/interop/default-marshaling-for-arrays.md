---
title: 陣列的預設封送處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05ac1016710109110c3ff9d0d318a71fe0827f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="default-marshaling-for-arrays"></a>陣列的預設封送處理
在包含整個 Managed 程式碼的應用程式中，Common Language Runtime 會將陣列類型傳遞為 In/Out 參數。 相較之下，Interop 封送處理器預設會將陣列傳遞為 In 參數。  
  
 使用[關聯最佳化](copying-and-pinning.md)，與相同 Apartment 中的物件互動時，Blittable 陣列可以操作為 In/Out 參數。 不過，如果您稍後將程式碼匯出至用來產生跨電腦 Proxy 的型別程式庫，並且使用該程式庫跨 Apartment 封送處理呼叫，則呼叫可以回復為實際 In 參數行為。  
  
 陣列本質上相當複雜，而且 Managed 與 Unmanaged 陣列之間的區別保證資訊比其他非 Blittable 類型還要多。 本主題提供下列封送處理陣列資訊：  
  
-   [Managed 陣列](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Unmanaged 陣列](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [將陣列參數傳遞給 .NET 程式碼](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [將陣列傳遞給 COM](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a>Managed 陣列  
 Managed 陣列類別可能會不同；不過，<xref:System.Array?displayProperty=nameWithType> 類別是所有陣列類型的基底類別。 **System.Array** 類別的屬性可以判斷陣列的順位、長度以及下限和上限，以及用來存取、排序、搜尋、複製和建立陣列的方法。  
  
 這些陣列類型是動態的，而且沒有基底類別庫中所定義的對應靜態類型。 很容易就會將每個項目類型和順位組合視為不同類型的陣列。 因此，一維整數陣列的類型與一維 Double 類型陣列不同。 同樣地，二維整數陣列與一維整數陣列不同。 比較類型時，不會考慮陣列界限。  
  
 如下表所示，任何 Managed 陣列執行個體都必須是特定項目類型、順位和下限。  
  
|Managed 陣列類型|項目類型|順位|下限|簽章標記法|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|依類型指定。|依順位指定。|選擇性依界限指定。|*型別* **[** *n*，*m* **]**|  
|**ELEMENT_TYPE_CLASS**|不明|不明|不明|**System.Array**|  
|**ELEMENT_TYPE_SZARRAY**|依類型指定。|1|0|*型別* **[** *n* **]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a>Unmanaged 陣列  
 Unmanaged 陣列是具有固定或變動長度的 COM 樣式安全陣列或 C 樣式陣列。 安全陣列是自我描述陣列，具有關聯陣列資料的類型、順位和界限。 C 樣式陣列是固定下限為 0 的一維類型陣列。 封送處理服務具有這兩種類型之陣列的有限支援。  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a>將陣列參數傳遞給 .NET 程式碼  
 從 Unmanaged 程式碼，可以將 C 樣式陣列和安全陣列以安全陣列或 C 樣式陣列形式傳遞給 .NET 程式碼。 下表顯示 Unmanaged 類型值和匯入的類型。  
  
|Unmanaged 類型|匯入的類型|  
|--------------------|-------------------|  
|**SafeArray(** *Type* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> 順位 = 1，下限 = 0。 只有在 Managed 簽章中提供時，才會知道大小。 不是順位 = 1 或下限 = 0 的安全陣列無法封送處理為 **SZARRAY**。|  
|*Type*  **[]**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> 順位 = 1，下限 = 0。 只有在 Managed 簽章中提供時，才會知道大小。|  
  
### <a name="safe-arrays"></a>安全陣列  
 將安全陣列從型別程式庫匯入至 .NET 組件時，會將陣列轉換成一維已知類型陣列 (例如 **int**)。 套用至參數的相同類型轉換規則也會套用至陣列項目。 例如，**BSTR** 類型的安全陣列變成 Managed 字串陣列，而變異值的安全陣列變成 Managed 物件陣列。 **SAFEARRAY** 項目類型擷取自型別程式庫，並儲存至 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉的 **SAFEARRAY** 值中。  
  
 因為無法從型別程式庫判斷安全陣列的順位和界限，所以順位會假設等於 1，而下限假設等於 0。 順位和界限必須定義於[型別程式庫匯入工具 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 所產生的 Managed 簽章中。 如果在執行階段傳遞給方法的順位不同，則會擲回 <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>。 如果在執行階段傳遞的陣列類型不同，則會擲回 <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException>。 下列範例示範 Managed 和 Unmanaged 程式碼中的安全陣列。  
  
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
  
 如果修改 Tlbimp.exe 所產生的方法簽章以指出項目類型為 **ELEMENT_TYPE_ARRAY** 而非 **ELEMENT_TYPE_SZARRAY**，則可以將多維度或非零繫結的安全陣列封送處理至 Managed 程式碼。 或者，您可以搭配使用 **/sysarray** 參數與 Tlbimp.exe，以將所有陣列匯入為 <xref:System.Array?displayProperty=nameWithType> 物件。 如果所傳遞的陣列已知為多維度，您可以編輯 Tlbimp.exe 所產生的 Microsoft Intermediate Language (MSIL) 程式碼，然後重新進行編譯。 如需如何修改 MSIL 程式碼的詳細資訊，請參閱[自訂執行階段可呼叫包裝函式](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))。  
  
### <a name="c-style-arrays"></a>C 樣式陣列  
 將 C 樣式陣列從型別程式庫匯入至 .NET 組件時，會將陣列轉換成 **ELEMENT_TYPE_SZARRAY**。  
  
 陣列項目類型取決於型別程式庫，並且在匯入期間保留。 套用至參數的相同轉換規則也會套用至陣列項目。 例如，**LPStr** 類型陣列會成為 **String** 類型陣列。 Tlbimp.exe 會擷取陣列項目類型，並將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性套用至參數。  
  
 陣列順位會假設等於 1。 如果順位大於 1，會以資料行主要順序將陣列封送處理為一維陣列。 下限一律會等於 0。  
  
 型別程式庫可以包含固定或可變長度的陣列。 Tlbimp.exe 只能從型別程式庫中匯入固定長度陣列，因為型別程式庫缺少封送處理可變長度陣列所需的資訊。 使用固定長度陣列，會從型別程式庫中匯入大小，並將其擷取於套用至參數的 **MarshalAsAttribute** 中。  
  
 您必須手動定義包含可變長度陣列的型別程式庫，如下列範例所示。  
  
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
  
 雖然您可以將 **size_is** 或 **length_is** 屬性套用至介面定義語言 (IDL) 來源中的陣列以將大小傳送至用戶端，但是 Microsoft 介面定義語言 (MIDL) 編譯器不會將該資訊傳播至型別程式庫。 如果不知道大小，Interop 封送處理服務無法封送處理陣列項目。 因此，會將可變長度的陣列匯入為參考引數。 例如:   
  
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
  
 您可以編輯 Tlbimp.exe 所產生的 Microsoft Intermediate Language (MSIL) 程式碼，然後重新進行編譯，以提供具有陣列大小的封送處理器。 如需如何修改 MSIL 程式碼的詳細資料，請參閱[自訂執行階段可呼叫包裝函式](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))。 若要指出陣列中的項目數，請使用下列其中一種方式，將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 類型套用至 Managed 方法定義的陣列參數：  
  
-   識別包含陣列中項目數的另一個參數。 參數是以位置進行識別，而第一個參數開始於數字 0。     
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
-   將陣列的大小定義為常數。 例如:   
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 將陣列從 Unmanaged 程式碼封送處理至 Managed 程式碼時，封送處理器會檢查與判斷陣列大小的參數建立關聯的 **MarshalAsAttribute**。 如果未指定陣列大小，則只能封送處理一個項目。  
  
> [!NOTE]
>  **MarshalAsAttribute** 不會影響從 Managed 陣列封送處理至 Unmanaged 程式碼。 在該方向，陣列大小取決於檢查。 沒有任何方法可以封送處理 Managed 陣列的子集。  
  
 Interop 封送處理器使用 **CoTaskMemAlloc** 和 **CoTaskMemFree** 方法來配置和擷取記憶體。 Unmanaged 程式碼所執行的記憶體配置也必須使用這些方法。  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a>將陣列傳遞給 COM  
 所有 Managed 陣列類型都可以從 Managed 程式碼傳遞至 Unmanaged 程式碼。 根據 Managed 類型和其套用的屬性，陣列可以存取為安全陣列或 C 樣式陣列，如下表所示。  
  
|Managed 陣列類型|匯出為|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**|<xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> 類型是在簽章中提供。 順位一律為 1，下限一律為 0。 在執行階段，一律會知道大小。|  
|**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]|**UnmanagedType.SafeArray(** *type* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> 在簽章中，提供類型、順位和界限。 在執行階段，一律會知道大小。|  
|**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray(** *type* **)**<br /><br /> 在執行階段，一律可辨識類型、順位、界限和大小。|  
  
 與包含 LPSTR 或 LPWSTR 之結構陣列有關的 OLE Automation 限制。  因此，必須將 [字串] 欄位封送處理為 **UnmanagedType.BSTR**。 否則便會擲回例外狀況。  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 將包含 **ELEMENT_TYPE_SZARRAY** 參數 (一維陣列) 的方法從 .NET 組件匯出至型別程式庫時，會將陣列參數轉換成指定類型的 **SAFEARRAY**。 相同的轉換規則會套用至陣列項目類型。 Managed 陣列的內容會自動從 Managed 記憶體複製至 **SAFEARRAY**。 例如:   
  
#### <a name="managed-signature"></a>Managed 簽章  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Unmanaged 簽章  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 安全陣列的順位一律為 1，而下限一律為 0。 在執行階段，大小取決於所傳遞 Managed 陣列的大小。  
  
 使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將陣列封送處理為 C 樣式陣列。 例如:   
  
#### <a name="managed-signature"></a>Managed 簽章  
  
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
  
#### <a name="unmanaged-signature"></a>Unmanaged 簽章  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 雖然封送處理器具有封送處理陣列所需的長度資訊，但是陣列長度通常會傳遞為個別引數，以將長度傳遞給被呼叫者。  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 將包含 **ELEMENT_TYPE_ARRAY** 參數的方法從 .NET 組件匯出至型別程式庫時，會將陣列參數轉換成指定類型的 **SAFEARRAY**。 Managed 陣列的內容會自動從 Managed 記憶體複製至 **SAFEARRAY**。 例如:   
  
#### <a name="managed-signature"></a>Managed 簽章  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Unmanaged 簽章  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 在執行階段，安全陣列的順位、大小和界限是取決於 Managed 陣列的特性。  
  
 套用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將陣列封送處理為 C 樣式陣列。 例如:   
  
#### <a name="managed-signature"></a>Managed 簽章  
  
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
  
#### <a name="unmanaged-signature"></a>Unmanaged 簽章  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 無法封送處理巢狀陣列。 例如，下列簽章會在使用[型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 匯出時產生錯誤。  
  
#### <a name="managed-signature"></a>Managed 簽章  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>ELEMENT_TYPE_CLASS \<System.Array>  
 將包含 <xref:System.Array?displayProperty=nameWithType> 參數的方法從 .NET 組件匯出至型別程式庫時，會將陣列參數轉換成 **_Array** 介面。 Managed 陣列的內容只能透過 **_Array** 介面的方法和屬性進行存取。 使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，也可以將 **System.Array** 封送處理為 **SAFEARRAY**。 封送處理為安全陣列時，會將陣列項目封送處理為變異值。 例如:   
  
#### <a name="managed-signature"></a>Managed 簽章  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Unmanaged 簽章  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>結構內的陣列  
 Unmanaged 結構可以包含內嵌的陣列。 根據預設，會將這些內嵌的陣列欄位封送處理為 SAFEARRAY。 在下列範例中，`s1` 是直接配置在結構本身內的內嵌陣列。  
  
#### <a name="unmanaged-representation"></a>Unmanaged 呈現  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 陣列可以封送處理為 <xref:System.Runtime.InteropServices.UnmanagedType>，這需要您設定 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 欄位。 大小只能設定為常數。 下列程式碼示範 `MyStruct` 的對應 Managed 定義。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [預設的封送處理行為](default-marshaling-behavior.md)  
 [Blittable 和非 Blittable 類型](blittable-and-non-blittable-types.md)  
 [方向屬性](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [複製和 Pin](copying-and-pinning.md)
