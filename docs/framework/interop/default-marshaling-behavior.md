---
title: 預設的封送處理行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fef84250f9dbc10a921a6844f7020c72835cea
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="default-marshaling-behavior"></a>預設的封送處理行為
Interop 封送處理會依據規則作業，這些規則指定與方法參數關聯的資料在 Managed 和 Unmanaged 記憶體之間傳遞時的運作方式。 這些內建規則會將這類封送處理活動當做資料類型轉換來控制；控制被呼叫端是否可以變更收到的資料，並將這些變更傳回給呼叫端；以及控制在哪些情況下，封送處理器會提供效能最佳化。  
  
 本節指出 Interop 封送處理服務的預設行為特性， 提供有關封送處理陣列、Boolean 類型、char 類型、委派、類別、物件、字串和結構的詳細資訊。  
  
> [!NOTE]
>  不支援封送處理泛型類型。 如需詳細資訊，請參閱[使用泛型型別互通](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100))。  
  
## <a name="memory-management-with-the-interop-marshaler"></a>使用 Interop 封送處理器進行記憶體管理  
 Interop 封送處理器一律會嘗試釋放 Unmanaged 程式碼所配置的記憶體。 這個行為使用 COM 記憶體管理規則進行編譯，但與管理原生 C++ 的規則不同。  
  
 如果您使用平台叫用 (會自動釋放指標的記憶體) 時，預期原生 C++ 行為 (不釋放記憶體)，則會發生混淆。 例如，從 C++ DLL 呼叫下列 Unmanage 方法不會自動釋放任何記憶體。  
  
### <a name="unmanaged-signature"></a>Unmanaged 簽章  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 不過，如果您將方法定義為平台叫用原型、將每個 **BSTR** 類型取代為 <xref:System.String> 類型，並呼叫 `MethodOne`，則 Common Language Runtime 會嘗試釋放 `b` 兩次。 您可以使用 <xref:System.IntPtr> 類型 (而不是 **String** 類型) 變更封送處理行為。  
  
 執行階段一律會使用 **CoTaskMemFree** 方法來釋放記憶體。 如果您正在使用的記憶體不是使用 **CoTaskMemAlloc** 方法配置，則必須使用 **IntPtr**，並使用適當方法手動釋放記憶體。 同樣地，您可以在絕不應該釋放記憶體的情況下避免自動釋放記憶體；例如，從 Kernel32.dll 使用 **GetCommandLine** 函式，該函式會傳回核心記憶體的指標。 如需手動釋放記憶體的詳細資訊，請參閱[緩衝區範例](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))。  
  
