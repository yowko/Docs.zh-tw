---
title: 指定字元集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 798fcacab5bd74dbd6569a68a3b598c0bb63a0a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087738"
---
# <a name="specifying-a-character-set"></a>指定字元集
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位控制字串封送處理，並決定平台叫用如何在 DLL 中尋找函式名稱。 這個主題將描述這兩種行為。  
  
 某些 API 匯出兩個版本的函式，接受字串引數：窄 (ANSI) 和寬 (Unicode)。 例如，Win32 API 包括 **MessageBox** 函式的下列進入點名稱：  
  
-   **MessageBoxA**  
  
     提供 1 個位元組字元 ANSI 格式化，區別方式是在進入點名稱附加 "A"。 **MessageBoxA** 呼叫一律以 ANSI 格式的字串封送處理。  
  
-   **MessageBoxW**  
  
     提供 2 個位元組字元 Unicode 格式化，區別方式是在進入點名稱附加 "W"。 **MessageBoxW** 呼叫一律以 Unicode 格式的字串封送處理。  
  
## <a name="string-marshaling-and-name-matching"></a>字串封送處理及名稱比對  
 `CharSet` 欄位可接受下列值：  
  
 <xref:System.Runtime.InteropServices.CharSet.Ansi> (預設值)  
  
-   字串封送處理  
  
     平台叫用會將字串從其受管理的格式 (Unicode) 封送處理為 ANSI 格式。  
  
-   名稱比對  
  
     當 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> 欄位是 `true` 時，如同 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 中的預設值，平台叫用僅會搜尋您指定的名稱。 例如，如果您指定 **MessageBox**，平台叫用會搜尋 **MessageBox**，並在找不到正確的拼字時失敗。  
  
     當 `ExactSpelling` 欄位是 `false` 時，如同在 C++ 和 C# 中的預設值，平台叫用會先搜尋未損壞別名 (**MessageBox**)，然後如果找不到未損壞別名則搜尋損壞名稱 (**MessageBoxA**)。 請注意，ANSI 名稱比對行為不同於 Unicode 名稱比對行為。  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
-   字串封送處理  
  
     平台叫用會將字串從其受管理的格式 (Unicode) 複製為 Unicode 格式。  
  
-   名稱比對  
  
     當 `ExactSpelling` 欄位是 `true` 時，如同 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 中的預設值，平台叫用僅會搜尋您指定的名稱。 例如，如果您指定 **MessageBox**，則平台叫用會搜尋 **MessageBox**，並在找不到正確的拼字時失敗。  
  
     當 `ExactSpelling` 欄位是 `false` 時，如同在 C++ 和 C# 中的預設值，平台叫用會先搜尋損壞名稱 (**MessageBoxW**)，然後如果找不到損壞名稱則搜尋未損壞別名 (**MessageBox**)。 請注意，Unicode 名稱比對行為不同於 ANSI 名稱比對行為。  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
-   平台叫用會在執行階段，根據在目標平台，在 ANSI 和 Unicode 格式之間選擇。  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>在 Visual Basic 中指定字元集  
 下列範例會宣告 **MessageBox** 函式三次，每次都有不同的字元集行為。 您可以在宣告陳述式新增 **Ansi**、**Unicode** 或 **Auto** 關鍵字，在 Visual Basic 中指定字元集行為。  
  
 如果您省略字元集關鍵字，如同您在第一個宣告陳述式的做法，<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位會預設為 ANSI 字元集。 在範例中的第二個和第三個陳述式，明確地以關鍵字指定字元集。  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a>在 C# 和 C++ 指定字元集  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位將基礎字元集識別為 ANSI 或 Unicode。 字元集控制應該如何封送處理方法的字串引數。 您可以使用下列格式之一來表示字元集：  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 下列範例示範 **MessageBox** 函式的三個 Managed 定義，其已屬性化以指定字元集。 在第一個定義中，根據其省略，`CharSet` 欄位預設為 ANSI 字元集。  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [平台叫用範例](../../../docs/framework/interop/platform-invoke-examples.md)
- [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
