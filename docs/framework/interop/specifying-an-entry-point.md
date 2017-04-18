---
title: "指定進入點 | Microsoft Docs"
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
  - "平台叫用中的屬性欄位, EntryPoint"
  - "EntryPoint 欄位"
  - "平台叫用, 屬性欄位"
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 指定進入點
進入點可識別函式在 DLL 中的位置。  在 Managed 專案中，目標函式的原始名稱或以序數編號的進入點可以在整個互通界限識別這個函式。  此外，您也可以將進入點對應到不同的名稱，實際地重新命名這個函式。  
  
 以下清單是需要重新命名 DLL 函式的可能原因：  
  
-   若要避免使用要區分大小寫的 API 函式名稱  
  
-   若要符合現有的命名標準  
  
-   若要容納接受不同資料型別 \(藉由宣告同一 DLL 函式的多個版本\) 的函式  
  
-   若要簡化含有 ANSI 和 Unicode 版本之 API 的使用  
  
 這個主題將示範如何在 Managed 程式碼中重新命名 DLL 函式。  
  
## 在 Visual Basic 中重新命名函式  
 Visual Basic 會在 **Declare** 陳述式中使用 **Function** 關鍵字設定 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=fullName> 欄位。  以下範例所示為基本的宣告。  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
 如下列範例所示，您可以在定義中包括 **Alias** 關鍵字，使用 **MsgBox** 取代 **MessageBox** 進入點 \(Entry Point\)。  在兩個範例中，**Auto** 關鍵字不必指定進入點 \(Entry Point\) 的字集版本。  如需選取字元集的詳細資訊，請參閱[指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)。  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MsgBox Lib "user32.dll" _  
       Alias "MessageBox" (ByVal hWnd As Integer, ByVal txt As String,_  
       ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## 在 C\# 和 C\+\+ 中重新命名函式  
 您可以使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=fullName> 欄位來藉由名稱或序數指定 DLL 函式。  如果在您的方法定義中的函式名稱與 DLL 中進入點相同，您就不需要使用 **EntryPoint** 欄位來明確識別這個函式。  否則，請使用下列一種屬性形式來指示名稱或序數：  
  
```  
[DllImport("dllname", EntryPoint="Functionname")]  
[DllImport("dllname", EntryPoint="#123")]  
```  
  
 請注意，您必須在序數前面加上井字號 \(\#\) 前置詞。  
  
 下列範例示範如何使用 **EntryPoint** 欄位，在程式碼中以 **MsgBox** 取代 **MessageBoxA**。  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
    [DllImport("user32.dll", EntryPoint="MessageBoxA")]  
    public static extern int MsgBox(int hWnd, String text, String caption,  
                                    uint type);  
}  
  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", EntryPoint="MessageBoxA")]  
extern "C" int MsgBox(HWND hWnd,  
                      String*  pText,  
                      String*  pCaption,  
                      unsigned int uType);  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [平台叫用範例](../../../docs/framework/interop/platform-invoke-examples.md)   
 [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)