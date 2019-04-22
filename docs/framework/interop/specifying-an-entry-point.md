---
title: 指定進入點
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15a441ea7b0b16c83c590289d04cf0c10623fb85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086061"
---
# <a name="specifying-an-entry-point"></a>指定進入點
進入點可識別函式在 DLL 中的位置。 在 Managed 專案中，目標函式的原始名稱或序數進入點可跨越交互操作界限識別該函式。 此外，您可以將進入點對應到不同的名稱，有效地重新命名函式。  
  
 以下是重新命名 DLL 函式的可能原因清單：  
  
-   避免使用區分大小寫的 API 函式名稱  
  
-   符合現有的命名標準  
  
-   容納接受不同資料類型 (藉由宣告相同 DLL 函式的多個版本) 的函式  
  
-   簡化使用包含 ANSI 和 Unicode 版本的 API  
  
 本主題示範如何在 Managed 程式碼中重新命名 DLL 函式。  
  
## <a name="renaming-a-function-in-visual-basic"></a>在 Visual Basic 中重新命名函式  
 Visual Basic 使用 **Function** 關鍵字在 **Declare** 陳述式中設定 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 欄位。 下列範例示範基本宣告。  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 您可以將 **MessageBox** 進入點取代為 **MsgBox**，方法是在您的定義中包含 **Alias** 關鍵字，如下列範例所示。 在這兩個範例中，**Auto** 關鍵字讓您不需要指定進入點的字元集版本。 如需選取字元集的詳細資訊，請參閱[指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)。  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a>在 C# 和 C++ 中重新命名函式  
 您可以使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 欄位來依名稱或序數指定 DLL 函式。 如果方法定義中的函式名稱與 DLL 中的進入點相同，則不必明確地以 **EntryPoint** 欄位來識別函式。 否則，請使用其中一種下列屬性形式來表示名稱或序數：  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 請注意，您必須在序數前面加上井字號 (#)。  
  
 下列範例示範如何使用 **EntryPoint** 欄位，將程式碼中的 **MessageBoxA** 取代為 **MsgBox**。  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [平台叫用範例](../../../docs/framework/interop/platform-invoke-examples.md)
- [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