## <a name="default-marshaling-for-classes"></a>類別的預設封送處理  
 類別只能由 COM Interop 封送處理，並且一律會封送處理為介面。 在某些情況下，用來封送處理類別的介面就是所謂的類別介面。 如需以您選擇的介面來覆寫類別介面的相關資訊，請參閱[類別介面簡介](com-callable-wrapper.md#introducing-the-class-interface)。  
  
### <a name="passing-classes-to-com"></a>將類別傳遞給 COM  
 將 Managed 類別傳遞給 COM 時，Interop 封送處理器會自動使用 COM Proxy 來包裝類別，並將 Proxy 產生的類別介面傳遞給 COM 方法呼叫。 Proxy 接著會將類別介面上的所有呼叫重新委派給 Managed 物件。 Proxy 也會公開類別未明確實作的其他介面。 Proxy 會代表類別自動實作 **IUnknown** 和 **IDispatch** 這類介面。  
  
### <a name="passing-classes-to-net-code"></a>將類別傳遞給 .NET 程式碼  
 一般而言，Coclass 在 COM 中不會做為方法引數， 通常會以預設介面代替 Coclass 傳遞。  
  
 在將介面傳遞至 Managed 程式碼中之後，Interop 封送處理器會負責以適當的包裝函式來包裝介面，並將包裝函式傳遞給 Managed 方法。 您可能很難決定要使用哪個包裝函式。 不論物件實作多少個介面，COM 物件的每個執行個體都只會有一個包裝函式。 例如，實作五個不同介面的單一 COM 物件只會有一個包裝函式。 同一個包裝函式會公開所有五個介面。 如果建立 COM 物件的兩個執行個體，則會建立包裝函式的兩個執行個體。  
  
 為了讓包裝函式在整個存留期間保持同一個類型，當第一次透過 Interop 封送處理器傳遞物件所公開的介面時，封送處理器必須識別正確的包裝函式。 封送處理器會透過查看物件所實作的其中一個介面，來識別物件。  
  
 例如，封送處理器會決定應該使用類別包裝函式來包裝已傳遞至 Managed 程式碼中的介面。 當透過封送處理器第一次傳遞介面時，封送處理器會檢查介面是否來自已知的物件。 這項檢查會發生於下列兩種情況：  
  
-   另一個已傳遞至其他位置之 COM 的 Managed 物件正在實作介面。 封送處理器能夠立即識別 Managed 物件所公開的介面，而且能夠以提供實作的 Managed 物件來比對介面。 接著 Managed 物件會傳遞給方法，並且不需要任何包裝函式。  
  
-   已包裝的物件正在實作介面。 為了判斷是否為這種情況，封送處理器會查詢物件是否有 **IUnknown** 介面，並且將傳回的介面與其他已包裝之物件的介面進行比較。 如果該介面與其他包裝函式的介面相同，則物件會有相同的識別，因此會將現有的包裝函式傳遞給方法。  
  
 如果介面不是來自已知的物件，則封送處理器會執行下列作業：  
  
1.  封送處理器會查詢物件是否有 **IProvideClassInfo2** 介面。 如果有的話，封送處理器會使用從 **IProvideClassInfo2.GetGUID** 傳回的 CLSID 來識別提供介面的 coclass。 如果先前已註冊組件，封送處理器就可以使用 CLSID 從登錄中找出包裝函式。  
  
2.  封送處理器會查詢介面是否有 **IProvideClassInfo** 介面。 如果有的話，封送處理器會使用從 **IProvideClassInfo.GetClassinfo** 傳回的 **ITypeInfo** 來判斷公開介面之類別的 CLSID。 封送處理器可以使用 CLSID 來找出包裝函式的中繼資料。  
  
3.  如果封送處理器仍然無法識別類別，則會以稱為 **System.__ComObject** 的泛型包裝函式類別來包裝介面。  
  
## <a name="default-marshaling-for-delegates"></a>委派的預設封送處理  
 根據呼叫的機制，Managed 委派會封送處理為 COM 介面或函式指標：  
  
-   若為平台叫用，委派預設會封送處理為 Unmanaged 函式指標。  
  
-   若為 COM Interop，委派預設會封送處理為 **_Delegate** 類型的 COM 介面。 **_Delegate** 介面是在 Mscorlib.tlb 型別程式庫中定義，並且包含 <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> 方法，可讓您呼叫委派所參考的方法。  
  
 下表顯示 Managed 委派資料類型的封送處理選項。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理委派。  
  
|列舉類型|Unmanaged 格式的描述|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Unmanaged 函式指標。|  
|**UnmanagedType.Interface**|**_Delegate** 類型的介面，如 Mscorlib.tlb 中所定義。|  
  
 請考慮以下的範例程式碼，其中 `DelegateTestInterface` 的方法是匯出至 COM 類型程式庫。 請注意，只有標記為 **ref** (或 **ByRef**) 關鍵字的委派才會傳遞為 In/Out 參數。  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a>類型程式庫表示  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 函式指標和其他任何 Unmanaged 函式指標一樣，都可以解除參考。  
  
> [!NOTE]
>  Unmanaged 程式碼所持有之 Managed 委派的函式指標參考，無法防止 Common Language Runtime 在 Managed 物件上執行記憶體回收。  
  
 例如，下列程式碼不正確，因為傳遞給 `SetChangeHandler` 方法的 `cb` 物件參考無法使 `cb` 在過了 `Test` 方法的存留期後仍保持運作。 一旦 `cb` 物件的記憶體被回收，傳遞給 `SetChangeHandler` 的函式指標便不再有效。  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 為了彌補未預期的記憶體回收，呼叫端必須確保只要 Unmanaged 函式指標正在使用中，`cb` 物件就會保持運作。 您可以選擇性地讓 Unmanaged 程式碼通知 Managed 程式碼已不再需要函式指標，如下列範例所示。  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a>實值類型的預設封送處理  
 大部分的實值型別 (例如整數和浮點數) 都是 [Blittable](blittable-and-non-blittable-types.md)，而且不需要封送處理。 其他[非 Blittable](blittable-and-non-blittable-types.md) 類型在 Managed 和 Unmanaged 記憶體中有不同的表示，而且需要封送處理。 但其他類型需要跨互通界限進行明確格式化。  
  
 本主題提供以下有關格式化實值類型的資訊：  
  
-   [在平台叫用中使用的實值型別](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [在 COM Interop 中使用的實值型別](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 本主題除了描述格式化類型之外，還指出具有獨特封送處理行為的[系統實值型別](#cpcondefaultmarshalingforvaluetypesanchor1)。  
  
 格式化類型是複雜類型，其中包含在記憶體中明確控制其成員配置的資訊。 這項成員配置資訊會透過 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來提供。 配置可以是下列其中一個 <xref:System.Runtime.InteropServices.LayoutKind> 列舉值：  
  
-   **LayoutKind.Automatic**  
  
     表示 Common Language Runtime 可以為了更高的效率隨意重新排列類型的成員。 不過，當實值類型傳遞至 Unmanaged 程式碼時，成員的配置是可以預測的。 嘗試封送處理這類結構會自動造成例外狀況。  
  
-   **LayoutKind.Sequential**  
  
     表示類型的成員可以透過它們出現在 Managed 類型定義中的相同順序來配置於 Unmanaged 記憶體中。  
  
-   **LayoutKind.Explicit**  
  
     表示根據每個欄位提供的 <xref:System.Runtime.InteropServices.FieldOffsetAttribute> 來配置成員。  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a>在平台叫用中使用的實值類型  
 在下列範例中，`Point` 和 `Rect` 類型使用 **StructLayoutAttribute** 提供成員配置資訊。  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 當封送處理至 Unmanaged 程式碼時，這些格式化類型會封送處理為 C 樣式結構。 如此可讓您輕鬆地呼叫具有結構引數的 Unmanaged 應用程式開發介面。 例如，`POINT` 和 `RECT` 結構可以傳遞至 Microsoft Win32 API **PtInRect** 函式，如下所示：  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 您可以使用以下的平台叫用定義來傳遞結構：  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 `Rect` 實值類型必須以傳址方式傳遞，因為 Unmanaged 應用程式開發介面必須將 `RECT` 的指標傳遞至函式。 `Point` 實值類型必須以傳值方式傳遞，因為 Unmanaged 應用程式開發介面必須在堆疊上傳遞 `POINT`。 這種微妙的差異是非常重要的。 參考會當做指標傳遞至 Unmanaged 程式碼， 而值會在堆疊上傳遞至 Unmanaged 程式碼。  
  
> [!NOTE]
>  當格式化類型封送處理為結構時，只能存取類型內的欄位。 如果類型具有方法、屬性或事件，您無法從 Unmanaged 程式碼存取這些項目。  
  
 只要類別有固定成員配置，也可以當做 C 樣式結構封送處理至 Unmanaged 程式碼。 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性也會提供類別的成員配置資訊。 具有固定配置的實值類型和具有固定配置的類別之間的主要差異在於，將其封送處理至 Unmanaged 程式碼的方式不同。 實值類型是以傳值方式 (在堆疊上) 傳遞，因此呼叫端不會看到被呼叫端對類型的成員所做的任何變更。 參考類型是以傳址方式 (在堆疊上傳遞類型的參考) 傳遞，因此呼叫端會看到被呼叫端對類型的 Blittable 類型成員所做的所有變更。  
  
> [!NOTE]
>  如果參考類型具有非 Blittable 類型的成員，則需要轉換兩次：第一次是在將引數傳遞至 Unmanaged 端時，第二次是從呼叫傳回時。 由於這會增加額外負荷，因此如果呼叫端想要看到被呼叫端所做的變更，就必須將 In/Out 參數明確套用至引數。  
  
 在下列範例中，`SystemTime` 類別具有循序成員配置，可以傳遞至 Win32 API **GetSystemTime** 函式。  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 **GetSystemTime** 函式的定義如下：  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 **GetSystemTime** 的對等平台叫用定義如下：  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 請注意，`SystemTime` 引數未當做參考引數輸入，因為 `SystemTime` 是類別，不是實值類型。 不同於實值類型，類別永遠會以傳址方式傳遞。  
  
 下列程式碼範例顯示具有 `SetXY` 方法的不同 `Point` 類別。 由於類型具有循序配置，因此可傳遞至 Unmanaged 程式碼，並封送處理為結構。 不過，即使物件是以傳址方式傳遞，還是無法從 Unmanaged 程式碼中呼叫 `SetXY` 成員。  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a>在 COM Interop 中使用的實值類型  
 格式化類型也可以傳遞至 COM Interop 方法呼叫。 事實上，當匯出至類型程式庫時，實值類型會自動轉換成結構。 如下列範例所示，`Point` 實值類型會變成名為 `Point` 的類型定義 (typedef)。 `Point` typedef 會取代在類型程式庫中的所有 `Point` 實值類型的參考。  
  
 **型別程式庫呈現**  
  
```  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 當透過 COM 介面進行封送處理時，會使用與封送處理平台叫用呼叫的值和參考時相同的規則。 例如，將 `Point` 實值類型的執行個體從 .NET Framework 傳遞至 COM 時，會以傳值方式傳遞 `Point`。 如果以傳址方式傳遞 `Point` 實值類型，則會在堆疊上傳遞 `Point` 的指標。 Interop 封送處理器不支援任一方向中更高層級的間接取值 (**Point** \*\*)。  
  
> [!NOTE]
>  由於匯出的型別程式庫無法表示明確的配置，因此不可在 COM Interop 中使用將 <xref:System.Runtime.InteropServices.LayoutKind> 列舉值設定為 [明確] 的結構。  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a>系統實值類型  
 <xref:System> 命名空間具有數個實值類型，代表執行階段基本類型的 Boxed 格式。 例如，實值型別 <xref:System.Int32?displayProperty=nameWithType> 結構代表 **ELEMENT_TYPE_I4** 的 Boxed 格式。 如同其他格式化類型，封送處理這些類型的方式與這些類型 Box 處理基本類型的方式相同，而不是將其封送處理為結構。 因此會將 **System.Int32** 封送處理為 **ELEMENT_TYPE_I4**，而不是封送處理為包含 **long** 類型之單一成員的結構。 下表包含 **System** 命名空間中的實值型別清單，這些類型是基本類型的 Boxed 表示。  
  
|系統實值類型|項目類型|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|**ELEMENT_TYPE_BOOLEAN**|  
|<xref:System.SByte?displayProperty=nameWithType>|**ELEMENT_TYPE_I1**|  
|<xref:System.Byte?displayProperty=nameWithType>|**ELEMENT_TYPE_UI1**|  
|<xref:System.Char?displayProperty=nameWithType>|**ELEMENT_TYPE_CHAR**|  
|<xref:System.Int16?displayProperty=nameWithType>|**ELEMENT_TYPE_I2**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**ELEMENT_TYPE_U2**|  
|<xref:System.Int32?displayProperty=nameWithType>|**ELEMENT_TYPE_I4**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**ELEMENT_TYPE_U4**|  
|<xref:System.Int64?displayProperty=nameWithType>|**ELEMENT_TYPE_I8**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**ELEMENT_TYPE_U8**|  
|<xref:System.Single?displayProperty=nameWithType>|**ELEMENT_TYPE_R4**|  
|<xref:System.Double?displayProperty=nameWithType>|**ELEMENT_TYPE_R8**|  
|<xref:System.String?displayProperty=nameWithType>|**ELEMENT_TYPE_STRING**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_I**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_U**|  
  
 **System** 命名空間中的其他一些實值型別會以不同方式處理。 由於 Unmanaged 程式碼已經有這些類型的確立格式，因此封送處理器針對這些類型有特殊的封送處理方式。 下表列出 **System** 命名空間中的特殊實值型別，以及要封送處理的目標 Unmanaged 類型。  
  
|系統實值類型|IDL 類型|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DATE**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**DECIMAL**|  
|<xref:System.Guid?displayProperty=nameWithType>|**GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 下列程式碼示範 Stdole2 型別程式庫中 Unmanaged 類型 **DATE**、**GUID**、**DECIMAL** 和 **OLE_COLOR** 的定義。  
  
#### <a name="type-library-representation"></a>類型程式庫表示  
  
```  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 下列程式碼顯示 Managed `IValueTypes` 介面中的對應定義。  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a>類型程式庫表示  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [Blittable 和非 Blittable 類型](blittable-and-non-blittable-types.md)  
 [複製和 Pin](copying-and-pinning.md)  
 [陣列的預設封送處理](default-marshaling-for-arrays.md)  
 [物件的預設封送處理](default-marshaling-for-objects.md)  
 [字串的預設封送處理](default-marshaling-for-strings.md)
