---
title: "平台叫用範例 | Microsoft Docs"
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
  - "COM Interop, 平台叫用"
  - "DLL 函式"
  - "範例 [.NET Framework], 平台叫用"
  - "與 Unmanaged 程式碼的互通, 平台叫用"
  - "平台叫用, 範例"
  - "Unmanaged 函式"
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 平台叫用範例
下列範例說明如何定義和呼叫 User32.dll 中的 **MessageBox** 函式，將一個簡單字串做為引數傳遞。  在這些範例中，[DllImportAttribute.CharSet Field](frlrfSystemRuntimeInteropServicesDllImportAttributeClassCharSetTopic) 欄位會設為 **Auto**，讓目標平台決定字元寬度和字串封送處理 \(Marshaling\)。  
  
 同樣的範例會出現在 Visual Basic、C\# 和 C\+\+ 中。  若要顯示所有範例，請按一下頁面左上角的 \[語言篩選條件\] 按鈕![](../../../docs/framework/interop/media/filter2.gif "Filter2")。  若需額外的範例，請參閱[使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)。  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
       ByVal caption As String, ByVal Typ As Integer) As IntPtr  
End Class  
  
Public Class HelloWorld      
    Public Shared Sub Main()  
        Win32.MessageBox(0, "Hello World", "Platform Invoke Sample", 0)  
    End Sub  
End Class  
  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
     [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern IntPtr MessageBox(int hWnd, String text,   
                     String caption, uint type);  
}  
  
public class HelloWorld {  
    public static void Main() {  
       Win32.MessageBox(0, "Hello World", "Platform Invoke Sample", 0);  
    }  
}  
  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" IntPtr MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
void main(void) {  
     String* pText = L"Hello World!";  
     String* pCaption = L"Platform Invoke Sample";  
     MessageBox(0, pText, pCaption, 0);  
}  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)