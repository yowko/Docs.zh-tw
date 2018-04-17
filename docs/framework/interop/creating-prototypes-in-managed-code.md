---
title: 在 Managed 程式碼中建立原型
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c59a05c5f6abfa30a71ccf7608f8a84738f99c3a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="creating-prototypes-in-managed-code"></a>在 Managed 程式碼中建立原型
本主題描述如何存取 Unmanaged 函式，並介紹數個以 Managed 程式碼來標註方法定義的屬性欄位。 如需示範如何建構要與平台叫用搭配使用之 .NET 型宣告的範例，請參閱[使用平台叫用封送處理資料](marshaling-data-with-platform-invoke.md)。  
  
 在您可以從 Managed 程式碼存取 Unmanaged DLL 函式之前，您需要知道函式的名稱，以及將它匯出的 DLL 名稱。 利用此資訊，您可以開始撰寫 Managed 定義給在 DLL 中實作的 Unmanaged 函式。 此外，您可以調整叫用平台建立函式和封送處理資料給予或來自函式的方式。  
  
> [!NOTE]
>  配置字串的 Win32 API 函式可讓您使用下列方法以釋放字串 `LocalFree`。 平台叫用以不同方式處理這類參數。 為了平台叫用呼叫，將參數設定為 `IntPtr` 類型而非 `String` 類型。 使用 <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> 類別所提供的方法來手動將類型轉換為字串，並手動釋放。  
  
## <a name="declaration-basics"></a>宣告的基本概念  
 Unmanaged 函式的 Managed 定義會依語言而異，您可以在下列範例中觀察到。 如需更完整的程式碼範例，請參閱[平台叫用範例](platform-invoke-examples.md)。  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 若要套用 <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping> 、 <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention> 、 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> 、 <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig> 、 <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> 或 <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> 欄位到 [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] 宣告中，您必須使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性而不是 `Declare` 陳述式。  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a>調整定義  
 不論您是否明確地設定它們，屬性欄位都會定義 Managed 程式碼的行為。 平台叫用操作根據以中繼資料的形式存在於組件中的各種欄位上所設定的預設值。 您可以藉由調整一或多個欄位的值來變更此預設行為。 在許多情況下，您會使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 來設定該值。  
  
 下表列出一組平台叫用的完整屬性欄位。 在每個欄位裡，資料表包含預設值以及連結，關於如何使用這些欄位來定義 Unmanaged DLL 函式的詳細資訊。  
  
|欄位|描述|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|啟用或停用自動調整對應。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|指定用來傳遞方法引數的呼叫慣例。 預設值是 `WinAPI` ，它對應至適用於 32 位元 Intel 平台的 `__stdcall` 。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|控制項名稱的損害以及字串引數的方式應該封送處理至函式。 預設值為 `CharSet.Ansi`。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|指定要呼叫 DLL 進入點。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|控制是否應修改進入點以對應至字元集。 預設值依程式語言而異。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|控制是否應將 Managed 方法簽章轉換成 Unmanaged 簽章，其會傳回 HRESULT 且傳回值會有額外的 [out, retval] 引數。<br /><br /> 預設值是 `true` (簽章不應該轉換)。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|可讓呼叫者使用 `Marshal.GetLastWin32Error` API 函式來判斷當執行此方法時是否發生錯誤。 在 Visual Basic 中，預設值是 `true`；在 C# 和 C++ 中，預設值是  `false`。|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|在無法對應 Unicode 字元的例外狀況中，控制項的擲回轉換成 ANSI "?" 字元。|  
  
 如需詳細參考資訊，請參閱 <xref:System.Runtime.InteropServices.DllImportAttribute>。  
  
## <a name="platform-invoke-security-considerations"></a>平台叫用安全性考量  
 <xref:System.Security.Permissions.SecurityAction> 列舉的 `Assert`、`Deny` 和 `PermitOnly` 成員稱為「堆疊查核修飾詞」。 如果這些成員被做為平台叫用宣告式和 COM 介面定義語言 (IDL) 陳述式的宣告式屬性，就會忽略這些成員。  
  
### <a name="platform-invoke-examples"></a>平台叫用範例  
 本節中的平台叫用範例將說明如何使用具有堆疊查核行程修飾詞的  `RegistryPermission` 屬性。  
  
 在下列程式碼範例中， <xref:System.Security.Permissions.SecurityAction> `Assert`， `Deny`，和`PermitOnly`修飾詞會被忽略。  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 不過，`Demand` 修飾詞，在下列範例中會被接受。  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 如果它們被放在包含 (換行) 平台叫用呼叫的類別上，<xref:System.Security.Permissions.SecurityAction> 修飾詞會正常運作。  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <xref:System.Security.Permissions.SecurityAction> 修飾詞也會正確運作於巢狀案例中，其中它們被放在平台叫用呼叫的呼叫者上：  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a>COM Interop 範例  
 本節中的 COM Interop 範例說明使用具有堆疊查核行程修飾詞的 `RegistryPermission` 屬性。  
  
 下列 COM Interop 介面宣告忽略 `Assert` 、 `Deny` 和 `PermitOnly` 修飾詞，類似於先前章節中的平台叫用範例。  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 此外，如下列範例所示，在 COM Interop 介面宣告的情況下，不接受 `Demand` 修飾詞。  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 Unmanaged DLL 函式](consuming-unmanaged-dll-functions.md)  
 [指定進入點](specifying-an-entry-point.md)  
 [指定字元集](specifying-a-character-set.md)  
 [平台叫用範例](platform-invoke-examples.md)  
 [平台叫用的安全性考量](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))  
 [識別 DLL 中的函式](identifying-functions-in-dlls.md)  
 [建立類別以包裝 DLL 函式](creating-a-class-to-hold-dll-functions.md)  
 [呼叫 DLL 函式](calling-a-dll-function.md)
