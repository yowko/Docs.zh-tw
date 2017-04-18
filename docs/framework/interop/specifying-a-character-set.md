---
title: "指定字元集 | Microsoft Docs"
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
  - "平台叫用中的屬性欄位, CharSet"
  - "CharSet 欄位"
  - "平台叫用, 屬性欄位"
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 指定字元集
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> 欄位控制字串封送處理並決定平台叫用如何尋找 DLL 中的函式名稱。  這個主題將描述這兩種行為。  
  
 有些 API 會針對使用字串引數的函式匯出兩個版本：窄 \(ANSI\) 和寬 \(Unicode\)。  例如，Win32 API 包含下列 **MessageBox** 函式的進入點名稱：  
  
-   **MessageBoxA**  
  
     提供一個位元組的 ANSI 字元格式，在進入點名稱後附加一個 "A" 做為區別。  **MessageBoxA** 的呼叫一定會以 ANSI 格式封送處理的字串，這在 Window 95 和 Windows 98 平台上是十分常見的做法。  
  
-   **MessageBoxW**  
  
     提供雙位元組字元 Unicode 格式，在進入點名稱後附加一個 \[W\] 做為區別。  **MessageBoxW** 的呼叫一定會以 Unicode 格式封送處理的字串，這在 Windows NT、Windows 2000 和 Windows XP 等平台上是一種通用的做法。  
  
## 字串封送處理和名稱比對  
 **CharSet** 欄位接受下列值：  
  
 **CharSet.Ansi** \(預設值\)  
  
-   字串封送處理  
  
     平台叫用會從字串的 Managed 格式 \(Unicode\) 將它們封送處理至 ANSI 格式。  
  
-   名稱比對  
  
     當 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=fullName> 欄位為 **true** \(在 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 中為預設\)，則平台叫用只會搜尋您所指定的名稱。  例如，如果您指定 **MessageBox**，平台叫用會搜尋 **MessageBox**，且會在找不到完全相符的拼字時失敗。  
  
     當 **ExactSpelling** 欄位為 **false** \(C\+\+ 和 C\# 的預設值\)，平台叫用會先搜尋 unmangled 別名 \(**MessageBox**\)，如果找不到 unmangled 別名，就會接著搜尋 mangled 名稱 \(**MessageBoxA**\)。  請注意，ANSI 比對名稱的行為與 Unicode 比對名稱的行為不同。  
  
 **CharSet.Unicode**  
  
-   字串封送處理  
  
     平台叫用會從字串的 Managed 格式 \(Unicode\) 將它們複製到 Unicode 格式。  
  
-   名稱比對  
  
     當 **ExactSpelling** 欄位為 **true** \(此為 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 的預設值\)，平台叫用只會搜尋您指定的名稱。  例如，如果您指定 **MessageBox**，平台叫用會搜尋 **MessageBox**，且會在找不到完全相符的拼字時失敗。  
  
     當 **ExactSpelling** 欄位為 **false** \(C\+\+ 和 C\# 的預設值\)，平台叫用會先搜尋 mangled 名稱 \(**MessageBoxW**\)，如果找不到 mangled 名稱，接著會搜尋 unmangled 別名 \(**MessageBox**\)。  請注意，Unicode 比對名稱的行為與 ANSI 比對名稱的行為不同。  
  
 **CharSet.Auto**  
  
-   平台叫用會在 Run Time 期間依據目標平台選擇適當的 ANSI 和 Unicode 格式。  
  
## 在 Visual Basic 中指定字元集  
 下列範例會使用不同的字集行為宣告 **MessageBox** 函式三次。  在 Visual Basic 中，您可以將 **Ansi**、**Unicode** 或 **Auto** 關鍵字加入宣告陳述式中，以指定字集行為。  
  
 如果您省略字集關鍵字，如同第一個宣告陳述式的做法，則 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> 欄位會預設使用 ANSI 字集。  範例中的第二個和第三個陳述式會使用關鍵字明確指定字元集。  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## 在 C\# 和 C\+\+ 中指定字元集  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> 欄位會識別基礎字元集為 ANSI 或 Unicode。  字元集會控制方法的字串引數應如何封送處理。  請使用下列其中一種形式來指定字元集：  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 下列範例顯示 **MessageBox** 函式用來指定字集的三個 Managed 定義。  在第一個定義中，藉由省略而使得 **CharSet** 欄位預設使用 ANSI 字元集。  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [平台叫用範例](../../../docs/framework/interop/platform-invoke-examples.md)   
 [使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)